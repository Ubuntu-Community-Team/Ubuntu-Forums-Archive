---
title: "Multiple display - Not correct default screen"
date: 2008-08-09
forum: Desktop Environments
---

### Post by 4t0m1c_w07f on 2008-08-09
Hi, I got the nvidia-settings installed and configured my two monitors but now the default screen is the wrong one. I have 2 monitors: Samsung Syncmaster 940bf and an LG 710S. The syncmaster is on the right and the LG is on the left. Whatever I try, the LG still remains the default. Here is a copy of my xorg.conf:
```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG 710S"
    HorizSync       30.0 - 71.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT-0: 1280x1024 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: 1280x1024_60 +0+0"
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT-1: nvidia-auto-select +0+0"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-1: 1280x1024_75 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

I would like to have the syncmaster as my default.

Thanks in advance.

---

### Post by dlodge on 2009-08-30
I have the same problem on a HP DV3-1075 laptop. The default screen is always the screen on the left, but I want the default screen to be on the right.

The computer contains ATI Radeon HD 3200 graphics and I'm running proprietary ATI drivers, version 9.8.

I suspect this is an issue with the implementation of multiple monitors rather than with the individual configurations. Any thoughts?

---

### Post by nistrum on 2009-10-11
dlodge: I managed to get screens to swap with fglrx. Presuming you don't use Randr for anything disable it using the instructions on this page:

[http://ubuntuforums.org/showthread.php?t=1137576](http://ubuntuforums.org/showthread.php?t=1137576)

Then add: 'Option "SwapScreens" "On"' to the device section of your xorg.conf. Randr seems to stop this driver feature from working hence the steps to disable it. After doing this gnome-display-properties won't work and you'll need to use amdcccle instead.

Don't know about nvidia though, sorry.

--Matt

---

