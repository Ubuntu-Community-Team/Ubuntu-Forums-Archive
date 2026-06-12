---
title: "kernel 2.6.15-23-386 + nvidia = failed to load xorg"
date: 2006-05-24
forum: Desktop Environments
---

### Post by jan247 on 2006-05-24
Hi, can anyone help me out?

If I'm booting: Ubuntu, kernel 2.6.15-22-386 with log:
[I](II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo"
(**) NVIDIA(0): Enabling RENDER acceleration
(WW) NVIDIA(0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce 6600 GT at PCI:5:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.61.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6600 GT at PCI:5:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 400 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1280x960"
(II) NVIDIA(0):     "1152x864"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default[/I]

Everything seems to work fine, but if it's Ubuntu, kernel 2.6.15-23-386, xorg fails, and the log says:

[I](II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo"
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.[/I]

Fatal server error:
no screens found

Can anyoune help me out on this? I am pretty sure they use the same xorg.conf and drivers...

---

### Post by jan247 on 2006-05-24
oh, i'm sorry.. i'm in the wrong forums.. shouldve posted in under dapper

---

