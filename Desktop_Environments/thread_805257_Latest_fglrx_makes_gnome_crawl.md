---
title: "Latest fglrx makes gnome crawl"
date: 2008-05-23
forum: Desktop Environments
---

### Post by bethebunny on 2008-05-23
My situation:
OS: Debian amd64 architecture
Graphics card: ATI Radeon HD3870
Monitors: 1024x768, 1280x1024 LCDs

I just started out with a fresh Debian install, ran Envy to install the latest fglrx driver which (finally) supports the HD3870 graphics card. As long as fglrx is set as the driver in my xorg.conf, Gnome is worthless; windows open just fine, but moving them around or scrolling them drops the FPS to <1 with just Gnome and the OS running, haven't even tried running anything hardware accelerated yet.

I need hardware acceleration to work so I can game/watch video on one monitor while working on the other; since working usually entails coding I would much prefer to do this on a linux box, and would like to avoid the $200 license cost of VMware.

This brings up an additional problem: dual-headed display under the aticonfig tool apparently doesn't support monitors of different resolutions. I do a
```
"sudo aticonfig --dtop=horizontal,reverse --overlay-on=1"
```
which works as intended, sets my system resolution to 2048X768, and then try a
```
"sudo aticonfig --resolution=0,1280x1024"
```
only to receive the error "screen0 does not exist".
I only really need hardware acceleration on one monitor, but there should be no reason I can't have it on both. Any help towards either end would be much appreciated.

xorg.conf with fglrx (laggy):
*UPDATED*
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/X11R6/lib/X11/fonts/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/X11R6/lib/X11/fonts/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/X11R6/lib/X11/fonts/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/X11R6/lib/X11/fonts/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/usr/X11R6/lib/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
	Option	    "XkbVariant" "dvorak"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier   "Philips 150B"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc ATI Default Card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "DesktopSetup" "horizontal,reverse"
	Option	    "OverlayOnCRTC2" "1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc ATI Default Card"
	Monitor    "Philips 150B"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```

xorg.conf without fglrx (default, basically):
```
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/X11R6/lib/X11/fonts/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/X11R6/lib/X11/fonts/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/X11R6/lib/X11/fonts/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/X11R6/lib/X11/fonts/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	FontPath	"/usr/X11R6/lib/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"dvorak"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc ATI Default Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Philips 150B"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"Philips 150B"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Edit: Hardware acceleration appears to be working just fine from preliminary tests (VLC playing DVDs, Lango), gnome still staggering.

---

