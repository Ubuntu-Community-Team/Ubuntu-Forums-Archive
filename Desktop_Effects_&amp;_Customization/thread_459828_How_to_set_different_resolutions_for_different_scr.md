---
title: "How to set different resolutions for different screens"
date: 2007-05-31
forum: Desktop Effects &amp; Customization
---

### Post by ThomasNovin on 2007-05-31
Hi all

I have a HP nc8430 laptop which I use 50% by itself and 50% in a docked environment. When I use it standalone I'm using the native resolution 1680x1050. When I use it docked I have an external display which has 1280x1024 as native resolution.

The question is, how do I configure xorg.conf to automatically detect which display I'm using and set the resolution accordingly?

Strange thing is, at the login screen, I always get 1650x1050 (which ofcourse doesn't look very good when I'm docked) even though I have set my resolution to 1280x1024 in System>Preferences>Screen Resolution.

```

# Laptop display
Section "Monitor"
        Identifier   "Generic Monitor"
        HorizSync    28.0 - 84.0
        VertRefresh  43.0 - 60.0
        Option      "DPMS"
EndSection

# External display
Section "Monitor"
        Identifier   "aticonfig-Monitor[1]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Generic Video Card"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "1680x1050" "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[1]"
        Device     "aticonfig-Device[1]"
        Monitor    "aticonfig-Monitor[1]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1280x1024"
        EndSubSection
EndSection

```

---

