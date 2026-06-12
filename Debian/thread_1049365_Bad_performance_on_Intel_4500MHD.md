---
title: "Bad performance on Intel 4500MHD"
date: 2009-01-24
forum: Debian
---

### Post by MagiSu on 2009-01-24
You will be amazed by this glxgears data, with a Thinkpad T400 Intel Chipset.

297 frames in 5.0 seconds = 59.330 FPS
298 frames in 5.0 seconds = 59.545 FPS
299 frames in 5.0 seconds = 59.745 FPS
299 frames in 5.0 seconds = 59.745 FPS
299 frames in 5.0 seconds = 59.745 FPS

The performance is worse than my old Thinkpad R50. I cannot believe this! Here is my xorg.conf

Section "InputDevice"
Identifier    "Generic Keyboard"
Driver        "kbd"
Option        "XkbRules"    "xorg"
Option        "XkbModel"    "pc104"
Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
Identifier    "Configured Mouse"
Driver        "mouse"
Option        "SendCoreEvents"
Option        "Device" "/dev/input/mice"
Option        "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier     "Synaptics Touchpad"
Driver         "synaptics"
Option         "CorePointer"
Option         "Device" "/dev/psaux"
Option         "Protocol" "auto-dev"
Option       "Emulate3Buttons" "true"
Option         "HorizScrollDelta" "0"
Option       "Emulate3Buttons" "true"
Option       "LeftEdge" "1700"
Option       "RightEdge" "5300"
Option       "TopEdge" "1700"
Option       "BottomEdge" "4200"
Option       "FingerLow" "25"
Option       "FingerHigh" "30"
Option       "MaxTapTime" "180"
Option       "MaxTapMove" "220"
Option       "VertScrollDelta" "100"
Option       "MinSpeed" "0.06"
Option       "MaxSpeed" "0.10"
Option       "AccelFactor" "0.0010"
#Option       "SHMConfig" "1"
Option       "UpDownScrolling" "1"
Option       "CircularScrolling" "0"
Option       "LockedDrags" "0"
Option       "TouchpadOff" "0"
#Option       "Repeater" "/dev/ps2mouse"
EndSection

Section "Module"
Load  "dri"
Load  "extmod"
Load  "record"
Load  "dbe"
Load  "glx"
Load  "GLcore"
Load  "xtrap"
Load  "freetype"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Monitor"
Identifier    "Configured Monitor"
EndSection

Section "Monitor"
Identifier    "HDMI-1"
Option        "Ignore" "True"
EndSection

Section "Monitor"
Identifier    "HDMI-2"
Option        "Ignore" "True"
EndSection

Section "Device"
Identifier    "Intel Corporation Mobile Integrated Graphics Controller"
Driver        "intel"
Option        "monitor-HDMI-1" "HDMI-1"
Option        "monitor-HDMI-2" "HDMI-2"
Option        "AccelMethod"   "XAA"
Option        "FramebufferCompression"  "False"
EndSection

Section "Screen"
Identifier    "Default Screen"
Monitor        "Configured Monitor"
Device        "Configured Video Device"
DefaultDepth    24
SubSection "Display"
Modes    "1440x900"
EndSubSection
EndSection

Section "ServerLayout"
Identifier    "Default Layout"
Screen        "Default Screen"
InputDevice    "Synaptics Touchpad"
InputDevice    "Configured Mouse"
EndSection


Can anyone figure what happened? Thank you!

---

