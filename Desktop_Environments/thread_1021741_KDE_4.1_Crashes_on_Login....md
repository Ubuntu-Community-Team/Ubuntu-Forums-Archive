---
title: "KDE 4.1 Crashes on Login..."
date: 2008-12-25
forum: Desktop Environments
---

### Post by icanfly0307 on 2008-12-25
Hi everyone, I'm running Kubuntu 8.04 with KDE 4.1. Everything looks great except for the fact that I can't get my graphics card to run in 24 bit colors. The only thing that works is 16 bit colors and honestly, it looks horrible and edgy with the default wallpapers. Whenever I modify my xorg.conf to use 24 bit colors, KDE gets past the splash screen and onto the desktop but logs back out automatically. Is this a known bug with a fix to it? Thanks for your help.

**Graphics Card:** Intel 82815 Onboard Controller
**Driver:** i810 (tried intel, but that didn't work either) :(

---

### Post by wd5gnr on 2008-12-26
Can you paste your xorg.conf in? Is the graphics onboard? Do you have a BIOS setting to set the amount of RAM used? Perhaps you don't have enough to support 24 bits at the proposed resolution? Have you tried a lower resolution at 24 bits?

---

### Post by icanfly0307 on 2008-12-26
Hi, thanks for your reply. Here's my xorg.conf:

[I]# Xorg configuration created by system-config-display

Section "ServerLayout"
	Identifier     "single head configuration"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Synaptics" "CorePointer"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us+inet"
EndSection

Section "InputDevice"
	Identifier  "Synaptics"
	Driver      "synaptics"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "auto-dev"
	Option	    "Emulate3Buttons" "yes"
	Option	    "LeftEdge" "120"
	Option	    "RightEdge" "830"
	Option	    "TopEdge" "120"
	Option	    "BottomEdge" "650"
	Option	    "FingerLow" "14"
	Option	    "FingerHigh" "15"
	Option	    "MaxTapMove" "110"
	Option	    "VertScrollDelta" "20"
	Option	    "HorizScrollDelta" "20"
	Option	    "MinSpeed" "0.3"
	Option	    "MaxSpeed" "0.75"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	ModelName    "LCD Panel 1024x768"
	HorizSync    31.5 - 48.0
	VertRefresh  56.0 - 65.0
	Option	    "dpms"
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "i810"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1024x768"
	EndSubSection
EndSection[/I]

I know that my graphics card can support 24 bits because it can run fine on GNOME and Windows XP. My default and highest resolution is 1024x768 and it used to work fine in KDE 3.5.9. 16 bits looks really, really bad. And yes, the card is onboard (Intel 82815) with upto 32 MB of shared RAM. Hope this helps. Thanks. :)

PS. Kubuntu would get stuck at 800x600 with the default settings and not use the optimal resolution on a fresh install. This xorg.conf is from my Fedora 8 installation which I copied over to Kubuntu.

---

### Post by icanfly0307 on 2008-12-30
Any Suggestions? :(

---

### Post by wd5gnr on 2008-12-30
Can you check the specs on your monitor and make sure the HorizSync and VertRefresh parameters are ok? I had at least one case where the auto detect didn't work.

---

