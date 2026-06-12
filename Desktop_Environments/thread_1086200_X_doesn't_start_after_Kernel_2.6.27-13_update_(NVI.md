---
title: "X doesn't start after Kernel 2.6.27-13 update (NVIDIA ?)"
date: 2009-03-03
forum: Desktop Environments
---

### Post by martinm1000 on 2009-03-03
Hi,

Since yesterday kernel -13 update, I get a black screen instead of gnome login manager;

I think this might be nvidia related; I'm using driver 177.

Things still work booting the previous -12 kernel.

If I compare X window logs, the part in bold is what I don't see under kernel -13 (Hang?)

(II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
[B](II) NVIDIA(0): NVIDIA GPU GeForce Go 7400 (G72) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.21.fe
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce Go 7400 at PCI:1:0:0:
(--) NVIDIA(0):     LPL (DFP-0)
(--) NVIDIA(0): LPL (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): LPL (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0[/B]
(...)

---

### Post by martinm1000 on 2009-03-03
Ok, well it looks like this is the Thread:

[http://ubuntuforums.org/showthread.php?t=1084959](http://ubuntuforums.org/showthread.php?t=1084959)

(Kind of hard to find without a proper title....)

Common guys, push the nvidia driver 180 WITH 2.6.27-13 !!!

---

