---
title: "Quake2 dynamic lighting not working!"
date: 2007-06-23
forum: Gaming &amp; Leisure
---

### Post by Zannax on 2007-06-23
I installed the quake2 package from ubuntu repositories  as well as quake2 data in the right directories.

It runs fine, but the dynamic lighting seems not to work right: when there are shoots/explosions, textures of the walls nearby become garbled with strange colors for a second.

I guess there's something wrong with dynamic lighting...

My video-card is ATI Radeon 7000 series, default ubuntu driver.
Is it a common issue? Is there a way to let it work right?

Thank you

---

### Post by Cappy on 2007-06-23
I did a quick google and found this:

The proprietary Linux drivers don't support the R100 chips (Radeon 7000-7500).

That's as good as you can get since ATI doesn't support "legacy" cards like NVIDIA does.

---

### Post by Zannax on 2007-06-24
Ok thank you, but I have **not** installed the proprietary ATI driver, I've kept the default one ubuntu installed with...

Maybe my card is not fully supported, although that's strange because it's not so an ancient one... :-)
Moreover it has the same defects selecting any video mode in the game, even with software rendering.

---

### Post by Zannax on 2007-06-24
Update: 
with "software x11" and "software SDL" drivers lighting works right but texture-blur is off, so it's quite uglier anyway...

So the problem is something with OpenGL drivers, maybe they don't work 100% ok with my card... Too bad maybe I get a newer one soon or later, an nVidia one...

---

