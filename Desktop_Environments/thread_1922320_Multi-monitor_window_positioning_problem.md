---
title: "Multi-monitor window positioning problem"
date: 2012-02-08
forum: Desktop Environments
---

### Post by kpostrup on 2012-02-08
Hi,

I'm using Gnome 3.2 (gnome-shell) on Ubuntu 11.10, with two displays.

I use my second display (tv) primarily for watching movies, and power it off when it's not needed.

I used the NVIDIA X Server Settings app to configure my dual monitor setup, where my computer screen is configured as the Primary X screen.

However, sometimes when I launch an application, the new window pops up on my tv monitor, which is pretty annoying, in case it's off, or I'm watching tv.

Is there any way to configure which monitor new windows should pop up on? :confused:

Thanks

Kenneth

---

### Post by kpostrup on 2012-02-08
I suspect this may be due to the twinview configuration?

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
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
    ModelName      "Philips FTV"
    HorizSync       15.0 - 70.0
    VertRefresh     48.0 - 62.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0, CRT: nvidia-auto-select +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

