---
title: "nvidia driver help!"
date: 2009-05-02
forum: General Help
---

### Post by imscrewed on 2009-05-02
When using nvidia drivers with DVI to HDMI, the screen flashes black every 3 to 10 seconds. "No Video Signal" or "Unsupported Video Format" is displayed on the television screen.

This started with Ubuntu 8.10, I tried using nvidia driver 177. I gave up and upgraded to Ubuntu 9.04 and the issue persists. I have tried using nvidia drivers 180.44 and 185.19.1~Really185.18.04

Ubuntu 9.04 AMD64
ASUS M2N-SLI Deluxe
eVGA Nvidia GTX260
Philips 47PFL7422D/37

I see others experiencing this same problem, but their solution doesn't seem to resolve my issue. I have searched and searched and am about to give up. Please help.

My only conclusion, and this is purely assumption, is that this is yet another issue with 64bit Ubuntu?

---

### Post by dcstar on 2009-05-02
> **imscrewed said:**
> When using nvidia drivers with DVI to HDMI, the screen flashes black every 3 to 10 seconds. "No Video Signal" or "Unsupported Video Format" is displayed on the television screen.

This started with Ubuntu 8.10, I tried using nvidia driver 177. I gave up and upgraded to Ubuntu 9.04 and the issue persists. I have tried using nvidia drivers 180.44 and 185.19.1~Really185.18.04

Ubuntu 9.04 AMD64
ASUS M2N-SLI Deluxe
eVGA Nvidia GTX260
Philips 47PFL7422D/37

I see others experiencing this same problem, but their solution doesn't seem to resolve my issue. I have searched and searched and am about to give up. Please help.

My only conclusion, and this is purely assumption, is that this is yet another issue with 64bit Ubuntu?

And what resolution have **you** set to send to the external device?

---

### Post by imscrewed on 2009-05-03
> **dcstar said:**
> And what resolution have **you** set to send to the external device?

1920x1080 at 60 Hz

Checking my Xorg.0.log...
```
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0; 1920x1080_60 +0+0;"
(**) NVIDIA(0): Option "FlatPanelProperties" "Scaling = Native"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce GTX 260 (GT200) at PCI:3:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 917504 kBytes
(--) NVIDIA(0): VideoBIOS: 62.00.1a.00.1a
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce GTX 260 at PCI:3:0:0:
(--) NVIDIA(0):     Philips FTV (DFP-1)
(--) NVIDIA(0): Philips FTV (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Philips FTV (DFP-1): Internal Dual Link TMDS
(WW) NVIDIA(0): The EDID for Philips FTV (DFP-1) contradicts itself: mode
(WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
(WW) NVIDIA(0):     valid VertRefresh range (58.000-62.000 Hz) would exclude
(WW) NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
(WW) NVIDIA(0):     check for mode "1920x1080".
(WW) NVIDIA(0): The EDID for Philips FTV (DFP-1) contradicts itself: mode
(WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
(WW) NVIDIA(0):     valid VertRefresh range (58.000-62.000 Hz) would exclude
(WW) NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
(WW) NVIDIA(0):     check for mode "1920x1080".
(WW) NVIDIA(0): The EDID for Philips FTV (DFP-1) contradicts itself: mode
(WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
(WW) NVIDIA(0):     valid VertRefresh range (58.000-62.000 Hz) would exclude
(WW) NVIDIA(0):     this mode's VertRefresh (30.0 Hz); ignoring VertRefresh
(WW) NVIDIA(0):     check for mode "1920x1080".
(WW) NVIDIA(0): The EDID for Philips FTV (DFP-1) contradicts itself: mode
(WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
(WW) NVIDIA(0):     valid VertRefresh range (58.000-62.000 Hz) would exclude
(WW) NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
(WW) NVIDIA(0):     check for mode "1920x1080".
(WW) NVIDIA(0): The EDID for Philips FTV (DFP-1) contradicts itself: mode
(WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
(WW) NVIDIA(0):     valid VertRefresh range (58.000-62.000 Hz) would exclude
(WW) NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
(WW) NVIDIA(0):     check for mode "1920x1080".
(WW) NVIDIA(0): The EDID for Philips FTV (DFP-1) contradicts itself: mode
(WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
(WW) NVIDIA(0):     valid VertRefresh range (58.000-62.000 Hz) would exclude
(WW) NVIDIA(0):     this mode's VertRefresh (30.0 Hz); ignoring VertRefresh
(WW) NVIDIA(0):     check for mode "1920x1080".
(II) NVIDIA(0): Assigned Display Device: DFP-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select+0+0"
(II) NVIDIA(0):     "1920x1080_60+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(--) NVIDIA(0): DPI set to (76, 76); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
```The warning has got me stuck.

---

### Post by imscrewed on 2009-05-05
Well, I seem to have found a workaround.

Adding ModeLines to the monitor section, setting UseEDID to false and ExactModeTimingsDVI to true within xorg.conf seemed to have resolved this issue. This is working with the 185.19 beta driver.

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Philips FTV"
    HorizSync       15.0 - 70.0
    VertRefresh     58.0 - 62.0
    Option         "ExactModeTimingsDVI" "TRUE"
    # 1920x1080 @ 60 Hz (EDID)
    ModeLine        "1920x1080" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +HSync +VSync
    # 1920x1080 @ 24 Hz (EDID)
    ModeLine        "1920x1080_24" 74.25 1920 2558 2602 2750 1080 1084 1089 1125 +HSync +VSync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 260"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "UseEDID" "FALSE"
    Option         "DPI" "76 x 76"
    Option         "TwinView" "0"
    Option         "FlatPanelProperties" "Scaling = Native"
    SubSection     "Display"
        Modes      "1920x1080"  
        Depth      24
    EndSubSection
EndSection
```BTW, during all of this I ended up replacing 64bit Ubuntu with 32bit, and the problem persisted. So I will now try this fix with 64bit. Ugh...

---

