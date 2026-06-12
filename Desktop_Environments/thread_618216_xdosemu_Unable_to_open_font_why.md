---
title: "xdosemu Unable to open font: why?"
date: 2007-11-20
forum: Desktop Environments
---

### Post by crixtiano on 2007-11-20
When I run xdosemu , the software give me an error mesage:

> $ xdosemu
ERROR: X: Unable to open font "vga-cp866", using builtin

But, I don't understande. Because the font "vga-cp866" is installed inside my Ubuntu Feisty:


> 
$ dpkg -L xfonts-dosemu
/.
/etc
/etc/X11
/etc/X11/fonts
/etc/X11/fonts/misc
/etc/X11/fonts/misc/xfonts-dosemu.alias
/usr
/usr/share
/usr/share/fonts
/usr/share/fonts/X11
/usr/share/fonts/X11/misc
/usr/share/fonts/X11/misc/vga.pcf.gz
/usr/share/fonts/X11/misc/dosemu-vga11x19.pcf.gz
/usr/share/fonts/X11/misc/vga-cp866.pcf.gz
/usr/share/fonts/X11/misc/vga10x20-cp866.pcf.gz
/usr/share/doc
/usr/share/doc/xfonts-dosemu
/usr/share/doc/xfonts-dosemu/copyright
/usr/share/doc/xfonts-dosemu/changelog.gz
/usr/share/doc/xfonts-dosemu/changelog.Debian.gz



This font is set in /etc/dosemu/dosemu.conf file:

> # name of the X font that is used (e.g. "vga") default = "" (bitmap fonts)

$_X_font = "vga-cp866"



I have a question: what do I have to do to dosemu find the font  "vga-cp866" ?

I really need this, and I didn't find nothing about yet.

Thank you

Cristiano

---

