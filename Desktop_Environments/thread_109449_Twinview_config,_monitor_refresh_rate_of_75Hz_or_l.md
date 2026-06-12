---
title: "Twinview config, monitor refresh rate of 75Hz or less, how to do it?"
date: 2005-12-28
forum: Desktop Environments
---

### Post by deunan on 2005-12-28
Dear all!

I've tried many things, read various postings here on the forum, but can't seem to get my twinview settings like I wanted.

I want to operate the monitors at 75Hz refresh rate. or 60Hz if possible.  Well, it is possible on a certain Commercial Proprietry Closed Sourced OS.  Basically I wanna duplicate my setup from the OS which I migrated from to Ubuntu.

Seems that, I can only get the max, 2560x1024 with 75Hz and 2048x768 with 85Hz!  Tried modifying the various settings in the xorg.conf, but I can't seem to be able to get it right..

Would be very grateful if someone can review my xorg.conf file and give comments.

Sincere regards and thanks!

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)

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
	Load	"i2c"
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
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"nodeadkeys"
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
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	# Added Extra for Dual Display
	VideoRam 131072
	Option "NvAGP" "2"
	Option "TwinView" "true"
	Option "RenderAccel" "true"
	Option "UseEdidFreqs" "true"
	Option "TwinViewOrientation" "LeftOf"
	Option "MetaModes" "1280x1024, 1280x1024; 1024x768, 1024x768; 800x600, 800x600; 640x480, 640x480;"
	Option "ConnectedMonitor" "CRT, CRT"
	Option "SecondMonitorHorizSync" "30-86"
	Option "SecondMonitorVertRefresh" "50-160"
	Option "NoLogo"
	Option "CursorShadow" "1"
	Option "Coolbits" "1"
	# Added Extra for Dual Display
EndSection


Section "Monitor"
	Identifier	"DELL P780"
	Option		"DPMS"
	HorizSync    30.0 - 85.0
        VertRefresh  48.0 - 120.0 
EndSection

#Section "Monitor"
#	Identifier	"ViewSonic 17PS"
#	Option		"DPMS"
#	HorizSync    30.0 - 86.0
#       VertRefresh  50.0 - 160.0 
#EndSection

Section "Screen"
	Identifier	"Screen 1"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"DELL P780"
	DefaultDepth	24

	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
		ViewPort 0 0
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
		ViewPort 0 0
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
		ViewPort 0 0
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
		ViewPort 0 0
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
		ViewPort 0 0
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
		ViewPort 0 0
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen 1"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

