---
title: "[SOLVED] Dual Head on Nvidia 7600GS"
date: 2009-01-03
forum: General Help
---

### Post by scott_g on 2009-01-03
Hi,

I'm trying to set up a dual-head on an Nvidia 7600GS card (as the title implies), and have been trying for a while, with no avail.  I'm posting here to see if I'm missing something....  My monitor setup is as follows:

Primary monitor:
Samsung 2243wm 22" 1680x1050

Secondary monitor:
Xplio No-name 19" 1280x1024

Both are LCD, and the Samsung is attached the the DVI port of the graphics card, while the Xplio is on the analogue connection.

Here is my xorg.conf file:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
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
    Option         "Xinerama" "0"
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
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor1"
    VendorName     "Xplio"
    ModelName      "CRT-1"
    HorizSync       31.5 - 64.0
    VertRefresh     56.0 - 65.0
    Modeline 	   "1280x1024@60"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
    #ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Modeline "1680x1050@60"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1280x1024@60 +0+0; CRT: 1280x960@60 +0+0; CRT: 1024x768@60 +0+0; CRT: 800x600@60 +0+0; CRT: 800x600@56 +0+0; CRT: 640x480@60 +0+0"
    SubSection     "Display"
        Depth       24
	Modes "1280x1024@60"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1680x1050@60 +0+0"
    SubSection     "Display"
        Depth       24
	Modes "1680x1050@60"
    EndSubSection
EndSection

```

Note: This gives a resolution of 1024x768 on the Xplio, and 1280x1024 on the Samsung.  If I change the resolution using the nvidia-settings tool, I achieve the desired resolutions, but can't seem to save it to a conf file (seg-fault's).

Does anyone see something I've missed?

Thanks a lot,
Scott

---

### Post by IllegalCharacter on 2009-01-03
Are you running Compiz Fusion?

Have you tried reinstalling the NVidia drivers?

---

### Post by scott_g on 2009-01-04
I am running Compiz Fusion, and I haven't tried re-installing the Nvidia drivers, but they worked for the last year or two on the Xplio (just got the Samsung), so I figured they'd be ok...  

Also, I got nvidia-settings to save to the conf file, but the new conf file didn't seem to help.  

Thank you very much; any other ideas?

Thanks,
Scott

---

### Post by scott_g on 2009-01-04
After playing around with the config file, I finally got this figured out.  I've posted the relevant portions of my xorg-config file below.  I ended up using Twinview; it seemed easier to set up.

```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       31.5-64.0
    VertRefresh     56.0 - 65.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 1280x1024 +0+0, DFP: 1680x1050 +1280+0; CRT: NULL, DFP: 1680x1050_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Thanks,
Scott

---

