---
title: "Sudden malfunction of radeon drivers on desktop startup"
date: 2011-01-18
forum: Desktop Environments
---

### Post by MichaelPalin on 2011-01-18
Some days ago, I tried to make some graphical changes to grub through the graphical configuration tool that can be installed through synaptic. Things like changing the resolution and maybe something else. I don't know if this was the cause, but since then, every time ubuntu starts, the screen freezes when the desktop should be loading and, if lucky, the only thing that can be seen is what looks like distorted parts (misaligned series of lines) of the desktop. For example, the cursor seem to be represented by some sort of square, but, as said, the image is frozen, nothing moves.

At this point, I tried to enter console mode by pressing Ctrl+Alt+F1 and the screen fills with error messages, one after another, of graphical nature. They say something like this:

```
[142.124758][drm:radeon_ib_schedule]*ERROR*radeon couldn't schedule IB(0).
[142.641019][drm:radeon_cs_ioctl]*ERROR*Faild to schedule IB!
```

Note. "Faild" is written correctly. The first numbers keep increasing and the IB number goes from 0 to 15. My only guess is that I messed up the drivers somehow buy changing something in GRUB. I don't remember doing anything strange apart from that.

It's an Ubuntu 10.10 with the free drivers for the Radeon family and the graphics card is a HD3870X2.

Any idea? Thanks in advance.

---

