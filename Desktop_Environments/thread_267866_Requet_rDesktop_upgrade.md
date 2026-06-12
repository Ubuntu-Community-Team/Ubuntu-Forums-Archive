---
title: "Requet: rDesktop upgrade"
date: 2006-09-29
forum: Desktop Environments
---

### Post by choman on 2006-09-29
Not sure where to really where post this, I haven't see a forum that
really targets application upgrades.

Dapper (not sure about Edgy) ships and still is at rDesktop 1.4.1

would like to see an upgrade to the latest rDekstop 1.5.0.  Hopefully
this carries forward to Edgy.  Here is a quick breakdown of the new 
features in a lame attempt to gain more support (snipped from the 
Changelog).

rdesktop (1.5.0)
  * SeamlessRDP - seamless windows support
  * Keymap fixes
  * Fix connection issues with Windows XP RTM
  * Keyboard handling improvements and fixes
  * SGI/Irix sound-driver fixes
  * Support for clipboard INCR protocol
  * Session Directory support (patch from Brian Chapeau <lheria@users.sourceforge.net>)
  * Support for long filenames on redirected drives
  * XOR ellipse drawing fix
  * Clipboard unicode support (Ilya Konstantinov)
  * Fix display issues with exotic color depths (30bpp, 32bpp, etc) (Ilya Konstantinov)
  * Large file support
  * The default color depth is now the depth of the root window
  * Basic support for Windows Vista Beta 2
  * Fix high cpu-usage in OSS-driver

---

### Post by kosmic on 2006-09-29
Hi, i've made a .deb of rDesktop for you, please try it, and tell me if you have any errors.

worked fine in my system

---

### Post by ashrack on 2006-10-22
> **choman said:**
> Not sure where to really where post this, I haven't see a forum that
really targets application upgrades.

Dapper (not sure about Edgy) ships and still is at rDesktop 1.4.1

would like to see an upgrade to the latest rDekstop 1.5.0.  Hopefully
this carries forward to Edgy.  Here is a quick breakdown of the new 
features in a lame attempt to gain more support (snipped from the 
Changelog).

rdesktop (1.5.0)
  * SeamlessRDP - seamless windows support
  * Keymap fixes
  * Fix connection issues with Windows XP RTM
  * Keyboard handling improvements and fixes
  * SGI/Irix sound-driver fixes
  * Support for clipboard INCR protocol
  * Session Directory support (patch from Brian Chapeau <lheria@users.sourceforge.net>)
  * Support for long filenames on redirected drives
  * XOR ellipse drawing fix
  * Clipboard unicode support (Ilya Konstantinov)
  * Fix display issues with exotic color depths (30bpp, 32bpp, etc) (Ilya Konstantinov)
  * Large file support
  * The default color depth is now the depth of the root window
  * Basic support for Windows Vista Beta 2
  * Fix high cpu-usage in OSS-driver
Unfortunetly it wont be in EDGY also! Don understand why??
But I´ve opened a request at UBUNTU BACKPORTS [here]("http://ubuntuforums.org/showthread.php?t=282085")
So add your name to the list

---

### Post by dcstar on 2007-01-14
> **kosmic said:**
> Hi, i've made a .deb of rDesktop for you, please try it, and tell me if you have any errors.

worked fine in my system

That had dependency issues on my 6.10 system, this one seems to work:

[http://www.getdeb.net/category.php?id=21&release=Edgy](http://www.getdeb.net/category.php?id=21&release=Edgy)

---

