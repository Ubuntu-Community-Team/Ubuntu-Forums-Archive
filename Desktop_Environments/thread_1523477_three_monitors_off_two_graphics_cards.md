---
title: "three monitors off two graphics cards?"
date: 2010-07-03
forum: Desktop Environments
---

### Post by skipi-gz on 2010-07-03
hi, i doubt that this is possible at all but if i don't post this i dont think i will be able to sleep tonight. i have an on-board VIA P4M900 graphics and a nVidia GeForce GT 220 graphics card which is running TwinView at the moment.
xorg.conf:
> ....(skipping unimportant part)
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 71.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 220"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: 1280x1024 +1024+0, CRT-1: 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
(dont laugh at CRT-0 CRT-1 :P)
is it possible to use my VIA card for a third monitor? i tried [http://ubuntuforums.org/showthread.php?t=697280](http://ubuntuforums.org/showthread.php?t=697280) as a reference but it didn't work soo nicely :( (it is an old thread anyway).
thanks
skipi

---

### Post by skipi-gz on 2010-07-05
bounce

---

