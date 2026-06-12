---
title: "dual-monitor resolution problem"
date: 2009-02-17
forum: Desktop Environments
---

### Post by islan on 2009-02-17
Using the nvidia-settings dialog I was able to set up my dual-monitors, only there was one problem.  I was able to get high-resolutions for the first monitor, but not so high with the second monitor.  It is especially perplexing because they are both the same brand of monitor, though the nvidia-settings does not list them as such.

Any advice, or more info needed?

---

### Post by dzark on 2009-02-17
Graphics card and driver versions pls :)

---

### Post by islan on 2009-02-17
Card:  GeForce 7600 GS

Driver:  NVIDIA accelerated graphics driver (version 177)

---

### Post by dzark on 2009-02-17
Im pretty sure i used to be able to pull dual 1600x1200 on my 7600GS.. It may be a EDID issue - are both monitors DVI, 1 VGA/1 DVI or both VGA?

If they're one of each, try swapping? Does graphics card have both same plugs on back?

---

### Post by islan on 2009-02-17
> **dzark said:**
> Im pretty sure i used to be able to pull dual 1600x1200 on my 7600GS.. It may be a EDID issue - are both monitors DVI, 1 VGA/1 DVI or both VGA?

If they're one of each, try swapping? Does graphics card have both same plugs on back?

They both use VGA cables (those are the short ones, right?)

They are both using the same graphics card, with one of its ports using a converter to VGA.

I also have a second graphics card that I'm thinking about using for SLI, but that's another matter.

---

### Post by dzark on 2009-02-17
If you try swapping the cables, and re-detecting displays etc, and it's the same physical output of the card that is causing the problem, i think this link will help

[http://ubuntuforums.org/showthread.php?t=316985](http://ubuntuforums.org/showthread.php?t=316985)

The monitors send EDID data to the graphics card that tells it what resolutions/refresh/etc it can handle, and sometimes this gets lost... This will let you manually set the limits :)

---

### Post by islan on 2009-02-17
Okay, so apparently performing updates actually helped.  Thanks for your advice!

---

