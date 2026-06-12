---
title: "Screen Resolution"
date: 2009-03-29
forum: General Help
---

### Post by AlexRamallo on 2009-03-29
I just got the Ubuntu live CD, and booted it perfectly, but I cant change the screen resolution from 800x600(which is my monitors minimum) to the maximum of 1240x1024 at 60Hz

this is making it REALLY hard to browse since I only get to see like 1/4 of firefox when browsing, and the website layouts are all messed up. especially my website([http://snakeinalake.site40.net](http://snakeinalake.site40.net))

how would I be able to change the screen resolution? I went to *System->Preferences->Screen Resolution*
but that only lets me pick between 640x480 and 800x600

I want to install Linux on my computer, but if I cant even figure out how to change the simple screen resolution, how am I gunna be able to use the whole operating system? >.<

---

### Post by krisluv_18 on 2009-04-19
Hi there, I just installed ubuntu 8.10 on my Inspiron 1100 a few days ago. I was having the exact same problem, but after some searching, I finally got the right combination

Section "Device"
Identifier "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
Driver "intel"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

---

### Post by krisluv_18 on 2009-04-22
Sorry, I realized that I wasn't very specific in the last post. I'm running Xubuntu, so I don't remember exactly how to get to the "terminal" app. But I believe that it's Applications->Terminal. After you've opened terminal, type in the following: ```
gksudo gedit /etc/X11/xorg.conf
``` This should bring up your xorg.conf settings. You'll see sections where it says Section "Device"; Section "Monitor"; etc., etc. as in my earlier post above.
Good luck.

---

