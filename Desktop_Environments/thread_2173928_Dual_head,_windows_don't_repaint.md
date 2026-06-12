---
title: "Dual head, windows don't repaint"
date: 2013-09-11
forum: Desktop Environments
---

### Post by skyglow on 2013-09-11
My videocard is an ATI 6850 latest experimental proprietary drivers are installed (13.8)
I have 2 monitor attached to it (HDMI, DVI to VGA)
My desktop manager is gnome

glxgears
20888 frames in 5.0 seconds = 4177.494 FPS
fgl_glxgears 
Using GLX_SGIX_pbuffer
6826 frames in 5.0 seconds = 1365.200 FPS

i have over 1000 fps even full screen on each 
When i place a window on the border of the 2 monitor it doesn't repaint as it should on the second. The right screen is repainted every 1-3 seconds.

this is my xorg.conf
```
Section "ServerLayout"    Identifier     "Dual Head Layout"
    Screen      0  "myhead0" 1920 0
    Screen      1  "myhead1" 0 0
EndSection


Section "Module"
#       Load  "dri"
#    Load  "dri2"
#    Load  "dbe"
#    Load  "extmod"
#    Load  "record"
#    Load  "glx"
EndSection


Section "Monitor"
    Identifier   "Iiyama"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1200"
    Option        "TargetRefresh" "60"
    Option      "Primary" "true"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection


Section "Monitor"
    Identifier   "microstar"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x1024"
    Option        "TargetRefresh" "60"
    Option        "Position" "1920 0"
    Option      "RightOf" "Iiyama"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection


Section "Device"
    Identifier  "Radeon6850-0"
    Driver      "fglrx"
    Option        "Monitor-CRT1" "microstar"
    BusID       "PCI:1:0:0"
#    Screen      0
EndSection


Section "Device"
    Identifier  "Radeon6850-1"
    Driver      "fglrx"
    Option        "Monitor-DFP5" "Iiyama"
    BusID       "PCI:1:0:0"
#    Screen      1
EndSection


Section "Screen"
    Identifier "myhead0"
    Device     "Radeon6850-0"
    Monitor    "microstar"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
            Modes     "1920x1200"
#        Virtual    3120 1200
    EndSubSection
EndSection


Section "Screen"
    Identifier "myhead1"
    Device     "Radeon6850-1"
    Monitor    "Iiyama"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes     "1280x1024"
#        Virtual    3120 1200
    EndSubSection
EndSection



```
I forgot to mention it was working before last wipe but i can't find its xorg.conf anymore.
Thanks for your replies

PS
Screenshots capture the right image that should be seen.
I can see the mouse moving but i can't see the window while dragging it

---

### Post by skyglow on 2013-09-22
downgrading driver version fixes the problem
marking as solved

---

