---
title: "Dual monitors but the mouse is trapped in one (and wrong resolution)"
date: 2009-09-22
forum: Desktop Environments
---

### Post by PurposeOfReason on 2009-09-22
I'm back on arch for this one after a long gentoo break. When I was using it I had the following xorg.conf file and a nvidia 9600gt to power the monitors.
```

Section "ServerLayout"
    Identifier     "Dual Head Configuration"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" Relative "Screen0" 1050 630
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/mice"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "XkbLayout" "gb"
    Option         "XkbModel" "pc105"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 2209WA"
    HorizSync       30.0 - 83.0
    VertRefresh     60.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL 2209WA"
    HorizSync       30.0 - 83.0
    VertRefresh     60.0 - 60.0
    Option         "DPMS"
    Option         "RandRRotation" "on"
    Option         "Rotate" "CCW"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Screen          0
    Option "NoLogo" "True"
    Option "RenderAccle"    "True"
    Option  "TripleBuffer"  "True"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Screen          1
    Option "NoLogo" "True"
    Option "RenderAccle"    "True"
    Option  "TripleBuffer"  "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    Modes    "1680x1050"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    Modes    "1680x1050"
    EndSubSection
EndSection

```Now I have some board with integrated nvidia 7100 graphics that I know can do this dual monitor configuration, but it will not. It puts the left (rotated) monitor at a resolution of 1024*768 but does get it rotated. When it does this, I cannot get the mouse to leave that monitor though nvidia-settings does say it is on and working. Beyond that of having the wrong resolution it is identified as a CRT monitor and will not let me, manually or with the GUI, give it the proper resolution.

---

