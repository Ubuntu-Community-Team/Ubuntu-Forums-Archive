---
title: "window borders and effects not working in compiz (working in metacity)"
date: 2009-04-10
forum: Desktop Environments
---

### Post by josh6847 on 2009-04-10
I just spent some time getting my 1600x900 LCD monitor hooked up with my laptop for dual monitor.  Unfortunately, metacity is the only windows manager that works.  When compiz is selected, the window borders and all effects are gone.  Any ideas?  Here is my xorg.conf file:

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Driver		"ati"
	Busid		"PCI:1:0:0"
	Option		"LVDSBiosNativeMode"	"false"
	Option		"GARTSize"	"64"
	Option		"AGPSize"	"64"
	Option		"AGPMode"	"4"
	Option		"XAANoOffscreenPixmaps"
	Option		"AGPMode"	"8"
	Option		"AGPFastWrite"	"True"
	Option		"EnablePageFlip"	"true"
	Option		"EnableDepthMoves"	"true"
	Option		"UseInternalAGPGART"	"no"
	Option		"BackingStore"	"on"
	Option		"UseInternalAGPGART"	"no"
	Option		"DMAForXv"	"true"
	Option		"AccelMethod"	"XAA"
	Option		"ColorTiling"	"on"
	Option		"AccelDFS"	"true"
	Option		"TripleBuffer"	"true"
	Option		"DynamicClocks"	"on"
	Option 		"RenderAccel"	"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  	modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  	modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  	modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  	modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  	modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  	modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  	modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  	modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  	modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  	modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  	modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	modeline  "1600x900@60" 119.00 1600 1696 1864 2128 900 901 904 932 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	3200	900
		Modes		"1600x900@60"   "1024x768@60"	"1280x960@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"640x480@75"	"640x480@72"	"640x480@60"      
	EndSubSection
EndSection

Thanks

---

