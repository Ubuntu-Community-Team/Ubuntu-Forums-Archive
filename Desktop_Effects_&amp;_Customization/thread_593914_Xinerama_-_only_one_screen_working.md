---
title: "Xinerama - only one screen working"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by Meson on 2007-10-27
I've set up Xinerama in my xorg.conf file but only one screen is working.  I can easily switch which screen works by swapping the ConnectedMonitor option
```
Section "Module"
	Load		"dbe"
	Load		"extmod"
	Load		"type1"
	Load		"freetype"
	Load		"glx"
EndSection

Section "ServerLayout"
	Identifier	"xinLayout"
	Screen		"xinScreen0"
	Screen		"xinScreen1" leftOf "xinScreen0"
	Option		"Xinerama" "true"
	InputDevice	"Generic Keyboard" "CoreKeyboard"
	InputDevice	"Configured Mouse" "Synaptics Touchpad" "CorePointer"
EndSection
Section "Device"
	Identifier	"xinDevice0"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection
Section "Monitor"
	Identifier	"xinMonitor0"
	Option		"DPMS" "true"
EndSection
Section "Screen"
	Identifier	"xinScreen0"
	Device		"xinDevice0"
	Monitor		"xinMonitor0"
	Option		"ConnectedMonitor" "DFP-1"
	Option		"MetaModes" "nvidia-auto-select"
	Option		"AllowGLXWithComposite" "True"
	Option		"RenderAccel" "True"
	Option		"AddARGBGLXVisuals" "True"
	DefaultDepth	24
	SubSection     "Display"
		Depth       24
	EndSubSection
EndSection
Section "Device"
	Identifier	"xinDevice1"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Screen		1
EndSection
Section "Monitor"
	Identifier	"xinMonitor1"
	Option		"DPMS" "true"
EndSection
Section "Screen"
	Identifier	"xinScreen1"
	Device		"xinDevice1"
	Monitor		"xinMonitor1"
	Option		"ConnectedMonitor" "DFP-0"
	Option		"MetaModes" "nvidia-auto-select"
	Option		"AllowGLXWithComposite" "True"
	Option		"RenderAccel" "True"
	Option		"AddARGBGLXVisuals" "True"
	DefaultDepth	24
	SubSection     "Display"
		Depth       24
	EndSubSection
EndSection
```

---

### Post by boast on 2007-10-27
try using twinview?

---

### Post by Meson on 2007-10-27
I was trying to go to xinerama to get two seperate desktops.  I replaced ```
	Option		"ConnectedMonitor" "DFP-1"
	Option		"MetaModes" "nvidia-auto-select"
```
with
```
Option	"MetaModes" "DFP-1: nvidia-auto-select"
```
and it seemed to work.  But still doesn't behave as I want...

I'm looking to be able to do things like have separate desktop backgrounds...

---

