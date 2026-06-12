---
title: "odd window behavior with feisty and gnome"
date: 2007-04-25
forum: Desktop Environments
---

### Post by yoorobot on 2007-04-25
Hi,

Whenever I maximize a window, the window goes black.  By minimizing it then remaximizing via the panel the content reappears, but I am no longer able to close or minimize it via the titlebar buttons (I can unmax and/or close via the panel).

Anyone else having this problem?  Any solutions?

here's my xorg.conf:


Section "Device"
	Identifier	"NVIDIA Corporation NV44 [Quadro NVS 285]"
	Driver		"nvidia"
	Busid		"PCI:64:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"

Option "RenderAccel" "True"
Option "AllowGLXWithComposite" "True"
Option "backingstore" "True"
Option "TripleBuffer" "True"

	Option "TwinView" "True"
	Option "TwinViewOrientation" "RightOf"   
	Option "UseEdidFreqs" "true"
	Option "MetaModes" "1280x1024,1280x1024"
#; 1024x768,1024x768"
	Option "UseDisplayDevice" "CRT" 
	Option "DynamicTwinView" "false"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV44 [Quadro NVS 285]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

---

### Post by FuturePilot on 2007-04-25
Are you using the Desktop Effects? If so this is a bug in the Nvidia driver and there's not much you can do about it.

---

### Post by yoorobot on 2007-04-26
this problem occurs whether I enable desktop effects or not.
In fact, when enabled, these blackened windows are at least usable to the extent that I am able to get them to display their contents via "panel jiggling"...

---

### Post by orb9220 on 2007-04-26
> Device "NVIDIA Corporation NV44 [Quadro NVS 285]"

Is this a legacy card with less than 128mb of ram?

---

### Post by yoorobot on 2007-04-26
I believe it has at least 128mb or ram.

---

