---
title: "ATI, 1024x768@60 when using fglrx"
date: 2005-10-29
forum: Desktop Environments
---

### Post by Morrigu on 2005-10-29
ATI R9600Pro

When I'm using the "ati" driver, I get nice 1280x1024@85 desktop, but no 3D-acceleration (mesa only). When I change to "fglrx" driver, I get 3D-acceleration, but my display is only 1024x768@60. What's wrong here?

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Default Screen 1" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
	HorizSync    30-96
	VertRefresh  50-85
	Option	    "DPMS"
	Modeline "1280x1024_85.00" 159.36 1280 1376 1512 1744 1024 1025 1028 1075 -HSync +Vsync
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Driver      "ati"
	BusID       "PCI:3:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	BusID       "PCI:3:0:0"
	Option 	    "UseInternalAGPGART" "no"
EndSection

Section "Screen"
	Identifier "Default Screen 1"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600"
		Viewport  0 0
	EndSubSection
EndSection

```

As you can see, I have two devices, one for fglrx and one for ati, just to make the configuring easier to myself.

---

### Post by Morrigu on 2005-10-30
I have noticed there are many ppl with the same problem.. I wonder if fglrx doesn't even support anything else than 1024x768@60 ?

---

