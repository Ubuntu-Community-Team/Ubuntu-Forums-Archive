---
title: "beagle &amp; word documents"
date: 2006-08-04
forum: Desktop Environments
---

### Post by mvaniersel on 2006-08-04
Beagle is able to index chm help files and MS word documents according to this: [http://beagle-project.org/Supported_Filetypes]("http://beagle-project.org/Supported_Filetypes")

However, filters for these files do not seem to be installed by default. Where can I get those filters? Are there deb packages for that?

I'm using dapper drake. Here is the list of filters that I have:
```

martijn@bigcat017:~$ beagle-info --list-filters
&#65279;FilterHtml - Version 1 (/usr/lib/beagle/Filters/Filters.dll)
  - text/html

FilterJpeg - Version 3 (/usr/lib/beagle/Filters/Filters.dll)
  - image/jpeg

FilterTiff - Version 3 (/usr/lib/beagle/Filters/Filters.dll)
  - image/tiff

FilterMan - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - application/x-troff-man
  - text/x-troff-man
  - application/x-troff
  - text/x-troff

FilterOpenOffice - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - application/vnd.sun.xml.writer
  - application/vnd.sun.xml.writer.template
  - application/vnd.sun.xml.calc
  - application/vnd.sun.xml.calc.template
  - application/vnd.sun.xml.impress
  - application/vnd.sun.xml.impress.template
  - application/vnd.sun.xml.draw
  - application/vnd.sun.xml.draw.template
  - application/vnd.oasis.opendocument.text
  - application/vnd.oasis.opendocument.text-template
  - application/vnd.oasis.opendocument.spreadsheet
  - application/vnd.oasis.opendocument.spreadsheet-template
  - application/vnd.oasis.opendocument.presentation
  - application/vnd.oasis.opendocument.presentation-template
  - application/vnd.oasis.opendocument.graphics
  - application/vnd.oasis.opendocument.graphics-template

FilterPdf - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - application/pdf

FilterPng - Version 3 (/usr/lib/beagle/Filters/Filters.dll)
  - image/png

FilterText - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - text/plain
  - text/x-log
  - text/x-readme
  - text/x-install
  - text/x-credits
  - text/x-authors
  - text/x-copying

FilterRTF - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - application/rtf

FilterC - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - text/x-csrc
  - text/x-chdr

FilterCpp - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - text/x-c++src

FilterCSharp - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - text/x-csharp

FilterJava - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - text/x-java

FilterPython - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - text/x-python

FilterPerl - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - text/x-perl
  - application/x-perl

FilterPhp - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - text/x-php

FilterFortran - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - text/x-fortran

FilterPascal - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - text/x-pascal

FilterAbiWord - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - application/x-abiword

FilterSpreadsheet - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - application/x-gnumeric
  - application/csv
  - application/tab-separated-values
  - text/comma-separated-values
  - text/csv
  - text/spreadsheet
  - text/tab-separated-values
  - text/x-comma-separated-values
  - application/vnd.ms-excel
  - application/excel
  - application/x-msexcel
  - application/x-excel

FilterJavascript - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - *.js

FilterScheme - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - text/x-scheme

FilterMatlab - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - *.m

FilterScilab - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - *.sci

FilterDocbook - Version 4 (/usr/lib/beagle/Filters/Filters.dll)
  - application/docbook+xml
  - *.docbook
  - *.xml

FilterMonodoc - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - application/monodoc
  - *.zip

FilterDesktop - Version 2 (/usr/lib/beagle/Filters/Filters.dll)
  - application/x-desktop

FilterDirectory - Version 2 (/usr/lib/beagle/Filters/Filters.dll)
  - application/x-desktop
  - x-directory/normal
  - inode/directory

FilterMail - Version 1 (/usr/lib/beagle/Filters/Filters.dll)
  - message/rfc822

FilterMusic - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - *.ape
  - audio/x-flac
  - audio/x-mp3
  - audio/mpeg
  - *.mpc
  - *.mp+
  - audio/x-m4a
  - *.m4p
  - application/ogg
  - audio/x-vorbis+ogg
  - audio/x-s3m
  - audio/x-it
  - audio/x-mod
  - audio/x-xm
  - audio/x-ms-wma

FilterShellscript - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - application/x-shellscript

FilterRuby - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - text/x-ruby

FilterMPlayerVideo - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - video/dl
  - video/dv
  - video/fli
  - video/gl
  - video/mpeg
  - video/mp4
  - video/quicktime
  - video/mp4v-es
  - video/parityfec
  - video/pointer
  - video/vnd.fvt
  - video/vnd.motorola.video
  - video/vnd.motorola.videop
  - video/vnd.mpegurl
  - video/vnd.mts
  - video/vnd.nokia.interleaved-multimedia
  - video/vnd.vivo
  - video/x-la-asf
  - video/x-mng
  - video/x-ms-asf
  - video/x-ms-wm
  - video/x-ms-wmv
  - video/x-ms-wmx
  - video/x-ms-wvx
  - video/x-msvideo
  - video/x-sgi-movie

FilterBMP - Version 3 (/usr/lib/beagle/Filters/Filters.dll)
  - image/bmp

FilterEbuild - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - *.ebuild

FilterGif - Version 3 (/usr/lib/beagle/Filters/Filters.dll)
  - image/gif

FilterXslt - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - text/x-xslt
  - application/xslt+xml

FilterRPM - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - application/x-rpm

FilterDeb - Version 0 (/usr/lib/beagle/Filters/Filters.dll)
  - application/x-deb

```

---

