---
title: "trash and date in wrong place"
date: 2007-05-27
forum: Desktop Environments
---

### Post by maxepad on 2007-05-27
I modified my xorg.conf file to make my g5 imac run at native resolution. It seems however that after i did that my date and trash moved from the right towards the middle. I'm putting in a pic of the problem and the xorg.conf file. 

P.S. im new to linux so be gentle im still learning
P.P.S. thanks for all the help

[IMG]http://farm1.static.flickr.com/228/515538398_415e177a3d.jpg?v=0[/IMG]

> **_xorg.conf_**

*continued*

Section "Device"
	Identifier	"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Driver		"nv"
	BusID		"PCI:240:16:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes "1680x1050" "1024x768" "800x600" "640x480"

	EndSubSection
	SubSection "Display"
		Depth		8
		Modes "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by JAPrufrock on 2007-05-27
Put your cursor over the icon you wish to move and right click your mouse.  De-select lock to panel.  Right click again, then select move.  With your cursor you can now move the icon anywhere you want on any panel.

---

### Post by maxepad on 2007-05-27
well i feel like an idiot. thanks though

---

