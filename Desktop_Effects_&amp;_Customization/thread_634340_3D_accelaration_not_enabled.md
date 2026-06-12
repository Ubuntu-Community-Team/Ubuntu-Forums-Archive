---
title: "3D accelaration not enabled"
date: 2007-12-07
forum: Desktop Effects &amp; Customization
---

### Post by Zaff on 2007-12-07
Hi everyone.
I'm trying to enable 3D acceleration on my Macbook 2nd generation. The video driver is intel and here's what I get from lcpsi :
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 

```
and here is my xorg.conf :
```

Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "macintosh"
    Option        "XkbLayout"    "fr"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ImPS/2"
    Option        "ZAxisMapping"    "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SHMConfig"    "on"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "LeftEdge" "150"
Option "RightEdge" "1070"
Option "TopEdge" "100"
Option "BottomEdge" "310"
Option "FingerLow" "25"
Option "FingerHigh" "30"
Option "MaxTapTime" "180"
Option "MaxTapMove" "220"
Option "MaxDoubleTapTime" "180"
Option "HorizEdgeScroll" "0"
Option "VertEdgeScroll" "0"
Option "TapButton1" "0"
Option "TapButton2" "0"
Option "TapButton3" "0"
Option "LockedDrags" "off"
Option "VertScrollDelta" "20"
Option "HorizScrollDelta" "50"
Option "VertTwoFingerScroll" "1"
Option "HorizTwoFingerScroll" "1"
Option "MinSpeed" "1.10"
Option "MaxSpeed" "1.30"
Option "AccelFactor" "0.08"
Option "Emulate3Buttons" "true"
Option "SHMConfig" "on"
# corner buttons
Option "RTCornerButton" "0"
Option "RBCornerButton" "2"
Option "LTCornerButton" "0"
Option "LBCornerButton" "3"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "stylus"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "eraser"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "cursor"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
    Boardname    "Intel 945"
    Busid        "PCI:0:2:0"
    Driver        "intel"
    Screen    0
    Vendorname    "Intel"
    # ADD THIS IF YOUR LAPTOP DOES NOT HAVE A TV CONNECTOR or DOCKING STATION
        Option          "monitor-TV"   "TV"
    Option          "DRI"   "True"
EndSection

Section "Monitor"
    Identifier    "LCD"
    Vendorname    "APP"
    Modelname    "Builtin"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75 " 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75 " 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
    Gamma    1.0
EndSection
Section "Monitor"
    Identifier      "TV"
        Option          "Ignore" "True"
EndSection
Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
    Monitor        "LCD"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    2960    1850
        Modes        "1280x960@60"    "1280x1024@60"    "1280x1024@75"    " 1280x960@75"    "1152x864@75"    "1400x1050@60"    "1024x768@60"    "1400x1050@75"    "1024x768@70"    "1600x1200@65"    "1024x768@75"    "1600x1200@60 "    "832x624@75"    "1792x1344@60"    "800x600@60"    "800x600@75"    "800x600@72"    "800x600@56"    "640x480@75"    "640x480@72"    " 640x480@60"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen 0 "Default Screen" 0 0
    Inputdevice    "Generic Keyboard"
    Inputdevice    "Configured Mouse"
   
    # Uncomment if you have a wacom tablet
    #    InputDevice     "stylus"    "SendCoreEvents"
    #    InputDevice     "cursor"    "SendCoreEvents"
    #    InputDevice     "eraser"    "SendCoreEvents"
    Inputdevice    "Synaptics Touchpad"
EndSection
Section "Module"
    Load        "glx"
    Load        "GLcore"
    Load        "dri"
    Load        "v4l"
EndSection
Section "ServerFlags"
EndSection

```
So what am I missing here ?
if I do glxinfo I get direct rendering: No. I would like this t say yes obviously.
Also I use a dual screen setup from time to time, is it incompatible with 3d acceleration ?
Thanks for any help given.

---

### Post by smartboyathome on 2007-12-07
(btw, I have the same card you do, and I can get compiz working, so it isn't because it isn't compatible)

Try using the i810 driver instead of the intel driver (you will have problems with the intel driver and compiz). Change this section:
```
Section "Device"
    Identifier    "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
    Boardname    "Intel 945"
    Busid        "PCI:0:2:0"
    Driver        "intel"
    Screen    0
    Vendorname    "Intel"
    # ADD THIS IF YOUR LAPTOP DOES NOT HAVE A TV CONNECTOR or DOCKING STATION
        Option          "monitor-TV"   "TV"
    Option          "DRI"   "True"
EndSection
```

To this:
```
Section "Device"
    Identifier    "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
    Boardname    "Intel 945"
    Busid        "PCI:0:2:0"
    Driver        "i810"
    Screen    0
    Vendorname    "Intel"
    # ADD THIS IF YOUR LAPTOP DOES NOT HAVE A TV CONNECTOR or DOCKING STATION
        Option          "monitor-TV"   "TV"
    Option          "DRI"   "True"
EndSection
```

---

### Post by Zaff on 2007-12-07
> 
Try using the i810 driver instead of the intel driver (you will have problems with the intel driver and compiz).

thing is I think I was using that driver at first but then I started using xrandr for my dual screen setup and was told to switch to the intel one. Now I don't want to have to change the driver eveytime and if I can't use the dual screen then I'm just gonna stay like this for now. Can you tell me more about this ? I'm not exactly trying to run compiz (although that would be cool) just to be able to launch stuff like xmoto.

---

### Post by Zaff on 2007-12-08
anyone knows anything ?

---

