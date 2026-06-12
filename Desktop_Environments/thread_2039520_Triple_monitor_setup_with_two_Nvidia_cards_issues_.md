---
title: "Triple monitor setup with two Nvidia cards: issues with twinview"
date: 2012-08-09
forum: Desktop Environments
---

### Post by nmr300 on 2012-08-09
Good morning! 
I recently acquired an old HP XW workstation with a Nvidia NVS290, that ran smoothly with two monitors until yesterday. 
Since I use the machine mainly for writing (scientific papers, typically need LaTeX, gnuplot, Matlab etc. at the same time), I thought a third monitor would be nice. So I got myself a second NVS290 and attached three TFTs in portrait mode - that's when the trouble started. :confused:

I'm aware that this has been discussed at length in this and other forums. The best (i.e. only) solution to my knowledge is to use two monitors in twinview (on one card) and the third as separate X-screen, that is joined via Xinerama:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
EndSection

Section "Files"
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
    ModelName      "DELL 2007FP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL 2007FP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 290"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 290"
    BusID          "PCI:8:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option "RandRRotation" "yes"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +0+1200"
    Option         "TwinViewXineramaInfoOverride" "1200x1600+0+0, 1200x1600+1200+0, 1200x1600+2400+0"
Option "Rotate" "CCW"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
Option "Rotate" "CCW"
Option "RandRRotation" "yes"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

XFCE (xubuntu 12.04) however has some problems with this setup:
the "Display" dialog in the settings does no longer work ("could not determine version of RandR extension") and worse: the twinview monitors now behave like one big screen. Windows maximize to both displays and dialog boxes open in between the two displays (including login). 
Is there any way to fix the last issue? I mean other than buying an ATI card... :mad:

---

### Post by nmr300 on 2012-08-15
I gave up and got myself a cheap Radeon HD 6450: all three DVI monitors in portrait mode working straight out-of-the-box with the fglrx driver from the repositories. One large desktop, window behavior as anticipated. 

Cheers!

---

