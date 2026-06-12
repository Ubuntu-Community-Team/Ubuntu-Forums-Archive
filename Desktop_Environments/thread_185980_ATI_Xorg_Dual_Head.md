---
title: "ATI Xorg Dual Head"
date: 2006-06-01
forum: Desktop Environments
---

### Post by slavik on 2006-06-01
I have 2 monitors. One is 1280 by 1024 and other is 1024x768. I want to set them up such that they use the above native resolutions (LCD monitors).

Here is my xorg.conf:
```

Section "Device"
	Identifier	"X300-0"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Device"
	Identifier	"X300-1"
	Driver		"fglrx"
	BusID		"PCI:1:0:1"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"DELL 1707FP"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-76
EndSection

Section "Monitor"
	Identifier	"DELL"
	Option		"DPMS"
	#HorizSync	30-81
	#VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"X300-0"
	Monitor		"DELL 1707FP"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"X300-1"
	Monitor		"DELL"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes	       "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Multihead Layout"
	Screen		"Screen0" 0 0
	Screen		"Screen1" RightOf "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

```

With that configuration, the second monitor fails to initialize with error that no proper display mode was found for it. I get same error if I comment out the refresh rates.

My main monitor is Dell 1707FP, the secondary (the one that doesn't want to work) is a Dell E193FP.

The thing is, that fireglconfig generates a configuration that puts the secondary monitor resolution to 1280x1024, so it winds up not displaying the right and bottom portions of the screen.

---

### Post by Zak Mandhro on 2006-06-01
Here's my xorg.conf for dual screen using fglrx. You may be able to use it.

```

Section "Files"
FontPath	"/usr/share/X11/fonts/misc"
FontPath	"/usr/share/X11/fonts/cyrillic"
FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
FontPath	"/usr/share/X11/fonts/Type1"
FontPath	"/usr/share/X11/fonts/100dpi"
FontPath	"/usr/share/X11/fonts/75dpi"
# path to defoma fonts
FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load	"bitmap"
Load	"ddc"
Load	"dri"
Load	"extmod"
Load	"freetype"
Load	"glx"
Load	"int10"
Load	"type1"
Load	"vbe"
EndSection

Section "InputDevice"
Identifier	"keyboard"
Driver		"kbd"
Option		"CoreKeyboard"
Option		"XkbRules"	"xorg"
Option		"XkbModel"	"pc104"
Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
Identifier	"mouse"
Driver		"mouse"
Option		"CorePointer"
Option		"Device"		"/dev/input/mice"
Option		"Protocol"		"ExplorerPS/2"
Option		"ZAxisMapping"		"4 5"
Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
Identifier	"touchpad"
Driver		"synaptics"
Option		"SendCoreEvents"	"true"
Option		"Device"		"/dev/psaux"
Option		"Protocol"		"auto-dev"
Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
Identifier	"video1"
Driver		"fglrx"
BusID		"PCI:1:0:0"
VideoRam	131072
Option "KernelModuleParm" "agplock=0"
#Option "DesktopSetup"               "0x00000000" #single
#Option "DesktopSetup"               "0x00000201" #big
Option "DesktopSetup"               "0x00000000" #dual
#Option "DesktopSetup"               "0x00000100" #clone
Screen 0
EndSection

Section "Device"
Identifier	"video2"
Driver		"fglrx"
BusID		"PCI:1:0:0"
VideoRam	131072
Option "KernelModuleParm" "agplock=0"
Screen 1
EndSection

Section "Monitor"
Identifier	"internal"
Option		"DPMS"
HorizSync	30-70
VertRefresh	50-160
EndSection

Section "Monitor"
Identifier	"external"
Option		"DPMS"
HorizSync	30-70
VertRefresh	50-60
EndSection


Section "Screen"
Identifier	"primary"
Device		"video1"
Monitor		"internal"
DefaultDepth	24
SubSection "Display"
Depth		24
Modes		"1680x1050" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "Screen"
Identifier	"secondary"
Device		"video2"
Monitor		"internal"
DefaultDepth	24
SubSection "Display"
Depth		24
Modes		"1280x768"
EndSubSection
EndSection

Section "ServerLayout"
Identifier	"now"
Screen		"primary"
Screen		"secondary" RightOf "primary"
InputDevice	"keyboard"
InputDevice	"mouse"
InputDevice	"touchpad"
EndSection

Section "DRI"
Mode	0666
EndSection

```

---

