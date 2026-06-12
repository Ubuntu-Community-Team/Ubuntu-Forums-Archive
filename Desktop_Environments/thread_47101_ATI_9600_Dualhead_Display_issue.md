---
title: "ATI 9600 Dualhead Display issue"
date: 2005-07-07
forum: Desktop Environments
---

### Post by pingp on 2005-07-07
Hi, all
I am a newbie by Linux. I got Ubuntu 5.04 installed on my notebook, with original Ati driver. Here is my xorg.conf, even i modified it, I can got only one monitor working. If I connect extra Monitor before Linux up, the Notebook LCD stay blcak, otherweise I got same picture on both Monitor.

Thanx a lot, ur Lebing
**************************************************************************************

Section "Device"
	Identifier	"ATI Technologies, M10 0"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"ATI Technologies, M10 1"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"ATI Technologies, M10 0"
	Monitor		"Monitor0"
	DefaultDepth	24
	SubSection 	"Display"
			Depth		24
			Modes		"1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"ATI Technologies, M10 1"
	Monitor		"Monitor1"
	DefaultDepth	24
	SubSection 	"Display"
			Depth		24
			Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"DualHeads Layout"
	Screen		"Screen0"
	Screen		"Screen1" RightOf "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

---

