---
title: "compiz + dual-monitor + works but couple issues"
date: 2009-04-29
forum: Desktop Environments
---

### Post by josh6847 on 2009-04-29
I have a T40 thinkpad with ubuntu 8.1 and an ati video card.  I have had it for some time along with compiz fully functioning.  When I got a 20" acer monitor I even got the dual monitor setup (using metacity), but if I enable compiz then half of my laptop screen along with the whole acer monitor is "frozen" (the computer doesnt freeze, just half of my laptop screen plus the whole acer monitor cant be used... its almost like a layer was placed on top).  Its funny because the half of my laptop screen that isnt "frozen" (the left side) is fully functional, even with desktop cube and all.  Has anyone ever had this problem or know what I am talking about?  If you could help that would be great!

Thanks,

Josh

xorg.conf:

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
		Virtual	2700	900
		Modes		"1600x900x60"	"1024x768@60"	"1280x960@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"640x480@75"	"640x480@72"	"640x480@60"      
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection

Section "ServerFlags"
EndSection

---

