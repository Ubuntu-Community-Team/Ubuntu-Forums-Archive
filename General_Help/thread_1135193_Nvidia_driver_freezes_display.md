---
title: "Nvidia driver freezes display"
date: 2009-04-24
forum: General Help
---

### Post by meanmrmustard on 2009-04-24
Hardy Heron with a GeForce 7300 GS video card.
Both have been working fine since the original installation.


A couple days ago, first thing in the morning,  I found my machine at the log in screen. I incorrectly assumed that it had re-booted. I found yesterday that what happened is that X had simply shut down an restarted.

I ran xfix from recovery mode and things were normal again - resolution was at maximum (monitor is an Acer 23.5" widescreen LCD) but with no Compiz running. Enabling the proprietary driver only resulted in the screen freezing - then the cursor will move for a second or two only to freeze again. Subsequent attempts to run xfix result in 800x600 resolution and the xorg.conf shows no line for a driver.

I've ssh'd into the box and looking at logs - dmesg and kernel logs show nothing that looks unusual - it will stop scrolling for a few seconds at a time while I'm looking through them, then resumes scrolling.

I've tried installing the Nvidia driver with Envyng and got the same results - freezing. 

I can't even seem to use the vesa driver - or at least xorg.conf doesn't show it being used - or any driver for that matter.

The only thing I can think of that I haven't tried is compiling the Nvidia driver from source. I guess that's next.

Any ideas?

The present xorg.conf at 800x600 no nvidia driver
```
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

---

### Post by meanmrmustard on 2009-04-26
So I'm guessing the best advice is re-install?

---

