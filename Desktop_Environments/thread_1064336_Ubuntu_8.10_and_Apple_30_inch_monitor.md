---
title: "Ubuntu 8.10 and Apple 30 inch monitor"
date: 2009-02-08
forum: Desktop Environments
---

### Post by llongeri on 2009-02-08
Hi,

I after a while I was able to install Ubuntu 8.10 64 bits on my:
- Asus Commando Motherboard
- nVidia GeForce 9500 GT (GV-N95TOC-512H)
- Apple 30' 2560x1600 monitor

The installation process would freeze (with and ugly screen), the same happens with Fedora 10 (64 bits) installation disk.

In order to get it working , I had to do the following steps:

1.- install Ubuntu with a smaller monitor.

2.- edit /etc/X11/xorg.conf to setup 1280x800 resolution, something like:
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Modeline "1280x800" 71.00 1280 1328 1360 1440  800 803 809 823 +hsync -vsync
1603 1609 1646 +hsync -vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth	24
        SubSection "Display"
		Depth	24
		Modes	"1280x800"
	EndSubSection 
EndSection

3.- bootup with the Apple 30' monitor. (working at 1280x800).

4.- install envyng and install the nvidia driver 173 (177 doesn't work).

5.- reconfigure /etc/X11/xorg.conf with 2560x1600 resolution:
...
...
	Modeline "2560x1600" 268.000 2560 2608 2640 2720 1600 1603 1609 1646 +hsync -vsync
...
...
		Modes	"2560x1600"
...
...

Regards,
Luis Longeri

---

### Post by Vadi on 2009-02-08
Thanks for this.

Could you, if you have the time, try the Ubuntu 9.04 alpha 4? If you still have the issue - now would be a great time to report it so they can get it hopefully fixed (if they can - if the fault is in the nvidia drivers, then its up to nvidia) bu 9.04 release.

---

### Post by llongeri on 2009-02-10
I'll get some hard-disk and try it.

Luis Longeri

---

