---
title: "Setting Default Mouse"
date: 2005-11-02
forum: Desktop Environments
---

### Post by Dagonus on 2005-11-02
I'm trying to get the pen working for my Compaq TC1000 and in the readme for the driver I'm using for it, it has a problem listed and a solution for it. The problem is, being relatively new to linux, I don't know how to go about doing it. I imagine it might be as simple as adding or changing a line in xorg.conf but, I'm not certain.  

From the read me:

Problem 2:  X Server crash during GUI startup (Particularly Gnome). 

Solution:   You must have a regular mouse defined as the default pointer
	    even if no mouse is used.  During startup, Gnome attempts to
	    set mouse acceleration for the default pointer.  Since the
	    pendrivers are absolute pointers, and acceleration is meaningless,
	    they do not take well to attempts to set it :-)

---

### Post by iH8forcedRegistration on 2005-11-02
Try putting this (or something like it) in your xorg.conf
```

Section "InputDevice"
    Identifier	"Compaq Pen Thing"
    Driver		"mouse"
    Option		"SendCoreEvents" "true"
   # put the configuration stuff you already have for your pen here 
EndSection

Section "InputDevice"
    Identifier "Configured Mouse"
    Driver      "mouse"
    Option     "CorePointer"
    Option     "Device"   "/dev/input/mice"
    Option     "Protocol" "Auto"
EndSection

```

Then, add this line to the ServerLayout section of xorg.conf:
```
InputDevice "Compaq Pen Thing"
```

I *think* that should do it. But, as you can probably see from other threads, I'm not getting along so well with my mouse either.

---

### Post by Dagonus on 2005-11-05
Tried adding those in. No luck.
How do i specify the default mouse so that the system doesn't try to accelerate the pen?

xorg.conf currently looks like this:

```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri" 
#	Load 	"GLcore"  #Note: Line and Comment out Added to match demo 
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Indentifier	"mouse0"
	Driver		"tc1k"
	Option		"AlwaysCore"		"on"
	Option		"Device" 		"/dev/ttyS0"
	Option		"BaudRate"		"19200"
	Option		"MaximumXPosition"	"8600"
	Option		"MaximumYPosition"	"6485"
	Option		"MinimumXPosition"	"154"
	Option 		"MinimumYPosition"	"110"
	Option		"InvertY"
	Option		"SendCoreEvents"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 Go]"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 Go]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
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
	InputDevice	"mouse0"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by iH8forcedRegistration on 2005-11-06
The default mouse will be whichever one has this line in it:
```
Option "CorePointer"
```

Right now, your default mouse is ConfiguredMouse

What's mouse0?

---

