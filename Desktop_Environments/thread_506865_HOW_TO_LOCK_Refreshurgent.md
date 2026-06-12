---
title: "HOW TO LOCK Refresh**urgent**"
date: 2007-07-22
forum: Desktop Environments
---

### Post by justincnn on 2007-07-22
Monitor:SAMSUNG MyncMaster 711N
Display Cart:7300GT 256M 128bit
Drivers of Display card:100.14.11 

I make the nvidia-settings to 60HZ ,but everytime reboot the PC ,the nvidia-setting jump to "AUTO"

&the refresh changes to 75HZ,

but my lcd's best Refresh is 60HZ ,

pls kindly advice me how to lock the refresh

my xorg as below:

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       40.0 - 80.0
    VertRefresh     56.0 - 60.0
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
EndSection:popcorn:


:popcorn::popcorn:

---

### Post by justincnn on 2007-07-22
Hi All:

Any news ,

Tks

---

