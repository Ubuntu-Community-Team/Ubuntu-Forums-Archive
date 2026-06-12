---
title: "Change default screen in dual head (twinview)"
date: 2008-02-29
forum: Desktop Environments
---

### Post by lffcruz on 2008-02-29
Hi there,

I hope that someone can help me with something I've been trying to do...
I managed to configure twinview for dualhead in order to get the desktop effects working.
I used to have it configured with "System->Screens and Graphics" and it was ok, but no desktop effects were working.

At this point, the dual head is ok with effects, but the main screen is not the one i want...

I'm running 7.10 on a DELL D620 (nvidia Quadro NVS 110M)...
See more details bellow in my Xlog and xorg.conf.
the problem is that the external screen is being used as the main screen and i want it to be on the LCD screen...

Can someone give me a hand?

Many thanks...

Best regards

Luis



My X log:
(--) NVIDIA(0): Connected display device(s) on Quadro NVS 110M at PCI:1:0:0:
(--) NVIDIA(0):     HP L1706 (CRT-0)
(--) NVIDIA(0):     AUO (DFP-0)
(--) NVIDIA(0): HP L1706 (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): AUO (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): AUO (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Display Devices found referenced in MetaMode: CRT-0, DFP-0
(II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "DFP-0:1440x900_60+0+0,CRT-0:1280x1024+1440+0"
(II) NVIDIA(0): Virtual screen size determined to be 2720 x 1024
(--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.

My xorg.conf:

### CARD ###################################################################

Section "Device"
    Identifier   "Videocard0"
    Driver       "nvidia"
    VendorName   "NVIDIA Corporation"
    BoardName    "Quadro NVS 110M"
EndSection

### MONITORS ###############################################################

#Section "Monitor"
#       Identifier       "Monitor0"
#       Modelname        "D620 LCD"
#    modeline     "1440x900@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
#       Gamma   1.0
#EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Unknown"
    ModelName    "HP L1706"
    HorizSync    30.0 - 83.0
    VertRefresh  50.0 - 76.0
    Option       "DPMS"
EndSection

### SCREENS  ###############################################################

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewOrientation" "CRT-0 RightOf DFP-0"
    Option         "metamodes" "DFP-0: 1440x900_60 +0+0,CRT-0: 1280x1024 +1440+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


### SERVER  ################################################################

Section "ServerLayout"
    Identifier     "Layout0"
    Screen         "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

### MODULES  ###############################################################

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
    Load           "v4l"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

---

### Post by chewearn on 2008-02-29
I think in the Section "Device", you need this:

```
Option "TwinViewXineramaInfoOrder" "DFP-0, CRT-0"
Option "UseDisplayDevice" "DFP-0, CRT-0"
Option "TwinViewOrientation" "DFP-0 LeftOf CRT-0"
```

Also, comment out the "TwinViewOrientation" line in Section "Screen".

---

### Post by lffcruz on 2008-02-29
It wors!!!!

many thanks for your help :)

regards

Luis

---

