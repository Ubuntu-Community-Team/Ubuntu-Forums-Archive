---
title: "Beryl with Radeon 9250 and Rage 3d II"
date: 2007-04-28
forum: Desktop Effects &amp; Customization
---

### Post by Lothas on 2007-04-28
Hi, I have 2 displays connected to my PC through 2 different cards: An ATI Radeon 9250 (AGP) and an ATI Rage 3D II+ (PCI). So far, I managed to make both work under Feisty with Xinerama but 3D acceleration is a problem... It only works "properly" when the main display (on Radeon) is the only one abilitated in xorg.conf.

I just recently installed Beryl and managed to make it work with only one of the displays. On the secondary display it manages to slowly rotate the 3D Cube but it doesn't show anything on the desktops.

I'd like to know if there's a way for me to keep the effects at least on one display (mostly the scaling effect).

Thanks :)

---

### Post by Lothas on 2007-04-28
Bump

---

### Post by Lothas on 2007-04-29
Please... I'm really pleased with all the nice effects and tools (even though the rain isn't working :( ) but I also really like having twice the space to look at **constantly**. Don't make me choose between the 2... :cry:

---

### Post by Lothas on 2007-04-30
One last shameless Bump before I cry myself to sleep :(

---

### Post by antiram on 2007-04-30
you can use 9250 with mergedfb for both display, without using the rage card. Should work with compiz, have not tested beryl.
edit Modeline, CRT2Hsync, CRT2VRefresh and Monitor1 

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "v4l"
        Load    "vbe"
EndSection

Section "ServerLayout"
	Identifier	"Multihead layout"
	Screen		0 "Screen0" LeftOf "Screen1"
	Screen		1 "Screen1" 0 0
	InputDevice	"Keyboard0" "CoreKeyboard"
	Option		"MonitorLayout" "TMDS,CRT"
	Option		"MergedFB" "on"
EndSection

Section "InputDevice"
	Identifier	"Keyboard0"
	Driver		"kbd"
	Option		"XkbModel" "pc102"
	Option		"XkbLayout" "de"
	Option		"XkbVariant" "nodeadkeys"
	#Option		"XkbOptions" "grp:shifts_toggle,grp_led:scroll"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	VendorName	"AOC"
	ModelName	"9G"
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	VendorName	"Panasonic"
	ModelName	"TV"
	HorizSync	15-18
	VertRefresh	49-51
	Option		"CRT2HSync" "15-18"
	Option		"CRT2VRefresh" "49-51"
	ModeLine	"720x576" 14.0625 720 760 800 900 576 576 591 625 +hsync +vsync interlace composite	
EndSection

Section "Device"
	Identifier	"Videocard0"
	Driver		"radeon"
	VendorName	"GIGABYTE"
	BoardName	"ATI Technologies Inc RV280 [Radeon 9200 PRO] (Primary)"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"Videocard1"
	Driver		"radeon"
	VendorName	"GIGABYTE"
	BoardName	"ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary)"
	BusID		"PCI:1:0:0"
	#Option		"ForceMinDotClock" "14MHz"
	Screen		1
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Viewport	0 0
		Depth		24
		Modes		"1280x1024" "720x576" 
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"Videocard1"
	Monitor		"Monitor1"
	DefaultDepth	24
	SubSection "Display"
		Viewport	0 0
		Depth		24
		Modes		"720x576"
	EndSubSection
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by Lothas on 2007-04-30
Wait... that solution would "bypass" the second graphics card??? I mean, the radeon 9250 has only 1 VGA output and one S-Video output (for TV). I guess I'll go ahead and give it a try. I've lost some respect for the Blue screen of death after encountering it a few times.

---

### Post by Lothas on 2007-04-30
Apparently it's as I thought... you actually have 1 monitor and one TV connected to your radeon. Anyway, I tried using MergedFB and it was really weird... Like having two different PCs sharing a pointer... Xinerama is WAY better. So, I tried activating Beryl and my PC died (twice :( ). I restored my backed-up xorg.conf file and now Beryl works just fine.

So... I'm still looking for a solution.

---

### Post by Lothas on 2007-05-01
:-? Bump

---

