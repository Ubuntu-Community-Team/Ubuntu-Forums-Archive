---
title: "Visual Effects not full screen, only show as sub-region of screen"
date: 2008-03-30
forum: Desktop Effects &amp; Customization
---

### Post by shiftlock on 2008-03-30
I have a widescreen Gateway laptop with an ATI card and "Visual Effects" enabled on Ubuntu 7.10.  There is a problem with what I will call the "region" of the visual effects.

When I have no visual effects enabled, the LCD screen is used as expected.  The background image fills LCD, and full-screen windows completely cover the background, also filling the LCD panel.  Quite normal.

When I enable any of the visual effects, the region that displays the effects is smaller than the size of the LCD screen.  I still get the background image across the entire LCD panel.  The resolution of 1280 x 800 seems to be displaying correctly.  However, the region of the screen that will display windows is not the same size as the region of the screen that displays the background.

Let me be more specific with screenshots.  Attached is a screenshot of the Mouse Preferences window (just  a random window for the sake of illustration).  Notice how the bottom of the window is clipped?  (note: my background image is water with a rock; that is what you are seeing at the bottom)


It is very odd.  It is almost as if I have my full screen of 1280 x 800... with a 'region' of compizfusion effects.  Inside this compizfusion area I see all the eye candy as expected.  Unfortunately, the dimensions of this region are are smaller than the resolution of the full screen LCD panel.

Additionally, the mouse pointer still interacts with a window that happens to be in this grey-zone; off the compizfusion screen, yet still within the bounds of the LCD panel.  The mouse pointer changes to a resize-cursor as expected when nearing the edge of a window, clicking an invisible button works, and tool-tip pop ups display normall.  (I cannot get a screenshot of this mousey-ness as the cursor seems too shy to have it's picture taken)


Ubuntu: 7.10
Device: ATI Radeon Mobility X600
Drivers: Installed with ENVY

CompizConfig Display Options: 
 - Detect Outputs: unchecked
 - Outputs: removed default and replaced with "1280x800+0+0"

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X600
OpenGL version string: 2.1.7412 Release

In my xorg.conf file, I have commented out the Extensions and ServerFlags sections to combat the white-screen issue (as posted by many others in this forum):

```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"RightEdge"	"5900"
	Option		"TapTime"	"0"
EndSection


Section "Device"
	Identifier	"ATI RADEON X600"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x800"
	Horizsync	31.5-50.0
	Vertrefresh	56.0	-	65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON X600"
	Monitor		"LCD"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		#Virtual	1280	800
		Modes		"1280x800@60"	"1280x768@60"	"1280x720@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection
#Section "Extensions"
#	Option		"Composite"	"Enable"
#EndSection

#Section "ServerFlags"
#	Option		"AIGLX"	"off"
#EndSection

Section "DRI"
	Mode	0666
EndSection

```


Any ideas on how to get the Visual Effects to use the entire screen?

Let me know if you need any additional details or screen caps.  Thanks!!

---

