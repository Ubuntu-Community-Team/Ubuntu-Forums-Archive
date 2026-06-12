---
title: "Dualhead R9800pro wont go dualhead with Gutsy &amp; Compiz"
date: 2007-10-24
forum: Desktop Environments
---

### Post by baatz on 2007-10-24
Tonight i upgraded to gutsy gibbon, and finally compiz worked just fine (it didn' t in feisty).
In feisty though, i had a dual monitor setup working quite ok (without xinerama or compiz enabled, dualhead configged by ATI catalyst control center), both monitors had a window manager / x-server running.

To get compiz to work, i installed XGL and voila, compiz worked. The problem is, though, that my second monitor doesn't have a window manager running. I can see my mouse pointer as a nice X on the second screen, but that's it. As mentioned, in the previous distro i could fire up ati catalyst control center and mess around with the dualhead options as i wanted. Now, the control center doesn't work anymore; segfault -> coredump.

The issue therefore is: I'd like to get compiz running on a dualhead config so that i can extend my desktop on the second monitor, but i have no clue about how to get it running. I'd really appreciate any help here, so thanks in advance !

For completeness, here's the info:


kernel: 2.6.22-14 generic
distro: gusty 7.10
ATI proprietary driver: 8.37.6 fglrx


Relevant xorg.conf parts:

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
  screen "aticonfig-Screen[1]" rightof "aticonfig-Screen[0]"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "Files"
	
	# path to defoma fonts
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Horizsync	28.0	-	51.0
	Vertrefresh	43.0	-	60.0
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[1]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[1]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Screen	1
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
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

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[1]"
	Device		"aticonfig-Device[1]"
	Monitor		"aticonfig-Monitor[1]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

---

