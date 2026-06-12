---
title: "Multipl NVidia Cards and Xinerama"
date: 2009-09-23
forum: Desktop Environments
---

### Post by stefanadelbert on 2009-09-23
I'm trying to setup four monitors on two NVidia cards, 8600GT (PCIe) and GeForce 6200 (PCI).

Extract from lspci:
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
05:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

So far I have used nvidia-settings to setup two X screens successfully, but if I enable Xinerama I am unable to restart X (continually flicks displays on and off) and I need to manually run 'gdm stop' and switch back to a working xorg.conf.

Has anyone successfully got a similar setup working?

---

### Post by 65 mustang on 2009-11-02
> **stefanadelbert said:**
> I'm trying to setup four monitors on two NVidia cards, 8600GT (PCIe) and GeForce 6200 (PCI).

Extract from lspci:
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
05:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

So far I have used nvidia-settings to setup two X screens successfully, but if I enable Xinerama I am unable to restart X (continually flicks displays on and off) and I need to manually run 'gdm stop' and switch back to a working xorg.conf.

Has anyone successfully got a similar setup working?

+1 have this same problem on 9.04 and 9.10

---

### Post by Tallivant on 2009-11-30
You'll need to dual head both the 6200 and 8600.  I have a dual-head setup running two monitors (a 32" widescreen hdtv and 15.4" laptop screen) on my nvidia 8600 using xinerama, here's the xorg.conf file basics:

> Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 720
    Screen      1  "Screen1" Above "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LPL"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "PRI HDMI TV"
    HorizSync       15.0 - 68.0
    VertRefresh     48.0 - 76.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "DynamicTwinView" "true"
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: 1440x900 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "DynamicTwinView" "true"
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "DFP-1: 1280x720 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
I would recommend using this setup on your nvidia 8600 (customized to your screen resolutions and positionings), and then duplicating it for the 6200 (for a total of 4 devices, 4 screens, and 4 monitors)

---

### Post by stefanadelbert on 2009-12-01
Thanks, Tallivant. I'll give it a go!

---

