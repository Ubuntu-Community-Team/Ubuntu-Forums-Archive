---
title: "Secondary Display with no Mouse Pointer"
date: 2008-04-27
forum: Desktop Environments
---

### Post by jfdemers on 2008-04-27
Hi,

I just installed ubuntu on my ACER Travelmate laptop and I was trying to play with the xorg.conf file to do the following:

I have another CRT screen (that I want to be configured as 1280x1024) and I would like to mirror the laptop LCD screen (1280x800) on it.  I use a virtual screen size on the LCD to match the external one (See my xorg.conf file below.  Everything is OK.... except the mouse pointer on the external display (screen 1) is not visible... :- I tried the SWCursor thing (seen on a newsgroup somewhere...) and it didn't work!

Anyone has an idea?

Thanks!
jfdemers


xorg.conf file:
==============

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
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Primary Video Device"
	Boardname	"SiS Real256E"
	Busid		"PCI:1:0:0"
	Driver		"sis"
	Vendorname	"SiS"
EndSection

Section "Device"
	Identifier	"Secondary Video Device"
	Boardname	"SiS Real256E"
	Busid		"PCI:1:0:0"
	Driver		"sis"
	Vendorname	"SiS"
#	Option 		"SWCursor" "on" 
	Screen	1
EndSection

Section "Monitor"
	Identifier	"LCD Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"External Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"LCD Screen"
	Monitor		"LCD Monitor"
	Device		"Primary Video Device"
 	SubSection "Display"
                Depth           24
                Modes           "1280x800"
		Virtual		1280 1024
        EndSubSection

EndSection

Section "Screen"
	Identifier	"External Screen"
	Monitor		"External Monitor"
	Device		"Secondary Video Device"
	SubSection "Display"
	Depth	24
	Modes	"1280x1024" "1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Dual-Monitor Layout"
	InputDevice	"Synaptics Touchpad"
 	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Screen		0 "LCD Screen"
	Screen		1 "External Screen"
#	Screen 		1 "External Screen" Leftof "LCD Screen"
	Option          "Clone" "On"
	Option          "Xinerama" "On"
EndSection

---

