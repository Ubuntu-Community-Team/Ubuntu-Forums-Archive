---
title: "Two X sessions on separate monitors"
date: 2015-10-07
forum: Desktop Environments
---

### Post by UncleBoarder on 2015-10-07
This worked on my existing hardware until my HD crash and now I can't rembmer how I did it...

I have 3 monitors and 2 graphics cards. I want one X session on 1 graphics card (2 monitors)... this part is working.

And I want a second X sesson on the 2nd graphics card (1 monitor)... The screen is up but black, just a mouse "X" cursor, no actual X session.

I can start a second X session with "startx -- :1" But then it's married to F8, I want it active on the second video card.

I'm thinking it's something I need to configure in xorg.conf but I don't know what... I need help please.

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
#    Screen      1  "Screen1" Relative "Screen0" 1920 0
#    Screen      2  "Screen2" RightOf "Screen1"
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

#####################################################

Section "Monitor"
    Identifier     "Dell2407"
    VendorName     "Unknown"
    ModelName      "DELL 2407WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

#####################################################

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330"
    BusID          "PCI:2:0:0"
    Screen          0
    Option         "UseDisplayDevice"    "DFP-1"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330"
    BusID          "PCI:1:0:0"
    Screen          1
    Option         "UseDisplayDevice"    "DFP-1"
EndSection

#####################################################

Section "Screen"

# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1920+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Dell2407"
    DefaultDepth    24
     Option         "metamodes" "DFP-0: nvidia-auto-select +1920+0, DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "3840x1200"
    EndSubSection
EndSection

Section "Screen"

    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Dell2407"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Dell2407"
    DefaultDepth    24
    Subsection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by UncleBoarder on 2015-10-15
More info... This is really strange.  I've installed XScreenSaver 5.15 on my system and even though I only have an Xsession on 2 of my 3 screens... the screen saver works on ALL THREE SCREENS!

How is this possible that I can't get my second X session to display on my 3rd monitor but the screen saver displays there without problem???

I'm adding this info in hope that someone can offer insight to the original problem... I can't get my second X session to display on my 3rd monitor.

Still need help.

---

### Post by UncleBoarder on 2015-10-29
<bump>

---

