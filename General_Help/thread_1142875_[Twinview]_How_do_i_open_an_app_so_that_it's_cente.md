---
title: "[Twinview] How do i open an app so that it's centered in the main screen on launch?"
date: 2009-04-29
forum: General Help
---

### Post by Kale Kold on 2009-04-29
How do i open an application so that it's centered in the main screen on launch?

At the minute i open an application such as Firefox and it will open in the bottom right corner. Any fixes for this behavior?

Specs:
Jaunty
Nvidia 180.53 driver
Twinview

xorg.conf:
> 
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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
    ModelName      "HIQ L90D+ DVI"
    HorizSync       31.0 - 67.0
    VertRefresh     59.0 - 61.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTX"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


---

### Post by regor210 on 2009-04-29
Assuming your using Nvidia property drivers.

I use sysinfo
sudo apt-get install sysinfo

Use NVIDIA Display Settings. When you find something that works the way you like you can use.

sudo sysinfo

as root, to save and lock in your settings.

---

### Post by Kale Kold on 2009-04-29
> **regor210 said:**
> sudo sysinfo
as root, to save and lock in your settings.
How? All it does is save a file.

---

### Post by regor210 on 2009-04-29
goto Application>Accessories>Terminal  
type
sudo sysinfo

NVIDIA>NVIDIA Display Settings
In (X Server Display Configuration) setup your system they way you want then click on (Save  to X Configuration File) 

Make wise choices as you are in root and the way you save it will be the way it will stay until you change it.

---

### Post by Kale Kold on 2009-04-29
Yes, i've already done all that and i am happy with how my displays are setup.

The problem is that when i open an app such as firefox it defaults to either the bottom right of the main screen or the top left. It doesn't seem to save any location data when i close the app. Any way around this?

---

