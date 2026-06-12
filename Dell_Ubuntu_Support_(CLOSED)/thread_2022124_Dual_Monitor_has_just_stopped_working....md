---
title: "Dual Monitor has just stopped working..."
date: 2012-07-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rekounas on 2012-07-10
No real explanation for it.  Thought it was the monitor itself but after swapping monitors, etc, seems like a driver issue.

Setup is
Ubuntu 10.04 (Linux-x86_64)
2 Dell U2412M Monitors
Nvidia Driver 302.17


Getting the following error while attempting to set the second monitor

Failed to set MetaMode (2) 'DFP-0: nvidia-auto-select @1920x1200 +1920+0, DFP-1: nvidia-auto-select @1920x1200 +0+0' (Mode 3840x1200, id: 51) on X screen 0

Would you like to remove this MetaMode?

I say Yes and then I get this:

Failed to set MetaMode (1) 'DFP-0: 1920x1200 @1920x1200 +1920+0, DFP-1: 1920x1200 @1920x1200 +0+0' (Mode 3840x1200, id: 52) on X screen 0.

Yes, I am running setting as root.  also changed the permissions on the file just in case.

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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL U2412M"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 61.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 295"
EndSection

Section "Screen"

# Removed Option "TwinView" "True"
# Removed Option "MetaModes" "nvidia-auto-select, nvidia-auto-select"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +1920+0, DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

