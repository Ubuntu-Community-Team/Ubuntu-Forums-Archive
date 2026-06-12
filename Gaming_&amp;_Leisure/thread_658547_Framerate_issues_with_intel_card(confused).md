---
title: "Framerate issues with intel card(confused)"
date: 2008-01-04
forum: Gaming &amp; Leisure
---

### Post by sage722 on 2008-01-04
I have an Acer laptop that's my only gaming "solution" for now(buying a desktop isn't an option) that dual boots Gutsy and Vista, but I've noticed in Ubuntu I get considerably lower framerates in games in general, or at least some games.

Typical, but the weird thing is, I can get much better performance in general desktop usage in Ubuntu as well as Tremulous(over 50fps), but games like UrbanTerror and Wolfenstein:ET run equally slower(under 20fps). Don't these games use the same engine..?:-|

I've tweaked every setting in every area of the machine(getting multicore support, lower res, 16bpp,verifying BIOS dvmt, "performance" scaling), but I can't get decent performance out of what I suppose(or pray) should be relatively milk-run applications. In Windows, I can run Dawn of War(and its mods), Call of Duty/UO with relatively good performance.Are these problems due to the different Intel graphics drivers the two OSs use, maybe?

Specs:
[LIST]
[*]Ubuntu 7.10
[*]Intel Core Duo(1.87ghz)
[*]Intel 945GM Graphics(Ubuntu uses i810 intg'd chipset)
[/LIST]

xorg.conf:
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
	Option "DRI" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-50
	VertRefresh	43-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
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
	InputDevice	"Synaptics Touchpad"
EndSection
```

I realize that I presumably can't expect much of anything from an integrated Intel card, but any input would still be appreciated...

---

### Post by trash on 2008-01-11
Intel's website and other websites i've been to say that the Intel driver is now more current than i810 and the i915... That said, I have the intel driver installed and it still sucks infact worse than what you're getting lol.

I also have these lines in my Xorg but otherwise that same as yours.

Section "Module"
        Load            "glx"
        Load            "GLcore"

---

