---
title: "Compiz Problems (Multihead)"
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by klange on 2007-10-18
I'm trying, and utterly failing, to get my laptop running Compiz while my external display either remains on Metacity or also runs compiz.
Anyway, more to the point, I'm getting an interesting error on the laptop:
compiz.real (core) - Fatal: **GLX_EXT_texture_from_pixmap is missing**
compiz.real (core) - Error: Failed to manage screen: 0
compiz.real (core) - Fatal: No manageable screens found on display :0.0
And a slightly less mysterious one on the external monitor:
compiz.real (core) - Fatal: **No GLXFBConfig for default depth, this isn't going to work.**
compiz.real (core) - Error: Failed to manage screen: 1
compiz.real (core) - Fatal: No manageable screens found on display :0.1

I believe the one on the external monitor has to do with it not being explicitly set to 24-bit color, but the error I'm getting on the laptop itself is not one I really understand (I believe I've seen it before, though)

The reason I'm trying to get two Compiz displays rather than one is simply because I can't use just one. My graphics card can't handle the resolution (with a max of 2048x2048, which is significantly less when I'm using a widescreen monitor of 1280x800, giving me only 768 pixels of extra width to work with)

If anyone can help me, it would be great. I love having two monitors, but I'd also love to have my Compiz working at the same time.


Other relevant information:
Running Ubuntu 7.10
Chipset: Intel GMA 945
Resolutions: 1280x800 and 1280x1023
Display-related X config settings:
```

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller A"
	Boardname	"i810"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Option		"MonitorLayout"	"CRT,LFP"
EndSection


Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x800"
	Horizsync	31.5-50.0
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Internal Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller A"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	800
		Modes		"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Internal Screen" 0 0
  screen 1 "screen1" leftof "Internal Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "device" #                
	Identifier	"device1"
	Boardname	"i810"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	1
	Option		"MonitorLayout"	"CRT,LFP"
EndSection
Section "screen" #                
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" #                
	Identifier	"monitor1"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
	Option		"Xinerama"	"false"
EndSection
```

---

