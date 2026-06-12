---
title: "Four heads + xrandr + compositing with nVidia Quadro NVS 420?"
date: 2011-09-22
forum: Desktop Environments
---

### Post by Kensey on 2011-09-22
So, I have a shiny new workstation with a Quadro NVs 420 card in it.  What I want is to have all four displays be aggregated into one large one, and have compositing on.

I installed the binary driver and let nvidia-settings generate a config file using Xinerama.  Of course with Xinerama on I can't run compiz.

If I turn off Xinerama and leave the rest of the file alone, I get four separate displays, each one with a menubar.

If I remove the file completely, I get just the far left-hand monitor with a menubar.

The head section of the nvidia-settings-generated file looks like:

```
Section "ServerLayout"

# Removed Option "Xinerama" "0"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen2"
    Screen      2  "Screen2" RightOf "Screen0"
    Screen      3  "Screen3" RightOf "Screen1"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
EndSection
```

(Yes, that's the correct screen layout order -- I hooked them up left-to-right 1, 2, 3, 4 according to the numbers on the four-head adapter, but they apparently interleave such that the logical screen order goes 0, 2, 1, 3).

Then there are four Monitor sections, one for each monitor.  Nothing unusual there.

It looks like the card itself has two outputs, each with two screens -- I have four Device sections like this:

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 420"
    BusID          "PCI:4:0:0"
    Screen          0
EndSection
```

...that increment the Identifier and alternate Screen 0 and 1 and BusID PCI:4:0:0 and PCI 5:0:0, but otherwise everything is the same.

Likewise I have four Screen sections like this:

```
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
```

that increment the Identifier, Device and Monitor, and alternate between DFP-0 and DFP-1, but are otherwise identical.

Somewhere I feel like this should be an easy fix, but I'm not sure what to remove/combine/change.

---

