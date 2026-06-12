---
title: "compiz nvidia dual screen does not render properly screen 1"
date: 2009-02-19
forum: Desktop Environments
---

### Post by gupi-gupi on 2009-02-19
Hy I've this trouble with dual monitor and separate x screens with compiz git & GeForce 6600, googled a lot but could not find the solution yet.
I run intrepid , monitor 1024x768 (screen 0) and a tv (screen1) 1360x768 (showing up on the left of default screen. The trouble is that compiz loads fine on screen0 but in tv one chunk of screen is missing, as if compiz keeps the same resolution (1024x768) also on the tv (screen 1). 
Now same compiz git in debian sid displays fine in both monitor, but in intrepid no way I could gat it to work. (tried different version of compiz in intrepid, and xorg.conf from sid but still same result :(  here is xorg.conf from intrepid:```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 1360 0
    Screen      1  "Screen1" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
# Removed Option "Xinerama" "1"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "it"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "SAMSUNG"
    HorizSync       30.0 - 61.0
    VertRefresh     60.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony SDM-HS74P"
    HorizSync       28.0 - 65.0
    VertRefresh     57.0 - 63.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "DisableGLXRootClipping" "True"
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1360x768_60 +0+0; CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```
I also tied  different entry in ccsm >general option>display settings >output  (in sid I had two enties 640x480+0+0) don't work in 8.10

---

### Post by gupi-gupi on 2009-02-19
This is funny!!!!!! tried to solve this for two days, poste this thred cose just too frustrated and... a minute later as a very last try I removed the 177 driver and installed 173, and :D magic the tv screen just renders fine.

---

