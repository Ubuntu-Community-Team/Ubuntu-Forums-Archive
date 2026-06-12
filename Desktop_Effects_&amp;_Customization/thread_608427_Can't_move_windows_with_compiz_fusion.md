---
title: "Can't move windows with compiz fusion"
date: 2007-11-10
forum: Desktop Effects &amp; Customization
---

### Post by geekphreak on 2007-11-10
I have Xpress 200m with 8.42 driver on Gutsy x86. When compiz fusion is active, I can't move windows, or resize them. Also, all newly opened windows appear to have no titlebar. 
Here is my xorg.conf: ```

Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "ATI Technologies Inc Radeon XPRESS 200M"
    Driver        "fglrx"
    BusID        "PCI:1:5:0"
    VideoRam    128000
    Option        "UseFBDev"        "true"
    Option        "NoLogo"    "true"
    Option        "AllowGLXWithComposite"    "true"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    28-64
    VertRefresh    43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc Radeon XPRESS 200M"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option        "AddARGBVisuals"    "true"
    Option        "AddARGBGLXVisuals"    "true"
    Option        "RenderAccel"        "true"
    SubSection "Display"
        Modes        "1280x800"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"

# Uncomment if you have a wacom tablet
#    InputDevice     "stylus"    "SendCoreEvents"
#    InputDevice     "cursor"    "SendCoreEvents"
#    InputDevice     "eraser"    "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Extensions"
    Option        "Composite"    "1"
EndSection

```I have read a lot of posts, but nothing I tried so far worked, 
Any ideas? Thanks!

***  EDIT ***

RESOLVED: I seemed to have conflicting compiz packages.

---

### Post by craigor on 2008-01-17
do you remember which packages specifically? i'm having that problem right now, albeit in plain debian, but this is the only spot i found the same thing happening on the internet, so any advice would help. 

it's so frustrating! i can minimize, resize, alt-tab... just not move the windows.

---

