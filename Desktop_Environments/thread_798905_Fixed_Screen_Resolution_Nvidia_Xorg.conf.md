---
title: "Fixed Screen Resolution Nvidia Xorg.conf"
date: 2008-05-18
forum: Desktop Environments
---

### Post by Amerinidiot1231 on 2008-05-18
Hey! I finally edited to make a working xorg.conf file that seems to fix my minimal screen resolution problem in Heron.  I can choose a multitude of resolutions now.

Most of the code came from a xorg.conf file generated from 'nvidia-settings'

A few notes:
I have downloaded the 'nvidia-settings' package from synaptic package manager
I am using 'extra visual effects'.  If you do not use this setting and want to try my xorg.conf file I believe you would remove the line 'Option         "AddARGBGLXVisuals"	"True"'
If you have the extra visual effects and do not have that line, you will have to title bars when you next boot up.

Here is my Xorg.conf file, I hope it helps

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
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
    Driver         "keyboard"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    Option         "AddARGBGLXVisuals"	"True"
EndSection

---

