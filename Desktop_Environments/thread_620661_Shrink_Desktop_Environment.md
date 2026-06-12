---
title: "Shrink Desktop Environment"
date: 2007-11-22
forum: Desktop Environments
---

### Post by natewiebe13 on 2007-11-22
Is there a way to virtually make your desktop smaller. I am having overscan issues and ive read numerous amounts of forums, but nothing has seemed to work. I have a nVidia 7600GS to a Toshiba 62MX196. NTSC. If there is a way to virtually make the desktop smaller, as i think you can do in mythbuntu, i think it will trick my tv into showing the whole desktop. I am missing about 5% of screen on the top, bottom, and both sides. I am using a DVI - HDMI Monster Cable 800 series.
hope someone has the answer
thanks

---

### Post by genbuntu on 2007-11-22
hmm... I may be wrong but doesn't this have something to do with the screen resolution . If so you may try adjusting it (System>preferences> screen resolution)  to a higher one.
Edit: or maybe a lower one.

---

### Post by natewiebe13 on 2007-11-26
even with different resolutions I still get an overscan...so im hoping that i can have a virtual resolution inside of the actual resolution.

---

### Post by dcherryholmes on 2007-12-31
Bump on this.  I've got everything working great in mythbuntu w/ a 42" Phillips LCD 1080p while actually viewing through the myth frontend.  But if I switch over to a virtual desktop, or if I go into any of the configuration screens for myth, I have the same 5% or so of the desktop off the edge of the screen.

some relevant bits of xorg.conf in case it helps:

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Philips MAGNAVOX TV"
    HorizSync       30.0 - 75.0
    VertRefresh     56.0 - 62.0
    Option         "DPMS"
#    Option         "ConnectedMonitor" "TV"
    Option         "TVStandard" "HD1080p"
    Option         "TVOverScan" "0.0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1920x1080 +0+0; DFP: 1280x1024 +0+0; DFP: 1024x768 +0+0; DFP: 800x600 +0+0; DFP
: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

