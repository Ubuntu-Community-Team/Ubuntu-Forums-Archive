---
title: "gftp auto select binary/ascii"
date: 2006-03-12
forum: Desktop Environments
---

### Post by ubnoobie on 2006-03-12
does someone have a more complete gftprc (~/.gftp/gftprc) section on file extensions and how they should be transferred (binary/ascii)?

there's no interface in the program for editing that part of the config, and it's severely lacking in many common extensions (gif, php, js, css, etc).

OR, does gftp not use that and instead hook into some gnome list of what types of files different extensions are?

---

### Post by taurus on 2006-03-12
Fire up gftp -> FTP -> Options -> FTP.

---

### Post by ubnoobie on 2006-06-13
*(sorry for the delay in responding, just uncovered this in a search for my q's)..*


[QUOTE=taurus]Fire up gftp -> FTP -> Options -> FTP.[/QUOTE]

that appears to just enable/disable ascii transfers globally. i was referring to automatic selection of transfer type based upon a file's extension. the relevent section in gftprc:

```
# ext=file extenstion:XPM file:Ascii or Binary (A or B):viewer program. Note:
# All arguments except the file extension are optional
ext=.pdf::B:xpdf
ext=.rpm:rpm.xpm:B:
ext=.deb:deb.xpm:B:
ext=.diff:diff.xpm: :
ext=.htm:world.xpm:A:
ext=.html:world.xpm:A:
ext=.xcf:img.xpm:B:
ext=.psd:img.xpm:B:
ext=.xpm:img.xpm:B:
ext=.bmp:img.xpm:B:
ext=.tif:img.xpm:B:
ext=.tiff:img.xpm:B:
ext=.png:img.xpm:B:
ext=.jpg:img.xpm:B:
ext=.mp3:sound.xpm:B:
ext=.mid:sound.xpm:B:
ext=.wav:sound.xpm:B:
ext=.bz2:tar.xpm:B:
ext=.gz:tar.xpm:B:
ext=.1:man.xpm:B:xman
ext=.2:man.xpm:B:xman
ext=.3:man.xpm:B:xman
ext=.4:man.xpm:B:xman
ext=.5:man.xpm:B:xman
ext=.6:man.xpm:B:xman
ext=.7:man.xpm:B:xman
ext=.8:man.xpm:B:xman
ext=.tar:tar.xpm:B:
ext=.tgz:tar.xpm:B:
```

---

