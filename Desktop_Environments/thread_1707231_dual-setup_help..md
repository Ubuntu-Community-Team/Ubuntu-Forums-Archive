---
title: "dual-setup help."
date: 2011-03-15
forum: Desktop Environments
---

### Post by Tweisted on 2011-03-15
Hello everyone I was wondering if someone could give me a hand with this ongoing problem ive been having with dual monitors. Here is my setup

Im running 

Ubuntu 10.10 64bit
amd athlon X4 64bit
Ati radeon 57000

What im trying to setup is have 2 screens with there own desktop. Like you do on your main screen when installing Ubuntu, I want that same thing on my second desktop. So it would be 2 seperate desktops on 2 seperate monitors. Here is my xorg.conf file.

[http://pastebin.com/taB8aSMp](http://pastebin.com/taB8aSMp)

If someone could give me a helping hand I would very much appreciate it. Ive been having so much trouble trying to figure this out. Any help is much appreciated. Need any more information please let me know.

Thank you all very much!

---

### Post by Krytarik on 2011-03-15
If I understand you right, you want to set up separate xscreens, both screens will have their own panels and will have separate access to the (same) desktop, but you *can't move windows between them*. Is that correct?

If so, take the xorg.conf of my mom's machine as a reference:
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" 1152 0
EndSection

Section "Monitor"
    #DisplaySize      310   230    # mm
    Identifier   "Monitor0"
    VendorName   "SAM"
    ModelName    "SyncMaster"
    Modeline     "1152x864_85.00"  119.75  1152 1232 1352 1552  864 867 871 910 -hsync +vsync
    Option       "PreferredMode" "1152x864_85.00"
    HorizSync    30.0 - 85.0
    VertRefresh  50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"
    #DisplaySize      310   230    # mm
    Identifier   "Monitor1"
    VendorName   "LG"
    ModelName    "LG M2380D"
    Modeline     "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
    Modeline     "1920x1080_50.00"  141.50  1920 2032 2232 2544  1080 1083 1088 1114 -hsync +vsync
    Option       "PreferredMode" "1920x1080_50.00"
    HorizSync    30.0 - 83.0
    VertRefresh  56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "RV350 AR [Radeon 9600]"
    BusID       "PCI:1:0:0"
    Screen      0
EndSection

Section "Device"
    Identifier  "Card1"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "RV350 AR [Radeon 9600]"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    DefaultDepth    24
    SubSection "Display"
        Depth     24
        Modes   "1152x864" "1024x768"
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    DefaultDepth    24
    SubSection "Display"
        Depth     24
        Modes   "1920x1080" "1280x720"
    EndSubSection
EndSection

```

---

