---
title: "Ubuntu 7.10 is AMAZING!!!"
date: 2007-10-23
forum: Desktop Environments
---

### Post by nami on 2007-10-23
I installed it and it asked me to install the nvidia drivers which I did.  I then went into the display settings and enabled twinview.  it worked perfectly without having to edit any config files!!!

Very impressive as that was quicker than it would take to install the drivers and enable twinview in windows xp!!!

However!

I can't enable desktop effects while twinview is enabled.  The screen just flickers and then it says that it cannot enable desktop effects.  I have an nvidia geforce 6500 with 512mb ram.

Can someone please help?

---

### Post by davbren on 2007-10-23
I agree! Gutsy is amazing! There is so much more to it than the desktop efects. I would easily choose this as my OS of choice. I'm getting a new laptop soon so when that happens, away with windows!! WOO Kudos to Ubuntu!

---

### Post by nami on 2007-10-26
So is the following bug fixable?

> I can't enable desktop effects while twinview is enabled. The screen just flickers and then it says that it cannot enable desktop effects. I have an nvidia geforce 6500 with 512mb ram.

---

### Post by davbren on 2007-10-26
I should imagine so... Do you have the Nvidia tool for changing graphics settings. I have the "go" version of the same card. I'll have a look when I get home from work.

---

### Post by nami on 2007-10-26
I'm assuming you mean "nvidia-settings"?  If yes, then no.  For some reason, if I install that, it ruins my graphics and twinview config.  That is, it reverts back to 640x480 on both screens and instead of displaying a big twinview desktop, it shows s mirror image of 1 desktop on both screens...

So this time, I did not install it.

HELP...

---

### Post by Shimmy on 2007-10-26
I'm using 7.10, compiz-fusion and TwinView+Xinerama on nvidia, works like a charm.
However i did not set it up thru ubuntus screen-settings, i set it up manually on 7.04, and after upgrade it still works :)

---

### Post by nami on 2007-10-26
How would you set it up manually after a fresh install?

---

### Post by Shimmy on 2007-10-26
> **nami said:**
> How would you set it up manually after a fresh install?

Don't remember, but, my hottest tip is to look at my xorg.conf and find differencies that might make a change:
```

Section "ServerLayout"
    Identifier     "Layout0"
#    Screen      0  "Screen0" 0 0
    Screen      0  "Screen0" 0 0
    Screen	1 "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 1905FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection
Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL 1905FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 1400"
    Option            "RandRRotation" "yes"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 1400"
    Option            "RandRRotation" "yes"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: 1280x1024 +0+0, DFP-1: 1280x1024 +1280+0; DFP-0: 1024x768 +0+0; DFP-0: 800x600 +0+0; DFP-0: 640x480 +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: 1280x1024 +0+0, DFP-1: 1280x1024 +1280+0; DFP-0: 1024x768 +0+0; DFP-0: 800x600 +0+0; DFP-0: 640x480 +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

---

### Post by nami on 2007-10-26
thanks, i'll try that.

however, i've just noticed something strange.  the twinview looks fine as it with without compiz-fusion, however, when i take a screenshot, it only takes a screenshot of half the screen with the other screen just brown...

even if i have programs open on both monitors, the screenshot picks up the second monitor as blank in the screenshots...

something is not right and i feel this is a bug in 7.10.

---

### Post by Shimmy on 2007-10-26
> **nami said:**
> thanks, i'll try that.

however, i've just noticed something strange.  the twinview looks fine as it with without compiz-fusion, however, when i take a screenshot, it only takes a screenshot of half the screen with the other screen just brown...

even if i have programs open on both monitors, the screenshot picks up the second monitor as blank in the screenshots...

something is not right and i feel this is a bug in 7.10.

I think that you have to move your mouse to the screen you want to shot, or maby you need a focused window or so on the screen. I'm not sure thought. My screenshots works, it makes an image of both the screens.

Just try to enable Xinerama, i'm sure it will fix all your issues :)

---

### Post by nami on 2007-10-27
> **Shimmy said:**
> I think that you have to move your mouse to the screen you want to shot, or maby you need a focused window or so on the screen. I'm not sure thought. My screenshots works, it makes an image of both the screens.

Just try to enable Xinerama, i'm sure it will fix all your issues :)

but i never had to do that in 7.04...

i seem to have Xinerama enabled:

> # xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation GeForce 6500"
	Boardname	"nv"
	Busid		"PCI:5:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"AL1916"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation GeForce 6500"
	Monitor		"AL1916"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
  screen 1 "screen1" rightof "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"nv"
	Busid		"PCI:5:0:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
	Option		"Xinerama"	"true"
EndSection

---

