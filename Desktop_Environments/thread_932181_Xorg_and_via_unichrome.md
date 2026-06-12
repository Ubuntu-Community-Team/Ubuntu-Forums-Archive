---
title: "Xorg and via unichrome"
date: 2008-09-28
forum: Desktop Environments
---

### Post by Pazzeo on 2008-09-28
Hi all,

I have installed the via unichrome downloaded from this link [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action). Following the instructions xorg start correctly now. But in the log file I see these errors:
```

Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Sep 28 11:06:18 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module "i2c" already built-in
(II) Module "ramdac" already built-in
(II) Module "ddc" already built-in
(II) Module "ddc" already built-in
(EE) VIA(0):  Couldn't open "/dev/video2"
(EE) VIA(0): Refresh rate setting in XF86Config(-4) is not supported!!
(EE) VIA(0): Driver will try to find another refresh rate instead.
(EE) VIA(0): Can't find refresh rate -36 Hz.
(EE) VIA(0): Can't find suitable refresh rate, use 60Hz as default.
(EE) VIA(0):  Couldn't open "/dev/video2"
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
Link points to "/var/tmp/kdecache-root"
Link points to "/var/tmp/kdecache-root"
QPainter::setCompositionMode: PorterDuff modes not supported on device
QPainter::setCompositionMode: PorterDuff modes not supported on device
QPainter::setCompositionMode: PorterDuff modes not supported on device
QPainter::setCompositionMode: PorterDuff modes not supported on device
QPainter::setCompositionMode: PorterDuff modes not supported on device
QPainter::setCompositionMode: PorterDuff modes not supported on device
QPainter::setCompositionMode: PorterDuff modes not supported on device
QPainter::setCompositionMode: PorterDuff modes not supported on device
QPainter::setCompositionMode: PorterDuff modes not supported on device
QPainter::setCompositionMode: PorterDuff modes not supported on device
QPainter::setCompositionMode: PorterDuff modes not supported on device
Link points to "/tmp/kde-root"

```
I think the big problem is that the /dev/video2 is not found. 
How can I solve these errors?  What kind error is the QPainter::setCompositionMode: PorterDuff modes not supported on device ?? 

Thank you 

Pazzeo

---

