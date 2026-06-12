---
title: "Beryl and resolution"
date: 2007-02-17
forum: Desktop Environments
---

### Post by omoikane on 2007-02-17
I installed nvidia driver and it runs perfectly, shows up to 1600x1200 resolution.
I set resolution to 1280x1024 and it works just fine, I rebooted and it has no problem.

But I installed beryl and rebooted, my resolution is locked to 800x600 and cannot changable.
I removed beryl but resolution cannot back to normal.

and this is my log from /var/log/Xorg.0.log

```
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GT at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.25.53
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GT at PCI:1:0:0:
(--) NVIDIA(0):     @@@ (CRT-0)
(--) NVIDIA(0): @@@ (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(WW) NVIDIA(0): No valid modes for "832x624"; removing.
(WW) NVIDIA(0): No valid modes for "800x600"; removing.
(WW) NVIDIA(0): No valid modes for "720x400"; removing.
(WW) NVIDIA(0): No valid modes for "640x480"; removing.
(WW) NVIDIA(0): No valid modes for "1x1"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 800 x 600
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.

```

---

### Post by tekpunk on 2007-03-03
I have the same problem too..hopefully some one knows what to do.

---

### Post by KingCharles on 2007-03-04
Same here.

I just reinstalled clean, full system, and immediately after, updated all necessary updates.
I installed the nvidia driver from their website, and for some odd reason I got a resolution lock to 800x600 with a refresh rate of 50Hz too.

The odd thing is that the same exact driver was working before this morning. I am not sure what is going on but hope someone have some answers, because my eyes are hurting from this refresh rate! :(

---------------------------
EDIT:

OK... I found the answer [here]("http://www.nvnews.net/vbulletin/showthread.php?t=81635").

---

