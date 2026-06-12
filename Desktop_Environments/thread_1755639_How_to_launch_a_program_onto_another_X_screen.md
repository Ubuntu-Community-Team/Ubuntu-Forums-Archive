---
title: "How to launch a program onto another X screen?"
date: 2011-05-11
forum: Desktop Environments
---

### Post by skullmunky on 2011-05-11
This is for a live performance type of setup.  I have 2 graphics cards.  One is attached to 2 projectors, which are what the audience sees. The other has a single monitor, which is backstage.  The 'front' graphics card is configured in Twinview, and the 'backstage' one is configured as a second X screen by the nvidia settings control panel.  

What I'd like to do is launch my show program from a terminal on my backstage screen, but have it show up on the other X screen, the 'front' one.  X is amazing so I'm sure it can be done, but I'm having a hard time figuring out exactly how.  Thanks for any hints ... :)

--

Wow, Personal Best for self-solving my own thread question:

```

DISPLAY=:0.0; xclock

```

launches on display 0

```

DISPLAY=:0.1; xclock

```

launches on display 1

Additional notes to self:

1. stereo:

```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 1700"
    BusID          "PCI:2:0:0"
    Option "Stereo" "4"
EndSection

```

2. disable composite for stereo to work:

```

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

```

--

whole xorg:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
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
    ModelName      "Projectiondesign AS"
    HorizSync       30.0 - 140.0
    VertRefresh     48.0 - 110.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL 1905FP"
    HorizSync       0.0 - 0.0
    VertRefresh     0.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 1700"
    BusID          "PCI:2:0:0"
    Option "Stereo" "4"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 1700"
    BusID          "PCI:1:0:0"
EndSection

Section "Screen"

    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-au
to-select +0+0"
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
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

```

---

### Post by ManualSparrow on 2011-05-11
It might be easier to just enable Xinerama, which lets you drag windows across screens.

---

### Post by Tweak42 on 2011-05-11
Was replying to your question but realize you were using (2) separate video cards, not 1 card with several monitors.

This solution might work, it's what I use to auto place/size/position program windows onto my second monitor at launch; it saves having to drag them over manually and resize. 

[http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/](http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/)

---

### Post by skullmunky on 2011-05-14
Ooh, devilspie looks good.  Thanks.  

I thought about Xinerama but the thing is I'm using the two heads on one of the graphics cards in a twinview cloned-mode stereo configuration, so I don't know if that'll play nicely with xinerama.  if it does, that'd be cool, though.

---

