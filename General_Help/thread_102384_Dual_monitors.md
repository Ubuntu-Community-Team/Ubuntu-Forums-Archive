---
title: "Dual monitors"
date: 2005-12-11
forum: General Help
---

### Post by Therrol on 2005-12-11
I am trying to set up a dual monitor rig. My primary graphics card is a TNT2 with the nv drivers and my second one is an old PCI mach64 running VESA driver. Both cards work fine on their own, but when I run them both the mach64 craps out with

(II) VESA(1): initializing int10
(EE) VESA(1): shmget(lowmem) error: Invalid argument

any idea why this is happening? Here is my xorg.conf.


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	      0 "left"
        Screen        1 "right" RightOf "left"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"TNT2"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	VideoRam	32000
EndSection

Section "Device"
	Identifier	"ATI"
	Driver		"vesa"
	BusID		"PCI:0:13:0"
	VideoRam	2000
EndSection

Section "Monitor"
	Identifier	"Dell"
	Option		"DPMS"
	HorizSync	30-75
	VertRefresh	50-80
EndSection

Section "Monitor"
	Identifier	"gateway"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"left"
	Device		"TNT2"
	Monitor		"Dell"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"right"
	Device		"ATI"
	Monitor		"gateway"
	DefaultDepth	16
        SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
EndSection



Section "DRI"
	Mode	0666
EndSection

---

### Post by Ocxic on 2005-12-11
Remove the "VideoRam" options for the device with the vesa drivers and see if that does anything

---

