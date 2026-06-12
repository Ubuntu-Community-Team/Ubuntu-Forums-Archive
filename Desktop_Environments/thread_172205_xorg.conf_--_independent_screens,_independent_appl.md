---
title: "xorg.conf -- independent screens, independent applications"
date: 2006-05-08
forum: Desktop Environments
---

### Post by darkmage072 on 2006-05-08
I'm having an issue I can't resolve where the only non-cloned setup I can run is a configuration with two completely independent desktops.

When I say completely independent, I mean that my mouse can go from one screen to another (as I intended in xorg.conf), but if I make an instance of firefox in one, and try to make an instance on the other screen, it says my profile is already in use... Seems like strange behavior to me... I also can't drag windows from one screen to another! 

When I tried using fglrxconfig utility to do a "big desktop" (single framebuffer), the second monitor showed blank screen, though the monitor was on, and I couldn't navigate my mouse to it.

It may also be noteworthy that I got this (desired) configuration working on my last install, but I was using the ati driver and not the "fglrx" driver. I would think it would work for both...

Also, in case it matters, I'm running 64-bit and an ATI Radeon 9800XT.

Thanks for your help.

```

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
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
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
	Identifier	"ATI 9800 XT[0]"
	Driver		"fglrx"
	BusID		"PCI:2:0:0"
	Option		"UseFBDev"		"true"
	Screen 0
EndSection

Section "Device"
	Identifier	"ATI 9800 XT[1]"
	Driver		"fglrx"
	BusID		"PCI:2:0:0"
	Option		"UseFBDev"		"true"
	Screen 1
EndSection

Section "Monitor"
	Identifier	"Samsung 710N[0]"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Samsung 710N[1]"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Device		"ATI 9800 XT[0]"
	Monitor		"Samsung 710N[0]"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen[1]"
	Device		"ATI 9800 XT[1]"
	Monitor		"Samsung 710N[1]"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	0	"Screen[0]" 0 0
#	Screen	1	"Screen[1]" RightOf "Screen0"
	Screen	1	"Screen[1]" 1280 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

```

-- update --

I also ran cat /var/log/Xorg.0.log | grep WW (grepping for EE and NI returned nothing), and it gave me these warnings:
```
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(WW) Ignoring request to load module GLcore
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(1): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Option "UseFBDev" is not used
```

---

