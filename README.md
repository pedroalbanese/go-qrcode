# go-qrcode #

<img src='https://skip.org/img/nyancat-youtube-qr.png' align='right'>

[![ISC License](http://img.shields.io/badge/license-ISC-blue.svg)](https://github.com/pedroalbanese/go-qrcode/blob/master/LICENSE.md) 
[![GoDoc](https://godoc.org/github.com/pedroalbanese/go-qrcode?status.png)](http://godoc.org/github.com/pedroalbanese/go-qrcode)
[![GitHub downloads](https://img.shields.io/github/downloads/pedroalbanese/go-qrcode/total.svg?logo=github&logoColor=white)](https://github.com/pedroalbanese/go-qrcode/releases)
[![Go Report Card](https://goreportcard.com/badge/github.com/pedroalbanese/go-qrcode)](https://goreportcard.com/report/github.com/pedroalbanese/go-qrcode)
[![GitHub go.mod Go version](https://img.shields.io/github/go-mod/go-version/pedroalbanese/go-qrcode)](https://golang.org)
[![GitHub release (latest by date)](https://img.shields.io/github/v/release/pedroalbanese/go-qrcode)](https://github.com/pedroalbanese/go-qrcode/releases)

A QR Code is a matrix (two-dimensional) barcode. Arbitrary content may be encoded, with URLs being a popular choice :)

Each QR Code contains error recovery information to aid reading damaged or obscured codes. There are four levels of error recovery: Low, medium, high and highest. QR Codes with a higher recovery level are more robust to damage, at the cost of being physically larger.

## Install

    go get -u github.com/skip2/go-qrcode/...

A command-line tool `qrcode` will be built into `$GOPATH/bin/`.

## Usage

    import qrcode "github.com/skip2/go-qrcode"

- **Create a 256x256 PNG image:**

        var png []byte
        png, err := qrcode.Encode("https://example.org", qrcode.Medium, 256)

- **Create a 256x256 PNG image and write to a file:**

        err := qrcode.WriteFile("https://example.org", qrcode.Medium, 256, "qr.png")

- **Create a 256x256 PNG image with custom colors and write to file:**

        err := qrcode.WriteColorFile("https://example.org", qrcode.Medium, 256, color.Black, color.White, "qr.png")

All examples use the qrcode.Medium error Recovery Level and create a fixed 256x256px size QR Code. The last function creates a white on black instead of black on white QR Code.

## Documentation

[![godoc](https://godoc.org/github.com/skip2/go-qrcode?status.png)](https://godoc.org/github.com/skip2/go-qrcode)

## Demoapp

[http://go-qrcode.appspot.com](http://go-qrcode.appspot.com)

## CLI

A command-line tool `qrcode` will be built into `$GOPATH/bin/`.

```
qrcode -- QR Code encoder in Go
https://github.com/skip2/go-qrcode

Flags:
  -d	disable QR Code border
  -i	invert black and white
  -o string
    	out PNG file prefix, empty for stdout
  -s int
    	image size (pixel) (default 256)
  -t	print as text-art on stdout

Usage:
  1. Arguments except for flags are joined by " " and used to generate QR code.
     Default output is STDOUT, pipe to imagemagick command "display" to display
     on any X server.

       qrcode hello word | display

  2. Save to file if "display" not available:

       qrcode "homepage: https://github.com/skip2/go-qrcode" > out.png

```
## Maximum capacity
The maximum capacity of a QR Code varies according to the content encoded and the error recovery level. The maximum capacity is 2,953 bytes, 4,296 alphanumeric characters, 7,089 numeric digits, or a combination of these.

## Borderless QR Codes

To aid QR Code reading software, QR codes have a built in whitespace border.

If you know what you're doing, and don't want a border, see https://gist.github.com/skip2/7e3d8a82f5317df9be437f8ec8ec0b7d for how to do it. It's still recommended you include a border manually.

## Links

- [http://en.wikipedia.org/wiki/QR_code](http://en.wikipedia.org/wiki/QR_code)
- [ISO/IEC 18004:2006](http://www.iso.org/iso/catalogue_detail.htm?csnumber=43655) - Main QR Code specification (approx CHF 198,00)<br>
- [https://github.com/qpliu/qrencode-go/](https://github.com/qpliu/qrencode-go/) - alternative Go QR encoding library based on [ZXing](https://github.com/zxing/zxing)
