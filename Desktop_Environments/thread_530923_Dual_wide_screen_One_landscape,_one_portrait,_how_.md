---
title: "Dual wide screen: One landscape, one portrait, how to?"
date: 2007-08-21
forum: Desktop Environments
---

### Post by mdoyle on 2007-08-21
Alright. I've got a dual widescreen setup. I currently have them both setup and working correctly, but they are both set to landscape (hard to deal with since one is mounted on my wall as portrait). I have added:

Option "RandRRotation" "On"

to my xorg.conf file, and that allows me to rotate the_entire_desktop but not just a single monitor. Is there anyway that I can do this?

I am running Gutsy, video card is an nvidia 7950, and it's a Core 2 Quad with an Intel board.

---

### Post by mdoyle on 2007-08-21
bump

---

### Post by mdoyle on 2007-08-22
So not possible?

---

### Post by phillyphilphil on 2007-09-04
Hi there,

I've got the same problem.  The issue seems to be with the driver treating both monitors as one desktop -- even with TwinView enabled, it doesn't allow me to rotate only one screen either.  

I know that this can be done, Google results show that some people were able to accomplish this.  Just gotta figure out how to do it now...

---

### Post by jai_mantravadi on 2007-10-07
mdoyle and phillyphil,
I was searching how to do this for just one screen, and came across xrandr. It appears to have options for multiple displays although, I'm not sure if it would work for your problem or not. I was just replying because it seemed like it might. I'm not an expert on it tho. Good luck!
Jai

---

### Post by mdoyle on 2007-10-07
I've actually got it working a_long_time_ago. The following is my monitor, screen and device portion of my xorg.conf file. Hope it helps others.

Note: I have Xinerama and Seperate X Screen enabled in the Nvidia Settings manager.

```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "ViewSonic VX2235wm"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
    Option	   "RandRRotation" "On"
    Option	   "Rotate" "CW"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VX2235wm"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7950 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7950 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard0"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "DFP-0: 1680x1050 +0+0; DFP-0: 1280x1024 +0+0; DFP-0: 1024x768 +0+0; DFP-0: 832x624 +0+0; DFP-0: 800x600 +0+0; DFP-0: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard1"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "DFP-0: 1680x1050 +0+0; DFP-0: 1280x1024 +0+0; DFP-0: 1024x768 +0+0; DFP-0: 832x624 +0+0; DFP-0: 800x600 +0+0; DFP-0: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

---

