---
title: "CUDA messed up my XFCE"
date: 2009-03-25
forum: Desktop Environments
---

### Post by omax on 2009-03-25
Hi there! I just tried to install the CUDA 180.22 driver on my xubuntu.

The installation went great an no changes were done to my xorg.conf (even though it was backed up and overwritten)

However, on reboot when it loaded X it couldn't find module "type1". I commented out that line, but I get the error (EE) No devices found

Nothing more.

So I tried to remove the old nvidia-glx driver (177.something) with apt-get.
Then I downloaded the latest driver directly from nvidias site (180.29)
But when I installed it found an old driver (180.22) which is the CUDA driver. So I guess there is no need to intall the other graphic driver.

however, when I start X now it can't find neither glx or the nvidia driver.

What should I do? I don't want to roll back to my old driver, because I really need the CUDA.

Here is my current xorg.conf:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen         0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
#    Load           "type1"
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
    Option	"XkbModel"	"pc105"
    Option	"XkbLayout"	"se"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL E173FP"
    HorizSync       31.0 - 80.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Gainward GTS 250"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: 1024x768 +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

---

### Post by gjn on 2009-04-06
I have a GTS 250 as well, so I tried the CUDA driver on a 8.10 Live CD (AMD 64). I got the same results, first the type1 and then "No devices detected". Nvidia only officially support that card from 182 on. Nvidia also states in the release notes that only Ubuntu 8.04 is supported. 

You can recover from this failed attempt, but you need to understand the difference between the Ubuntu packaged binary drivers and the nvidia.com driver. You can't switch back and forth easily. Everything you need to know is here:
**nvidia-glx restricted driver:** [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")
**nvidia.com drivers:** [https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")

Read this warning:
> When using manually installed NVIDIA binary drivers you will need to redo some of the following steps every time packages related to mesa or linux-image are updated (see the Kernel and Mesa Updates section for details). Attempts to revert to the Ubuntu provided NVIDIA binary drivers may prove troublesome and upgrades to the next Ubuntu release (e.g. from Ubuntu 7.04 to 7.10) may fail unless the manual install is correctly uninstalled first.

I have done this several times with my card and it works well. I have not attempted to uninstall an nvidia.com driver yet.

---

