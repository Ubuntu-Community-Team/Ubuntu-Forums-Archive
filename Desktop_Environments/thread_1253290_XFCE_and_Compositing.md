---
title: "XFCE and Compositing"
date: 2009-08-29
forum: Desktop Environments
---

### Post by Nimless on 2009-08-29
Hello,

Is there a way to solve the tearing in XFCE with video playback when compositing is enabled? I think it's a sync to vblank problem, but i haven't find an option there.

Everything works on Gnome so it must be a problem with the XFCE compositer...

---

### Post by morgengenuss on 2009-08-30
what graphic card / driver are you using?
(maybe you can set options for that in xorg.conf)

also, you could try vlc with some alternative video settings (like using the cpu instead of the gpu to accelerate video).

---

### Post by Nimless on 2009-08-31
> **morgengenuss said:**
> what graphic card / driver are you using?
(maybe you can set options for that in xorg.conf)

also, you could try vlc with some alternative video settings (like using the cpu instead of the gpu to accelerate video).

I'm using nvidia with the latest proprietary driver...

---

