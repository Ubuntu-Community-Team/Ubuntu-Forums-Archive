---
title: "Yet another WoW/Wine thread."
date: 2007-05-30
forum: Gaming &amp; Leisure
---

### Post by renzuken on 2007-05-30
Well basically I've tried everything now to try set up WoW with a new Ubuntu installation under WINE. After 2 weeks now of stubbornly trying everything to make it work I have to break down and ask for help.

Firstly my laptop isn't exactly perfect for working with WoW however it managed perfectly fine under Windows XP. At first my problem was getting the 'World of warcraft cannot start up 3D acceleration" to which I downloaded new drivers. However now when I start up WoW under wine my screen now goes pitch black and my system just stops responding.

Help! I'm tearing my hair out :(

---

### Post by blazercist on 2007-05-30
what guide did you use to install wow?  also are you using beryl/compiz? if so you need to disable and not only disable them but if you are using xgl you need to use a normal gnome session... also your hardware specs would help as well as any console output you get.

---

### Post by renzuken on 2007-05-30
[https://help.ubuntu.com/community/WorldofWarcraft?highlight=%28worldofwarcraft%29](https://help.ubuntu.com/community/WorldofWarcraft?highlight=%28worldofwarcraft%29) 

Is the guide I used to install WoW in the first place. The installation seems to be fine.
I'm not using Beryl or Compiz and am using the normal Gnome session.
At the moment running 1.5Ghz intel processor and 512MB RAM.

From the glxinfo | grep rendering command I get 'Yes' and from glxinfo | grep 'OpenGL version' : OpenGL version string: 1.3 Mesa 6.5.2

The following is also my xorg.conf file.
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
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by hikaricore on 2007-05-30
It's the intel card that's going to give you the most trouble.  The drivers for linux released by intel are terrible, and despite community efforts have not gotten much better.
WoW will probably not run well with that card under linux, I suggest getting a nvida card (gforce 6200 or higher) for best results.

I'm not going to flat out say you won't have luck, as I have known a few people with integrated intel cards that can play WoW just fine.

But I'm warning you ahead of time, most people get 8-15fps with alot of skipping/lag and missing textures.  Both d3d and opengl modes fail for the most part.

---

### Post by blazercist on 2007-05-31
glxinfo outputs Mesa that means you don't have the driver properly installed and 3d acceleration isnt working, this is most likely your biggest problem...

---

### Post by hikaricore on 2007-05-31
> **blazercist said:**
> glxinfo outputs Mesa that means you don't have the driver properly installed and 3d acceleration isnt working, this is most likely your biggest problem...

No, their 3d acceleration is working properly.

> **renzuken said:**
> 
_From the glxinfo | grep rendering command I get '**Yes**' _and from glxinfo | grep 'OpenGL version' : OpenGL version string: 1.3 Mesa 6.5.2


---

