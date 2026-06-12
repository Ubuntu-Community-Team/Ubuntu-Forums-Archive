---
title: "Xorg completely ignores &quot;Option/Device&quot; lines from xorg.conf"
date: 2010-06-25
forum: Desktop Environments
---

### Post by DaftPunker on 2010-06-25
I'm using a fresh install of Ubuntu 9.10 x86 (I've just only made all of the updates). What I'm trying to do is a simple multiseat configuration (1 user per video card).

Graphics are working fine. My problem is quite weird: I can't make X to only accept input from a specif mouse/keyboard. So, if I move the mouse of seat1, the cursor will move for all the seats (and vice-versa).

Below, you can see the xorg.conf for 1 of the seats.
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/mouse1"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "Device" "/dev/input/event7"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 71.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nv"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    16
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024_60.00"
    EndSubSection
EndSection

```And yes, even if I launch only the above seat showed, the X server will accept input from any mouse/keyboard on the computer.

Anyone has any idea?
(sorry for my bad english)

---

