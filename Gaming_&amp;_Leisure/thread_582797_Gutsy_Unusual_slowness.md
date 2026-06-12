---
title: "Gutsy: Unusual slowness"
date: 2007-10-20
forum: Gaming &amp; Leisure
---

### Post by DJ Wings on 2007-10-20
Is anyone else having a problem with unusually low FPS rates? I ran GLXGears, and it reported 260FPS. Usually, I can get at least 900 on my Intel GMA950, but this is just weird. Sauerbraten ran at under 10FPS (metl4) with **all** the effects turned off. I'm running Xubuntu 7.10.

---

### Post by TidusBlade on 2007-10-20
Just a thought, you might have to reinstall your drivers again or something?

---

### Post by divali on 2007-10-20
Yes, horrid slowness here as well. Using Gnome desktop. Fiesty was nice and fast
so one day later after a trouble free upgrade this is quite a let down. In the meantime I'll be searching for the solution.

---

### Post by DJ Wings on 2007-10-20
> **TidusBlade said:**
> Just a thought, you might have to reinstall your drivers again or something?

I doubt it. GMA950 drivers are built-in. I think it's an issue with X, since I don't see a "Modules" section in xorg.conf, and when I tried to add one (to load DRI and DBE), it said it was invalid.

---

### Post by DJ Wings on 2007-10-20
I'm installing libgl1-mesa-dri, I'll see if that has any effect on it.
EDIT: Oh yeah, that did it... GLXGears jumped to 844FPS (with Firefox, Exaile, and Transmission open and XFWM compositing on!) without restarting X, and now openArena runs smoothly.

---

### Post by Perfect Storm on 2007-10-20
Great! Please, mark thread solved. (the info I can pass on to others who got intel problems).

---

### Post by DJ Wings on 2007-10-20
Duplicate post... I really hate my ISP right now.

---

