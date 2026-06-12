---
title: "libgl1-mesa-dri update and warsow?"
date: 2007-08-02
forum: Gaming &amp; Leisure
---

### Post by hype on 2007-08-02
Hi there,
after updating my system, i've had these "interesting" updates:
libgl1-mesa-dri
libgl1-mesa-glx
libglu1-mesa mesa-utils

I then started [warsow]("http://www.warsow.net/") and noticed _extremly poor performance_, where i was playing just smoothly a few minutes/hours before. 
(125 fps before, 24 after)

After searching logs, i actually realised that **i had no direct rendering anymore.**
Tho like i said it was juste fine few hours sooner, and that i didnt modify my xorg.conf or anything else except these libgl updates.

I use a nvidia 7600GT with 9755 drivers.

Did anyone had the same problem with warsow or any other game?

A weird thing is that i can actually use compiz-fusion without any performances problems (apparently)

Anyone could explain the link between libgl and the fact that direct rendering is off? Isnt the video card driver's supposed to "handle" direct rendering?

---

### Post by hype on 2007-08-02
Ok problem solved:
I just recompiled Nvidia drivers 9755 (after uninstlling them)

Direct rendering: Yes !

---

