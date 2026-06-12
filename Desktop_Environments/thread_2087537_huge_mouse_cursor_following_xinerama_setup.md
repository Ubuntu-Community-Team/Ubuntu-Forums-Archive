---
title: "huge mouse cursor following xinerama setup"
date: 2012-11-23
forum: Desktop Environments
---

### Post by teryret on 2012-11-23
Hello all, I just got a brandy new second monitor (it's huge :-D) and jumped through all the requisite hoops to get xorg.conf set up correctly.  As of now it's almost perfect, the only lingering issue is that my mouse cursor is suddenly huge (easily double the normal size in each dimension).

The crazy thing is that if I mouse over the top bar (when I'm using AwesomeWM) or the side bar (when I'm using Unity) it immediately shrinks back to the regular size, and then when I mouse out it gets huge again.  I'm at loss and Google doesn't seem to know what I'm talking about.

Here's my xorg.conf file:
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 1920 0
    Screen      1  "Screen1" 0 900
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL U2713HM"
    HorizSync       29.0 - 113.0
    VertRefresh     49.0 - 86.0
    Option         "DPMS"
    Option         "Rotate" "Left"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL2407WFPHC"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 520"
    Option         "RandRRotation" "on"
    BusID          "PCI:3:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 520"
    BusID          "PCI:3:0:0"
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
    Option         "metamodes" "DFP-1: 1920x1200 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Any ideas of things I can check?

---

### Post by teryret on 2012-11-23
Follow up.  I couldn't tell you why this worked, but what I ended up doing was going into dconf-editor to org->gnome->desktop->interface (which is where I had been trying to solve the problem by adjusting the cursor-size attribute) and changed the cursor-theme from DMZ-white to whiteglass.  I'm not sure exactly what that means, but it made my cursor reasonably sized... and black!?

---

