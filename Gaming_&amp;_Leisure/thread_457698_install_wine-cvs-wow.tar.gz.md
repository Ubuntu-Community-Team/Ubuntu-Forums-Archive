---
title: "install wine-cvs-wow.tar.gz"
date: 2007-05-28
forum: Gaming &amp; Leisure
---

### Post by freefromXP on 2007-05-28
I Read a post on how to get WOW working with wine.  I have wine installed but wow won't play.  Used to come up look good but was like playing  on a  old 386 machine. LOL   Takes like 5-10 between each letter once I get to that point. Sound really really choppy.

  I read this post but I am using Ubuntu and don't know how to install the package.  [http://wiki.archlinux.org/index.php/World_of_Warcraft]("http://wiki.archlinux.org/index.php/World_of_Warcraft")

   I have wine-cvs-wow.tar.gz on my desktop.

  I am running XP2700 1.5g ram , ATI 9800 pro.  Berlyl and UT2004 run great. 

This is my Xorg.cgf

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
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
        Load    "dbe"
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
	Identifier	"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Driver	"ati"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
        Option  "XAANoOffscreenPixmaps"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Visual Sensa"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Monitor		"Visual Sensa"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX"         "true" 
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

Section "Extensions"
	Option "Composite" "enable"
EndSection

---

