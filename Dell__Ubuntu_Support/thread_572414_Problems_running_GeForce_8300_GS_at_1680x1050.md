---
title: "Problems running GeForce 8300 GS at 1680x1050"
date: 2007-10-10
forum: Dell  Ubuntu Support
---

### Post by mikwat on 2007-10-10
I just purchased a new Dell XPS 410 N with Ubuntu 7.04 pre-installed which comes with the nVidia GeForce 8300 GS. I'm trying to use this machine with a 22" ViewSonic VX2235wm monitor running natively at 1680x1050. After going through "dpkg-reconfigure xserver-xorg" gdm successfully boots at the correct resolution, however there is slight flicker and fuzziness (which makes me feel like I'm going blind). I have tried all of the suggestions from Ubuntu ( [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto) ) without luck. There doesn't appear to be a binary driver from nVidia supporting this card either.

When I try connecting the monitor using a DVI cable, I get a blank screen and the monitor reports "Out of Range H 65 KHz, V 60 Hz" (although both of those freqencies are within the manufacturer's specification).

Any suggestions?

---

### Post by Perfect Storm on 2007-10-10
Please post your xorg.conf, also your monitor specs.

---

### Post by mikwat on 2007-10-10
Monitor Specs:
[http://www.viewsonic.com/products/desktopdisplays/lcddisplays/xseries/vx2235wm/](http://www.viewsonic.com/products/desktopdisplays/lcddisplays/xseries/vx2235wm/)

Frequency  	Fh: 30~82kHz, Fv: 50~85Hz

xorg.conf:
```

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NVIDIA Default Card"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"VX2235wm-3"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NVIDIA Default Card"
	Monitor		"VX2235wm-3"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by mikwat on 2007-10-10
I have fixed my display problems.  I installed the nVidia driver from [http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html) and followed the
instructions [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

