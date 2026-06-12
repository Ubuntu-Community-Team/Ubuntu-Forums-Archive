---
title: "Now do I set the initial viewport position?"
date: 2009-10-20
forum: Desktop Environments
---

### Post by OrangeVixen on 2009-10-20
I set up X so that I have a 1024x768 resolution but with a virtual size of 1280x1024. But I want the initial view position to be in the "center", so I figured I should use the Viewport option but it's not working. Here is my xorg.conf Screen section:

```

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
#    Option         "metamodes" "1024x768 +0+0"
    Option         "metamodes" "1024x768 @1280x1024 +0+0"
    SubSection     "Display"
        ViewPort    128 128
        Depth       24
    EndSubSection
EndSection

```

Note that I have Nvidia card.

---

