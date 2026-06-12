---
title: "Help with 4 monitor setup in gnome"
date: 2009-12-20
forum: Desktop Environments
---

### Post by Robstarusa on 2009-12-20
Hi all,

I have the following video cards connected to 4 monitors:

7800GT w/ 256M ram (2 DVI) works fine with nvidia drivers + Twinview
Matrox Millennium PCI with 4M ram, 1680x1050 single monitor
voodoo3 2000, not sure on ram (16?), 1680x1050 single monitor.

I have tried crafting an xorg.conf file, but if I use it I get 4 blank screens.  Any advice?

My monitor layout is like this:

[1920x1080/7800GT/DVI]  [1920x1080/7800GT/DVI] [1680x1050 - v3] [1680x1050 - matrox]

Are my driver names wrong?  How about my PCI device definitions in the xorg.conf file?

Output of lspci | grep VGA
```

rob2@rob-desktop-1:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)
06:01.0 VGA compatible controller: Matrox Graphics, Inc. MGA 2064W [Millennium] (rev 01)
06:02.0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo 3 (rev 01)

```

My xorg.conf:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sceptre X226W-1920"
    HorizSync       29.0 - 81.0
    VertRefresh     55.0 - 76.0
    Option         "DPMS"
EndSection

# http://usa.asus.com/product.aspx?P_ID=nDd2iW0CpEGYUWm1
Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Asus"
    ModelName      "VW192T+"
    HorizSync      31.0 - 80.0
    VertRefresh    56.0 - 75
EndSection

# http://usa.asus.com/product.aspx?P_ID=nDd2iW0CpEGYUWm1
Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Asus"
    ModelName      "VW192T+"
    HorizSync      31.0 - 80.0
    VertRefresh    56.0 - 75
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GT"
EndSection

# Vodoo 3
Section "Device"
    Identifier     "Device1"
    Driver         "tdfx"
    VendorName     "Bankrupt 3DFX"
    BoardName      "Voodoo3 2000"
    BusID          "PCI:6:2:0"
EndSection

# Matrox Millennium
Section "Device"
    Identifier     "Device2"
    Driver         "mga"
    VendorName     "Matrox"
    BoardName      "Millennium 4MB"
    BusID          "PCI:6:1:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-au
to-select +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier    "Screen1"
    Device	  "Device1"
    Monitor       "Monitor1"
    DefaultDepth  24
    Subsection    "Display"
        Depth      24
        Modes     "1680x1050"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "Screen2"
    Device	  "Device2"
    Monitor       "Monitor2"
    DefaultDepth  16
    Subsection    "Display"
        Depth     16
        Modes     "1680x1050"
    EndSubSection
EndSection

```

---

