---
title: "Need help configuring monitor (Unsolvable Screen 0 is not DRI capable error)"
date: 2007-06-26
forum: Desktop Environments
---

### Post by macawm on 2007-06-26
First off, my situation. I installed Feisty Server on an old Dell. I installed openbox WM. After running through every configuration I can think of I'm still unable to use X. I've run "dpkg-reconfigure xserver-xorg" several times to no avail. I've manually edited /etc/X11/xorg.conf until I'm blue in the face. I just have no other ideas on what the problem is or how to fix it. Currently all I get is a grey (blacnk) screen with a cursor. Please Help!

grep "(WW)\|(EE)" /var/log/Xorg.0.log

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(WW) intel(0): xf86AllocateGARTMemory: allocation of 1024 pages failed
(WW) intel(0): Direct rendering disabled
(EE) AIGLX: Screen 0 is not DRI capable
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(WW) intel(0): xf86UnMapVidMem: cannot find region for [0xb3a87000,0x3000000]

/etc/X11/xorg.conf

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"macintosh"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
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
	Identifier	"Intel Corporation 82815 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"DELL E551"
	Option		"DPMS"
	HorizSync	31-54
	VertRefresh	50-120
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82815 CGC [Chipset Graphics Controller]"
	Monitor		"DELL E551"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by macawm on 2007-06-26
Please delete this thread. I installed Fluxbox and it works flawlessly. Goodbye Gnome, KDE, etc.

---

### Post by ToyotaDiesel on 2007-10-22
I'm getting the same error: Screen 0 is not DRI compatible
 
on:

Ubuntu Server 7.1, fresh install of fluxbox

I get the error when I type startx

---

