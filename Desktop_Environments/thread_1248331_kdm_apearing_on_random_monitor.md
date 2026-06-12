---
title: "kdm apearing on random monitor"
date: 2009-08-24
forum: Desktop Environments
---

### Post by reub2000 on 2009-08-24
Edit: Issue has been solved in KDE 4.3.1.

I'm running Kubuntu on a dual-head setup using nvidia twinview. The problem is that the prompt for kdm appears on a seemingly random monitor. I'd prefer if it always came up on the monitor on my left.

Here is the device section for xorg.conf in case it is relevant:
```
Section "Device"
        Identifier  "Card0"
        Driver      "nvidia"
        VendorName  "nVidia Corporation"
        BoardName   "NV40 [GeForce 7800 GS]"
        BusID       "PCI:1:0:0"
        Option  "AllowGLXWithComposite" "Yes"
        Option  "TwinView"
        Option  "RenderAccel"
        Option  "MetaModes"     "1280x1024,1280x1024;NULL,1280x1024;NULL,1024x768;NULL,800x600;NULL,640x480"
        Option  "TwinViewOrientation"   "LeftOf"
        Option  "SecondMonitorHorizSync"        "31.5-110.0"
        Option  "SecondMonitorVertRefresh"      "60"
        EndSection
```

---

### Post by reub2000 on 2009-08-28
Anyone else using KDE 4.2 on a mutli monitor setup?

Another issue is that if I switch to a video mode without the monitor on the right using xrandr, the plasma toolbar disappears.

---

