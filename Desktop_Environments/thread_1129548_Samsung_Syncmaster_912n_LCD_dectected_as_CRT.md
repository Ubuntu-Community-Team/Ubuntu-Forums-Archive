---
title: "Samsung Syncmaster 912n LCD dectected as CRT"
date: 2009-04-18
forum: Desktop Environments
---

### Post by bxcrx on 2009-04-18
Any takers?

**Tech Specs:**

Ubuntu 8.10 Intrepid Ibex
Monior: Samsung Syncmaster 912n
Monitor connection: VGA from Syncmaster to VGA to DVI adapter Nvidia 7600 GT
Current Monitor Sync: 60hz due to putting in: Option "DynamicTwinView" "False"

Video Card: NVidia 7600 GT XFT 
Nvidia Driver: 180.29

**Xorg Config:**



```


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
    VendorName     "Samsung"
    ModelName      "SyncMaster912N"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option "DynamicTwinView" "False"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

**Monitor Specs:**

```

       

General

    * Display Type LCD display / TFT active matrix
    * Width 16.4 in
    * Depth 7.5 in
    * Height 16.7 in
    * Weight 12.1 lbs
    * Enclosure Color Black

Image

    * Display (projector) image aspect ratio 5:4
    * Image brightness 260.0 cd/m2
    * Image Contrast Ratio 800:1
    * Max horizontal view angle 170
    * Max vertical view angle 170

Display

    * Diagonal Size 19.0 in
    * Viewable Size 19.0 in
    * Dot Pitch / Pixel Pitch 0.294 mm
    * Max Resolution 1280 x 1024
    * Color Support 24-bit (16.7 million colors)
    * Max Sync Rate (V x H) 75.0 Hz x 81.0 KHz
    * Video Bandwidth 140.0 MHz
    * Response Time 25.0 ms
    * Video Output None
    * Signal Input VGA
    * Features MagicTune , MagicBright

Video Input

    * Analog Video Signal RGB

Audio Output

    * Type None

Input Device

    * Input device type None

Expansion / Connectivity

    * Interfaces 1.0 x VGA - 15 pin HD D-Sub (HD-15)

Miscellaneous

    * Cables Included 1.0 x VGA cable
    * Flat Panel Mount Interface 100 x 100 mm
    * Features Wall mountable
    * Compliant Standards TCO '95 , DDC-2B

Power

    * Power device form factor Internal
    * Operational power consumption 38.0 Watt

Software / System Requirements

    * Software type MagicTune

```
Thanks

---

### Post by bxcrx on 2009-04-18
Mods please delete this post

---

