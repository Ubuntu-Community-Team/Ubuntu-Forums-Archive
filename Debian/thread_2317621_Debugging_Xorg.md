---
title: "Debugging Xorg"
date: 2016-03-18
forum: Debian
---

### Post by lazar-urosevic92 on 2016-03-18
[COLOR=#222426][FONT=Arial]I am stucked for a month with video example given in [Qt Video Overview]("http://doc.qt.io/qt-5/videooverview.html").[/FONT][/COLOR]
[COLOR=#222426][FONT=Arial]I tried that code, but only I get is blank square (QWidget). I am using GStreamer0.10 for media playback over Qt5. I also played video with gst-launch-0.10 command and it works okay, but I cannot determine what's happening in Qt and why it won't work?[/FONT][/COLOR]
[COLOR=#222426][FONT=Arial]I looked in error log of X Server, located in /etc/X11/Xorg.0.log, and when I use fbdev as a display driver configured in /etc/X11/xorg.conf it shows me the error:[/FONT][/COLOR][INDENT]"FBDEV(0): FBIOPUTCMAP: Invalid argument"
[/INDENT]
[COLOR=#222426][FONT=Arial]when I use modesetting driver everything acts the same but no errors. I figured out that when I delete xorg.conf file and start X server again, video works but with lack of colors and with flickering also example works well on my Ubuntu VM and via vnc client. Every advice and help will be appreciated.[/FONT][/COLOR]

[LIST]
[*]Target machine: BeagleBone Black
[*]Distribution: Debian Jessie 8.2
[*]Kernel Version: 4.1.15-ti-rt-r43
[/LIST]
[COLOR=#222426][FONT=Arial]List of available drivers in /usr/lib/xorg/modules/drivers: **ati_drv.so, mach64_drv.so, nouveau_drv.so, r128_drv.so, vesa_drv.so, fbdev_drv.so, modesetting_drv.so, omap_drv.so, radeon_drv.so**[/FONT][/COLOR]
[COLOR=#222426][FONT=Arial]Here is a full error log from Xorg when I try to launch my Qt application on BeagleBone Black under Debian Jessie 8.2 -> [http://pastebin.com/4x8KztBk](http://pastebin.com/4x8KztBk)[/FONT][/COLOR]
[COLOR=#222426][FONT=Arial]xorg.conf file from /etc/X11 -> [http://pastebin.com/4WhX8pJc](http://pastebin.com/4WhX8pJc)[/FONT][/COLOR]

---

