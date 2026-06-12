---
title: "Display On Another Monitor"
date: 2008-10-19
forum: Desktop Environments
---

### Post by ctull on 2008-10-19
im using a laptop and i would like to view my desktop on another monitor, is this possible with ubuntu

---

### Post by Absynthe on 2008-10-19
[http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php](http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php)

This will probably do

---

### Post by ctull on 2008-10-19
More along the lines of with windows u can press Fn( Function Key) + CRT/LCD and view your desktop tru another monitor or projector.
Any Help there........

---

### Post by loomsen on 2008-10-20
Sure it is.

If your monitor is working already, and you just wanna start a specific application on the other one, 

DISPLAY=:0.1 some_command

would launch it on DISPLAY 0.1

If you don't have your xorg.conf configured you have different options to do so.

For example this is my Serverlayout, I got my TV attached to my Laptop:

```
 
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice	   "Synaptics Touchpad"
EndSection

Section "Files"
	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
    Load           "dbe"
    Load		"record"
    Load		"dri"
EndSection

Section "ServerFlags"
    Option		"Xinerama"	"0"
EndSection

Section "InputDevice"
	Identifier	"Mouse0"
	Driver		"mouse"
	Option		"Protocol"			"auto"
	Option		"Device"				"/dev/psaux"
	Option		"Emulate3Buttons"		"no"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"		"True"
	Option		"Device"				"/dev/psaux"
	Option		"Protocol"			"auto-dev"
	Option		"HorizTwoFigerScroll"	"True"
	Option		"VertTwoFingerScroll"	"True"
EndSection

Section "InputDevice"
	Identifier	"Keyboard0"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
	Identifier	"Monitor0"
	VendorName	"Unknown"
	ModelName	"CPT"
	HorizSync	30.0 - 75.0
	VertRefresh	60.0
	Option		"DPMS"
EndSection

Section "Monitor"
    # HorizSync source: builtin, VertRefresh source: builtin
	Identifier	"Monitor1"
	VendorName	"Unknown"
	ModelName	"CRT-0"
	HorizSync	28.0 - 55.0
	VertRefresh	43.0 - 72.0
	Option		"DPMS"
EndSection

Section "Device"
    Identifier		"Videocard0"
    Driver			"nvidia"
    VendorName		"NVIDIA Corporation"
    BoardName		"GeForce 8600M GT"
    BusID          	"PCI:1:0:0"
    Option			"AllowIndirectPixmaps"		"true"
    Option			"Coolbits"	"1"
    Option 	   		"AllowGLXWithComposite"	"true"
#    Option	   		"XAANoOffscreenPixmaps"
	Option		"NoLogo"	"true"
    Screen       		0
EndSection

Section "Device"
    Identifier		"Videocard1"
    Driver			"nvidia"
    VendorName		"NVIDIA Corporation"
    BoardName		"GeForce 8600M GT"
    BusID			"PCI:1:0:0"
    Option			"AllowIndirectPixmaps"		"true"
    Option			"Coolbits"	"1"
    Option			"AllowGLXWithComposite"	"true"
#    Option			"XAANoOffscreenPixmaps"
	Option		"NoLogo"	"true"
    Screen			1
EndSection

Section "Screen"
# Laptop
    Identifier		"Screen0"
    Device			"Videocard0"
    Monitor		"Monitor0"
    	DefaultDepth    	24
    Option			"TwinView" "0"
    Option			"AllowGLXWithComposite"	"true"
    Option			"AddARGBGLXVisuals"		"true"
    Option			"TwinViewXineramaInfoOrder" "DFP-0"
#    Option			"metamodes" "DFP: 1440x900 +0+0"
#    Option			"DPI"		"110 x 108"
    SubSection		"Display"
        Depth			24
        Modes		"1440x900"
    EndSubSection
EndSection

Section "Screen"
# Fernseher
    Identifier		"Screen1"
    Device			"Videocard1"
    Monitor		"Monitor1"
    	DefaultDepth		24
    Option			"TwinView"	"0"
    Option			"TVStandard"	"PAL-B"
    Option			"AllowGLXWithComposite"	"true"
    Option			"AddARGBGLXVisuals"		"true"
#    Option			"metamodes" "CRT: 1360x768 +0+0,1024x768 +0+0"
#    Option			"DPI"		"100 x 75"
    SubSection		"Display"
	Depth			24
#	Modes		"nvidia-autoselect"
	Modes		"1024x768"
    EndSubSection
EndSection

Section "Extensions"
	Option 	"Composite"	"Enable"
	Option 	"RENDER"	"true"
	Option 	"DAMAGE"	"true"
EndSection


```

This creates a layout like this:

```

(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Videocard1"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Synaptics Touchpad"

```

[Reference and Guide](http://linux.die.net/man/5/xorg.conf)

---

### Post by ctull on 2008-10-26
Thanks Loomsen

---

