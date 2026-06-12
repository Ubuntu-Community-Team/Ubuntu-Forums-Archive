---
title: "Cant drag icons across monitors with twinview"
date: 2007-06-14
forum: Desktop Environments
---

### Post by Gruelius on 2007-06-14
Hi all,
with my setup i cant drag icons to the other monitor. I think this is because twinview uses only one monitor in its xorg.conf file

```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "BenQ FP222W"
    HorizSync       30.0 - 84.0
    VertRefresh     56.0 - 76.0
    ModeLine       "1024x768@60" 64.6 1024 1056 1296 1328 768 783 791 807 +hsync +vsync
    Option         "DPMS"
EndSection
```

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: 1680x1050_60 +0+0, DFP-1: 1280x1024_75 +1680+0; DFP-0: 1152x864 +1680+0, DFP-1: nvidia-auto-select +0+0; DFP-0: 1024x768 +0+0, DFP-1: NULL; DFP-0: 832x624 +0+0, DFP-1: NULL; DFP-0: 800x600 +0+0, DFP-1: NULL; DFP-0: 640x480 +0+0, DFP-1: NULL; DFP-0: 640x350 +0+0, DFP-1: NULL; DFP-0: 1280x1024 +0+0, DFP-1: NULL; DFP-0: 1024x768_60 +0+0, DFP-1: NULL"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
```

Any ideas?

---

