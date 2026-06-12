---
title: "Games not being scaled to full screen?"
date: 2006-06-07
forum: Gaming &amp; Leisure
---

### Post by barakaspeed on 2006-06-07
I'm having difficulty getting my games to play in full screen mode.  The games have the option enabled for full screen within their individual settings, but what I get when I play them is game in a black border.   It appears that the game isn't being scaled to fit the screen.  

My specs:
Dell Inspiron 9300
Nvidia Geforce 2go 6800 (nvidia-glx installed)
Pentium M 1.6
Screen Resolution 1920x1200


Note:  I didn't have this issue with Ubuntu 5.10.

Thanks in advance


EDIT:

Games that I have tested this with:  Armagetron, Planet Penguin Racer, SuperTux

Here's my xorg.conf file:

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
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
	Option		"Protocol"		"ExplorerPS/2"
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
	Option		"LeftEdge" 		"80"
	Option 		"RightEdge" 		"920"
	Option 		"TopEdge" 		"80"
	Option 		"BottomEdge" 		"690"
	Option 		"FingerLow" 		"14"
	Option 		"FingerHigh" 		"15"
	Option 		"MaxTapTime" 		"180"
	Option 		"MaxTapMove" 		"110"
	Option 		"ClickTime" 		"0"
	Option 		"EmulateMidButtonTime"	"75"
	Option 		"VertScrollDelta" 	"10"
	Option 		"HorizScrollDelta" 	"0"
	Option 		"MinSpeed" 		"0.45"
	Option 		"MaxSpeed" 		"0.75"
	Option 		"AccelFactor" 		"0.020"
	Option 		"EdgeMotionMinSpeed" 	"200"
	Option 		"EdgeMotionMaxSpeed" 	"200"
	Option 		"UpDownScrolling" 	"1"
	Option 		"CircularScrolling" 	"0"
	Option 		"CircScrollDelta" 	"0.1"
	Option 		"CircScrollTrigger" 	"2"
	Option 		"SHMConfig" 		"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV41.8 [GeForce Go 6800]"
	Driver		"nvidia"
	Option          "NvAGP"       "1"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-96
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV41.8 [GeForce Go 6800]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection
```

---

### Post by barakaspeed on 2006-06-11
bumpy?  anyone?

---

### Post by ZylGadis on 2006-06-11
Some games cannot change the xorg resolution. And even if they can, you have not given them the option to - your xorg only has 1900x1200. Therefore, any game that does not support 1900x1200 will do its best to run fullscreen in that resolution, resulting in its filling only the center part of the screen.

---

### Post by barakaspeed on 2006-06-11
Wow, can't believe I missed that. :oops: That's definitely what it is.  Thanks ZylGadis.

---

### Post by benplaut on 2006-06-12
i have a laptop and a external moniter.

Laptop on its own = it works
With monitor = not scaled

luckily, i don't care :P

---

