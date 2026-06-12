---
title: "Rendering problem after resolution change"
date: 2008-03-07
forum: Desktop Environments
---

### Post by nexnicholai on 2008-03-07
Hi, Im trying to get a Samsung SyncMaster 226BW to work with gnome and a Radion X1950.

I first started by following the steps in [this post]("http://ubuntuforums.org/showthread.php?t=716902").

This almost worked. The screen size changed but a strip on the right side of the monitor does not render correctly.

Here is some of my xorg.conf.
The two changes I've made so far:
Set Composite option to 1 to get desktop effects to work
Added "1680x1050" under Screen section

```

Section "Device"
	Identifier	"Generic Video Card"
	Boardname	"ati"
	Busid		"PCI:3:0:0"
	Driver		"fglrx"
	Screen	0
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes	"1680x1050"	"1600x1200@60"	"1600x1200@65"	"1400x1050@60"	"1280x960@75"	"1280x1024@60"	"1280x960@60"	"1280x1024@75"	"1152x864@75"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
```

Attached is a screenshot of my desktop. Its not as obvious in the pic, but notice how the lines go straight on the right side of the picture. This is the area that is not being rendered. 

Any help would be greatly appreciated.

-nex

---

### Post by nexnicholai on 2008-03-07
Update:

I messed around a bit and changed this line:

```
		Virtual	1600	1200
```

to this:

```
		Virtual	1680	1050
```

I have no idea why this worked. Feel free to reply with an explanation or if this was a bad fix.

-nex

---

