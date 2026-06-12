---
title: "Screen resolution NOT what I specified in xorg.conf!"
date: 2006-12-31
forum: Desktop Environments
---

### Post by wilberfan on 2006-12-31
I just noticed tonight that I only have two choices of screen res:   50 or 54  -- but my xorg.conf file specifically says **60 hz**!    What happened??

Here's the pertinent part of my xorg.conf:

> Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600]"
    Driver         "nvidia"
EndSection

Section "Monitor"
    Identifier     "HP f1905"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600]"
    Monitor        "HP f1905"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024_60" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024_60" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024_60" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024_60" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024_60" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "**1280x1024_60**" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Could it have something to do with the latest nvidia driver??   (It might be the newest beta (?), but I don't remember how to find out which version I'm running.)

---

