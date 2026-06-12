---
title: "Nvidia monitor rotation"
date: 2010-07-14
forum: Desktop Environments
---

### Post by fatalfurry on 2010-07-14
Is it possible to use the nvidia driver with Separate X screens and Xinerama? 

I would like to have one monitor normal and the other rotated 90 degrees.

---

### Post by fatalfurry on 2010-07-17
I have found a way to rotate one screen by entering

```


Section "Device"
   Option         "RandRRotation" "true"
   ....
EndSection

```

But this is only with Xinerama off and the settings do not save after a reboot.

---

### Post by schmolch on 2010-07-18
Example:
```

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:2:0:0"
Option "Rotate" "ccw"
Screen 0
EndSection


Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:2:0:0"
#Option "Rotate" "ccw"
Screen 1
EndSection
```

ccw means counterclockwise

---

### Post by fatalfurry on 2010-07-19
That did the trick. Now is there a way to align the two screens?

---

### Post by schmolch on 2010-07-19
> **fatalfurry said:**
> That did the trick. Now is there a way to align the two screens?

Here is my complete xorg.conf with 3 monitors next to each other:
```


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"

EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection


Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "NEC LCD2070NX"
    HorizSync       31.0 - 92.0
    VertRefresh     56.0 - 85.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "NEC LCD2070NX"
    HorizSync       31.0 - 92.0
    VertRefresh     56.0 - 85.0
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "NEC LCD2070NX"
    HorizSync       31.0 - 92.0
    VertRefresh     56.0 - 85.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7050 PV / nForce 630a"
    BusID          "PCI:0:18:0"
Option "Rotate" "ccw"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:2:0:0"
Option "Rotate" "ccw"
Screen 0
EndSection


Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:2:0:0"
Option "Rotate" "ccw"
Screen 1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
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
    Option         "metamodes" "DFP-0: nvidia-auto-select"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by fatalfurry on 2010-07-19
That did the trick. Thanks for the help.

---

