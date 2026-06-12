---
title: "something wrong with xorg.conf ??"
date: 2011-12-14
forum: Desktop Environments
---

### Post by Solutionz on 2011-12-14
I would like to start by thanking everyone in advance for any support. I have a rather interesting issue that i hope someone can solve. I have recently enabled nvidia restricted drivers (ubuntu 11.10 x64) and have lost seperate x view. when i checked xorg.conf i was shocked to find this is as the only entry:

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

The est of the file was blank. i started nvidia settings (sudo nvidia-settings) and enabled 2nd montior and set to seperate x view, went to apply settings but would not save?????? ok so i previewed the file it was trying to write and copied it myself to xorg.conf (via sudo nautilus),xorg.conf file reads now as:


Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
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
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG Electronics L226WT"
    HorizSync       28.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "LG Electronics L226WT"
    HorizSync       28.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
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
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection



Now what has happened is the 2nd monitor boots to a blank white screen, i can move my mouse over there (mouse pointer turns to X) but its not part of my desktop meaning i cannot drag files or windows over. 

im not sure what other info you guys need, any help is most appreciated.

---

### Post by Solutionz on 2011-12-14
so, what ive done is go twin view instead of separate x. heh

---

