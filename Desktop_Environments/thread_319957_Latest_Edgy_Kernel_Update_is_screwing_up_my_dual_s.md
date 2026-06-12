---
title: "Latest Edgy Kernel Update is screwing up my dual screen xorg.conf"
date: 2006-12-16
forum: Desktop Environments
---

### Post by Karbonik on 2006-12-16
Alright really, I'm getting tired of playing with my xorg.conf.

I had it nicely set up, working with the 915 resolution fix, dual screen in edgy, and suddenly with the latest (kernel? KDE?) update my xorg.conf file is now loading a KDE that cuts off most of my primary screen, giving me only about 2 inches of space on the left side of the laptop screen in which the main toolbar recognizes as actual space.

Programs open normally, but it is really annoying
 eg: this post is being done with Swiftfox, which is using the whole laptop screen

but for the toolbar, and the background of my laptop screen, it is not functioning.

Oh, and for some as yet unknown reason, it won't load the SDP server for my Bluetooth Device either. (not as big an issue for me)  but it works fine with a fresh (or reconfigured) xorg.conf

Here is the offending xorg.conf, which worked fine before the update.

Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection


(Skipping extraneous stuff here)



Section "Device"
    Identifier    "Intel Corporation Mobile Integrated Graphics Controller"
    Driver        "i810"
    BusID        "PCI:0:2:0"
##################New Add###############
    Screen 0
    Option "MonitorLayout" "CRT,LFP"
    Option "DevicePresence" "true"
########################################
EndSection

###########
Section "Device"
    Identifier "Device1"
    Driver "i810"
    BusID "PCI:0:2:0"
    Screen 1
    Option "MonitorLayout" "CRT,LFP"
    Option "DevicePresence" "true"
EndSection
###########



Section "Monitor"
#    Identifier    "Generic Monitor"
    Identifier    "Laptop Monitor"
    Option        "DPMS"
EndSection

#################
Section "Monitor"
    Identifier    "External Monitor Crystalscan"
    ModelName      "Gateway CrystalScan 500"
    HorizSync       30.0 - 64.0
    VertRefresh     50.0 - 100.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
    ModeLine       "1152x768@54" 65.0 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
    ModeLine       "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync

    Option        "DPMS"
EndSection
#################


Section "Screen"
#    Identifier    "Default Screen"
    Identifier    "Laptop Screen"
    Device        "Intel Corporation Mobile Integrated Graphics Controller"
#    Monitor        "Generic Monitor"
    Monitor        "Laptop Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x800"
    EndSubSection
EndSection

#################
Section "Screen"
    Identifier "Secondary Screen"
    Device "Device1"
    Monitor "External Monitor Crystalscan"
    DefaultDepth 24
    SubSection "Display"
        Depth 1
        Modes "1024x768"
    EndSubSection
    SubSection "Display"
        Depth 4
        Modes "1024x768"
    EndSubSection
    SubSection "Display"
        Depth 8
        Modes "1024x768"
    EndSubSection
    SubSection "Display"
        Depth 16
        Modes "1024x768"
    EndSubSection
    SubSection "Display"
        Depth 24
        Modes "1024x768"
Modes      "800x600@60" "832x624@75" "800x600@85" "1024x768@75" "800x600@75" "1024x768@70" "800x600@72" "1024x768@60" "800x600@56" "1024x768@43" "640x480@85" "1152x768@54" "640x480@75" "1280x854" "640x480@72" "1280x960@60" #"640x480@60" "1280x1024@60"
    EndSubSection
EndSection
#################

#################
Section "ServerLayout"
    Identifier "Dual-monitor Layout"
    Screen 0 "Laptop Screen" 0 0
    Screen 1 "Secondary Screen" LeftOf "Laptop Screen"
# Option "Clone" "On"
    Option "Xinerama" "On"
    InputDevice "Generic Keyboard"
    InputDevice "Configured Mouse"
#    InputDevice "Synaptics Touchpad"
EndSection
#################

Section "DRI"
    Mode    0666
EndSection

---

