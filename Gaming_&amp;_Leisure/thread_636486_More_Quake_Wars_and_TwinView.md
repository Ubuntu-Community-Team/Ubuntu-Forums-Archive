---
title: "More Quake Wars and TwinView"
date: 2007-12-09
forum: Gaming &amp; Leisure
---

### Post by Sicundercover on 2007-12-09
Sorry for the poor title I mis typed. If I knew how to change the title I would.

Ive got Quake Wars running but there are a few problems.

Im running TwinView and the game opens across both screens.

Also, I have a plantronics USB head set. I need to figure out how to get it working for In Game VOIP.

---

### Post by badrunner on 2007-12-10
With regards to twinview, there a known bugs with certain twinview setups that me and others have reported to nvidia without any hope of a fix for years now, just search the nv news forums for "twinview fullscreen games". Some setups work ok most of the time though.

To get games running on just one screen, you need meta modes for "nvidia-auto-select, NULL" and more if you want to run in lower resolutions.

Also, you really need to switch compiz off if you are using that (desktop effects), its currently a very poor window manager when using twinview and regularly changing screen resolutions etc.

---

### Post by Sicundercover on 2007-12-10
Yea I noticed the Compiz issues. But one of the big things I was noticing for the Null option settings is this: Im using Xinerama and it seems that the Null script is written to go into the places that they would go into for normal TwinView. 

I dont even know if Im making sense but heres my xorg.

```
Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "altwin:meta_win"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    VendorName     "Samsung"
    ModelName      "Samsung SyncMaster 225BW (Digital)"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Gamma           1
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x800@75" 107.2 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
    ModeLine       "1280x768@75" 103.0 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    ModeLine       "1440x900@75" 136.5 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
    ModeLine       "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
    ModeLine       "1600x1024@60" 136.4 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
    ModeLine       "1680x1050@60" 147.1 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1920x1200@60" 193.2 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8800 GTX]"
	Driver		"nvidia"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Screen          0

EndSection

Section "Device"
    Identifier     "Videocard0"
	Driver		"nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTX"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8800 GTX]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1920 1200
        Depth       24
        Modes      "1600x1024@60" "1680x1050@60" "1440x900@60" "1920x1200@60" "1440x900@75" "1280x800@60" "1280x768@75" "1280x800@75" "1280x720@60" "1280x768@60" "800x600@60" "800x600@75" "800x600@72" "800x600@56"
    EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
Option "TwinViewXineramaInfoOrder" "DFP, CRT"
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: NULL, DFP: 1600x1024@60 +0+0; CRT: 1280x1024_75 +1680+0, DFP: 1680x1050 +0+0; CRT: NULL, DFP: 1440x900@75 +0+0; CRT: NULL, DFP: 1280x800@60 +0+0; CRT: NULL, DFP: 1280x768@75 +0+0; CRT: NULL, DFP: 1280x800@75 +0+0; CRT: NULL, DFP: 1280x720@60 +0+0; CRT: NULL, DFP: 1280x768@60 +0+0; CRT: NULL, DFP: 800x600@60 +0+0; CRT: NULL, DFP: 800x600@75 +0+0; CRT: NULL, DFP: 800x600@72 +0+0; CRT: NULL, DFP: 800x600@56 +0+0"
	Option		"AddARGBGLXVisuals"	"True"
EndSection



Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

---

