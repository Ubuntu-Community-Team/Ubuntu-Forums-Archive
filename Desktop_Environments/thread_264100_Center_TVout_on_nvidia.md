---
title: "Center TVout on nvidia"
date: 2006-09-24
forum: Desktop Environments
---

### Post by futelihut on 2006-09-24
Hi

 I have been playing with mythtv and uses my tv for output. The problem is the image on the tv i not centered. The image is to far to the left and do not fill out the hight of the srceen. 

The hight have been solved using the overscan option, but it is still to far to the left. Is there any way to ajust this ?

Regards Morten

My xorg.conf
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
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option  "TVStandard"    "PAL-B"
	Option  "TVOutFormat"   "COMPOSITE"
	Option  "TVOverScan"    "0.7"
	Option  "RenderAccel"   "1"
	Option  "NoLogo"        "1"
	Option "ConnectedMonitor" "TV"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
#	Option		"DPMS"
#	HorizSync	28-40
#	VertRefresh	43-60
	HorizSync 30-50
	VertRefresh 50
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

