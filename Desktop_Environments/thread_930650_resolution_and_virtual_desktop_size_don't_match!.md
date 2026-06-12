---
title: "resolution and virtual desktop size don't match!"
date: 2008-09-26
forum: Desktop Environments
---

### Post by dagoss on 2008-09-26
For reasons that are unknown to me, my virtual desktop is the proper size (1680x1040) while the actual screen resolution is smaller (1440x900).  The option to change the resolution to 1680x1040 within the KDE4 system settings has the word (auto) next to it.  My xorg.conf has 1680x1040 as the ONLY option for Modes in the screen section, so KDE must be overriding it somewhere somehow...

This wasn't an issue before.  I was using the emulator Gens and after switching from full screen back to windowed, this problem started.  I tried restarting X and restarting my system, but to no avail.  I'm not sure how this happened since I didn't actually touch any configuration files (maybe Gens did this during installation?)
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	ModelName	"Acer AL2216W"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes "1680x1040@60"
	EndSubSection
EndSection

```

---

