---
title: "ATI Radeon HD 2400 XT and Gutsy"
date: 2008-01-17
forum: Desktop Environments
---

### Post by charlie. on 2008-01-17
I'm trying to install Gutsy on a laptop with an HD 2400 XT graphics card.

Out the box, Gutsy wouldn't run. The vesa driver and presumably the "bulletproof X" thing didn't work.

I tried xorg-driver-fglrx, it wouldn't work. (I got "no device found" from X)

I tried these instructions (file:///home/martindale/Downloads/ati-driver-installer-8.443.1-x86.x86_64.run) with the driver from ATI's download site. With this, I managed to get X to start but I still have problems:

glxgears crashes X.

Gnome Terminal won't open. (and, because it won't open, I can't run fglrxinfo. I tried running it in a non-X session (Ctrl + Alt + F1) but that didn't work either. It hung.)

I also tried two methods to get compiz fusion working: installing xserver-glx and whitelisting fglrx. I can't seem to get compiz working.

There are no errors in the Xorg error log.

---

### Post by charlie. on 2008-01-17
Here's xorg.conf:

```
# Stephen's xorg.conf

Section "ServerLayout"
	Identifier     "My Layout"
	Screen      0  "My Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
	Identifier  "Notebook Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI HD 2400 XT"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID	    "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "My Screen"
	Device     "ATI HD 2400 XT"
	Monitor    "Notebook Monitor"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	"Composite" "Disable"
EndSection

Section "ServerFlags"
        Option "AIGLX"        "false"
EndSection
```

---

