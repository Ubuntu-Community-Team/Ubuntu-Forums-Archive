---
title: "desktop 20% larger then displayed"
date: 2008-04-08
forum: Desktop Environments
---

### Post by dogworth on 2008-04-08
the right side and bottom of the desktop are off the screen. it does the same thing with ubuntu 7.10 and fluxbuntu 7.10. the motherboard is a pico-itx which uses VIA VX700 Unified Digital Media IGP Chipset. thanks for any input.
my xorg.conf is:

```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"BenQ FP931-D"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"BenQ FP931-D"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

---

### Post by warp99 on 2008-04-08
You using a generic video driver instead of the correct xserver-xorg driver for your card. I would run 'sudo dpkg-reconfigure xserver-xorg' and choose 'via' as your driver since support for your card has been available since June of last year:

[http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=183](http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=183)

---

### Post by warp99 on 2008-04-08
(Double post)

---

