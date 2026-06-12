---
title: "How to enable more desktop resolutions"
date: 2009-08-26
forum: Desktop Environments
---

### Post by jkonrad on 2009-08-26
I use a KVM to share a monitor among 8 machines. One of my machines is now running x64 9.04 Ubuntu. I can not set it to resolutions beyond 800 x 600. I know this monitor has a default resolution of 1280 x 1024 (from the manufacture specs, and the other computers are using that resolution successfully).

I used to mess with xorg.conf, but that file seems nearly empty (see attached or below). Where or how can I make these changes? Thank you.

My xorg.conf file (without the comment lines) from /etc/X11/xorg.conf:
"
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
"

---

### Post by jkonrad on 2009-08-27
I have tried the following, but nothing is working. Any other thoughts on how to change resolution? Thanks,

[I]"Options for resolution choices

You can add a modline in your /etc/X11/xorg.conf.

Open a terminal and type:

gtf 1280 1024 60

Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync

has to be copied in monitor section:

Section "Monitor"
Identifier "Configured Monitor"
Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
EndSection

or try adding this to xorg.conf in Section "Screen":
Option "metamodes" "1280x1024_60 +0+0; nvidia-auto-select +0+0"

The above is from realzippy"[/I]

---

### Post by jkonrad on 2009-08-27
I have been able to get farther on my own. I googled my monitor to find all the very specific settings. Then ran over to here

[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

Entered them all in and it generated a modline I copied into my xorg.conf file. After reboot it was a bit messed up, but I was able to choose a resolution 1280 x 960 that worked well. Still not sure why 1280 x 1024 doesn't work. That's listed in the monitors manual as the default resolution. However, I'm off 800 x 600 so I'm happy!

---

