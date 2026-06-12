---
title: "Problems Compiz-Fusion with NVIDIA drivers"
date: 2007-11-07
forum: Desktop Effects &amp; Customization
---

### Post by cavallopazzo on 2007-11-07
Hi guys. I read a lot in the net about many problems that I find with 
Ubuntu Gusty, NVIDIA 100.14.23 drivers (installed with Envy) and Compiz-Fusion.
My situation is that in my xorg.conf I have all right:

```
Section "ServerLayout"
	Identifier	"Default Layout"
        screen 0 "Default Screen" 0 0
	Option 		"AIGLX" "true"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"dbe"
	Load 		"dri"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1400x1050"
	Horizsync	31.5	-	65.5
	Vertrefresh	56.0	-	65.0
	Gamma	1
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV34M [GeForce FX Go5200 32M/64M]"
	Driver		"nvidia"
	Vendorname	"NVIDIA"
	Boardname	"NVIDIA GeForce FX (generic)"
	Screen	0
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
        Option 		"XAANoOffscreenPixmaps" "true"
	Option 		"TripleBuffer" "true"
	Option		"NoLogo"	"True"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34M [GeForce FX Go5200 32M/64M]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	Option		"RandRRotation"	"true"
	Option		"RenderAccel"	"True"
	Option		"AllowGLXWithComposite"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
	Option 		"RENDER" "true"
    	Option 		"DAMAGE" "true"

EndSection
```

The problem is that I can't start compiz because the terminal said me:

cavallopazzo86@cavallopazzo86-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0328 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1400x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 

But in the net I read that is not necessary have xserver-xgl package for Compiz-Fusion with NVIDIA Official Drivers. But now, I don't know what I can do for have my fantastic Desktop effects :(

What is the problem? How can I solve?

Thanks a lot

PS.: I don't install xserver-xgl because after I can't use nvidia-settings menu in X.

---

### Post by cavallopazzo on 2007-11-07
I've been solve after commenting the line about the memory usage in /usr/bin/compiz

```
#NVIDIA_MEMORY="65536" # 64MB
```

But now ... after some minutes of usage, all windows inside becomes black.

Now, someone can help me???

Thx

---

### Post by luisromangz on 2007-11-07
It is possible that your video card is not powerful enough to meet Compiz hardware requirements.

---

### Post by FuturePilot on 2007-11-07
Looks like you've encountered the black window bug.:(
You could try this workaround
```
compiz --replace --indirect-rendering --loose-binding
```

---

### Post by cavallopazzo on 2007-11-07
Thx so much Future ... I solved all my problems ...

I would say that if my card may not enouth for compiz-fusion I've not been here to ask problems about it ...

:confused:

---

