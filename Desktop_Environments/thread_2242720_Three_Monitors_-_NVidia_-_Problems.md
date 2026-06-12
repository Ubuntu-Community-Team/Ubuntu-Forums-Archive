---
title: "Three Monitors - NVidia - Problems"
date: 2014-09-03
forum: Desktop Environments
---

### Post by Bryan76 on 2014-09-03
I have three monitors.  Two connected to one NVidia Quadro FX 580, and a third connected to another Quadro FX 580.

I am using the latest nvidia drivers 340.32.  Ubuntu 14.04

To expand one single desktop across all three monitors, the only way I got that to work was to use one X screen on the first two monitors, one X screen on the third monitor, and use Xinerama to expand the desktop.  However, when I did this, the interface would behave very slowly.  Especially when doing anything that involved transparencies.  Such as the "ubuntu button" in the main menu.

So I turn off Xinerama.  Now the first two monitors are still on one X screen, and they behave much better.  The third monitors--another X screen--I can cursor over to it, but there is no user interface.  No Unity or winodw manager.  And the cursor changes to the old "X" cursor.  Also, I obviously can't drag any windows over there.

Any thoughts on how to get the three monitors working with decent performance?


```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" 3360 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL E228WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection


Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL P2210"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 580"
    BusID          "PCI:3:0:0"
EndSection


Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 580"
    BusID          "PCI:4:0:0"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 580"
    BusID          "PCI:4:0:0"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "DP-0: nvidia-auto-select +0+0, DP-1: nvidia-auto-select +1680+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection





```

---

