---
title: "Working X11 configuration File for Multiple Monitors"
date: 2005-10-21
forum: Desktop Environments
---

### Post by avatarcraeft on 2005-10-21
Hey, all,

Just wanted to post a working X11 config file that supports multiple ATI monitors.  I have 2 ATI Radeon 7500 cards, one AGP and one PCI with 3 monitors hung off of it spanned to a single desktop.  I'm sure I'm not the only person out there who wants to or has had problems getting multiple monitors to work.. so, here's a contribution:

This file is specifically for my set-up on Breezy.  You will more than likely have to modify it to meet your specific needs for your set-up and cards, but hopefully this will help you.  This is a working configuration that I use constantly. 

Good Luck!

--Ken



Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	Screen	    2  "Screen2" LeftOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
	Option	"Xinerama" "true"
EndSection

Section "Files"
	RgbPath      "/usr/X11R6/lib/X11/rgb"
	ModulePath   "/usr/X11R6/lib/modules"
	FontPath     "/usr/lib/X11/fonts/misc/"
	FontPath     "/usr/lib/X11/fonts/TTF/"
	FontPath     "/usr/lib/X11/fonts/Type1/"
	FontPath     "/usr/lib/X11/fonts/CID/"
	FontPath     "/usr/lib/X11/fonts/75dpi/"
	FontPath     "/usr/lib/X11/fonts/100dpi/"
EndSection

Section "Module"
	Load  "dri"
	# Load  "vnc"
	Load  "glx"
	Load  "extmod"
	Load  "dbe"
	Load  "xtrap"
	Load  "record"
	Load  "type1"
	Load  "freetype"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "IMPS/2"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "yes"
EndSection

Section "Monitor"

	Identifier   "Monitor0"
	VendorName   "PNR"
	ModelName    "PlanarPL1910M"
	HorizSync    24.0 - 80.0
	VertRefresh  49.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Monitor"

	Identifier   "Monitor1"
	VendorName   "PNR"
	ModelName    "PlanarPL1910M"
	HorizSync    24.0 - 80.0
	VertRefresh  49.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	
	Identifier   "Monitor2"
	VendorName   "CTX"
	ModelName    "CTXVL700"
	HorizSync    30.0 - 72.0
	VertRefresh  50.0 - 130.0
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon RV200 QW [Radeon 7500]1 "
	BusID       "PCI:1:0:0"

EndSection

Section "Device"
        Identifier  "Card1"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon RV200 QW [Radeon 7500]"
	BusID       "PCI:2:6:0"

EndSection

Section "Device"
	Identifier  "Card2"
	Driver	    "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon RV200 QW [Radeon 7500]"
	BusID	    "PCI:2:6:0"
	Screen	1
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth 24


	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes 	  "1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	DefaultDepth	24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes	  "1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen2"
	Device	   "Card2"
	Monitor    "Monitor2"
	DefaultDepth	   24 
	SubSection "Display"
		Viewport   0 0
		Depth	   24
		Modes      "800x600"
	EndSubSection
EndSection
Section "DRI"
	Mode 0666
EndSection

---

