---
title: "Loki + Heretic II on breezy"
date: 2005-11-27
forum: Gaming &amp; Leisure
---

### Post by anindya_m on 2005-11-27
This describes my experiences while installing Heretic II on my laptop. Hope it is useful.

System Config: Dell Inspiron 9300 (1.73Ghz, 512MB, 100GB, GeForce 6800)

**Step 1:** Get the Loki installer file (loki_demos-full-1.0e-x86.run) from the website. Proceed with install as usual.
**Step 2:** Run the loki_update program to download and install Heretic II. At this stage the game ran, but it would render only in software (it could not find the OpenGL library) and and sound would not work (an issue with SDL).
**Step 3:** Fix sound. I used the following environment setting in bash before running the loki launcher from the same shell:
```
export SDL_DSP_NOSELECT='1'
./loki_demos
```
I found this solution in [this post]("http://ubuntuforums.org/showthread.php?t=82135"). Thanks to Staesys. The issue is also described [here]("http://www.libsdl.org/faq.php?action=listentries&category=3").
**Step 4:** OpenGL. The library file it was looking for turns out to be /usr/lib/libglut.so.3.8.0 I entered this in the OpenGL Library box in the configuration utility. After that everything works fine :D

---

### Post by rawler on 2006-02-04
Dude, you're my HERO! :D Do you know for how long I've waited to get this game running?! :D

---

### Post by almostlinux on 2008-04-12
Amazing .. thanks. Finally I can play heretic2 :)

---

