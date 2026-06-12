---
title: "xcompmgr causes transparent screensavers &amp; games"
date: 2006-07-27
forum: Desktop Environments
---

### Post by dswissmiss on 2006-07-27
Hi guys,
I'm running Xubuntu Dapper and when I have xcompmgr running my desktop still shows through when running screensavers and games. It's like they run at 80% transparency (even if I don't turn transparency on in the xfce4 options menu).
Is there some option I'm missing or need to comment out in my xorg.conf file?

Thank you
Dswissmiss

parts of my xorg.conf file:
```
...
Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection
...
Section "Device"
        Identifier      "NVIDIA Corporation NV40 [GeForce 6800]"
        Driver          "nvidia"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
        Option          "NoLogo"
        Option          "UseEdidDpi"   "FALSE"
        Option          "DPI"   "96 x 96"
        BusID           "PCI:1:0:0"
EndSection
...
Section "Extensions"
        Option  "Composite" "Enable"
EndSection

```

---

### Post by jpkotta on 2006-07-27
I don't think the details of xcompmgr are set in the xorg.conf.  xorg.conf only enables the ability to composite.  IIRC, XFCE has a built-in compositer, and that might be interfering with xcompmgr.  Also, I've heard the built-in one is more stable and featureful.  Try using it instead.

*Note: I don't use XFCE (FVWM instead), but I do use xcompmgr.*

---

### Post by dswissmiss on 2006-07-27
Thanx for the reply.
I uninstalled xcompmgr and rebooted but still have the same problem with the built in compositor.
Any ideas?

Thank you

---

### Post by jpkotta on 2006-07-28
I'm out of ideas.  At least you know it's not xcompmgr.

---

### Post by dswissmiss on 2006-08-26
I've found the answer for anyone who cares:
Settings Manager > Window Manager Tweaks > Compositor > turn off Opacity for Popup Windows (make it opaque)

---

