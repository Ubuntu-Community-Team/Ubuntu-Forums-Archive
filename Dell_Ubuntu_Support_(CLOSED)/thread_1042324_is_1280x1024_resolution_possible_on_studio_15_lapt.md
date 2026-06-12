---
title: "is 1280x1024 resolution possible on studio 15 laptop"
date: 2009-01-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vigos on 2009-01-17
Hi,

I've been running Ubuntu 8.04.1 Hardy now on my Dell Studio 15 laptop for a while and have been pretty happy. The laptop came with a ATI Mobility Radeon HD 3400 card, (funny thing is I dont see this card when I look under Mobility Radeon on the ATI homepage here:

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html))


I've been checking the forums and haven't been able to figure things out maybe its just not supported by the ATI drivers in linux.

Anyway here's some information that may give you some ideas

Output of lspci -nn | grep VGA

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series [1002:95c4]

Output of fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 3400 Series
OpenGL version string: 2.1.7659 Release

Output of xrandr

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       60.0* 
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.0  
   640x480        60.0  
   640x400        60.0  
   512x384        60.0  
   400x300        60.0  
   320x240        60.0  
   320x200        60.0  


I've even tried to set 1280x1024 manually in the xorg.conf but no changes:

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"
	EndSubSection
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection


Would appreciate any help with this or even just to know thats all thats supported

Thanks!

---

### Post by vigos on 2009-01-19
ok well I there is a pretty simple answer to this and feel kind of stupid but the display only supports 1280x800 so thats why. I also get the same thing when I boot to windows.

---

