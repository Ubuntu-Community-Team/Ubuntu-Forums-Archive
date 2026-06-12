---
title: "Another Dual Head Dillemma"
date: 2008-12-06
forum: Desktop Environments
---

### Post by nitecon on 2008-12-06
Well my dual-head works just fine in ubuntu, however I figured I would try kde 4.1 again after the last fiasco where it didn't even want to install, but thats neither here nor there.

Anyway here is my xorg.conf 

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
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Monitor"
	Identifier	"MAG"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"VGAScreen"
	Device		"RadeonVGA"
	Monitor		"MAG"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
		Virtual	2880 900
	EndSubSection
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

Section "DRI"
	Mode	0666
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
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"VGAScreen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "Device"
	Identifier      "RadeonVGA"
	Driver          "ati"
	BusID           "PCI:1:0:0"
	Option          "MergedFB"			"true"			# Enable MergedFB function
	Option          "MonitorLayout" 		"LCD, CRT" 		# Use LCD and CRT even if you have 2 LCD's or CRT's
	Option          "CRT2Position" 			"LeftOf" 		# Physical location of your secondary monitor
	Option          "MetaModes" 			"1440x900-1440x900" 	# Monitor Resolutions for Primary-Secondary monitors
	Option          "MergedXineramaCRT2IsScreen0" 	"true" 			# determines which screen is going to be the primary screen;
EndSection

```

To get gnome to work I still had to go to screen resolution to drag and drop my monitors where I wanted them but after logging out it worked just fine.

On KDE I tried to do the same, although system settings does not save my configuration it just keeps it as clone-of.  I have also tried running

```
xrandr --output VGA-0 --left-of DVI-0
```

When I do xrandr -q it shows the outputs as VGA-0 and DVI-0 thus the xrandr command.

Any suggestions?  I'm stuck now and would like to make this my business desktop instead of gnome...

Thanks folks!

---

### Post by CHaoSlayeR on 2009-01-10
Hi there,

I found out that you probably will be better off using the 'radeon' open source driver instead of the 'ati' one. I got dual head set up quite easily following the how-to from intel:

[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)

In addition you will get full 3D support and accelerated XV if you chip is a R1xx - R5xx (R7xx support is currently being worked on).

C]-[aoZ

---

