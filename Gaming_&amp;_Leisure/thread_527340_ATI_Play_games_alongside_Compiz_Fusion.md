---
title: "ATI: Play games alongside Compiz Fusion?"
date: 2007-08-16
forum: Gaming &amp; Leisure
---

### Post by quadomatic on 2007-08-16
I was wondering if anyone knew whether I can play games alongside Compiz Fusion.

I recently tried Unreal Tournament 2004 natively, and under a session where XGL and Compiz Fusion were running, the game crashed. However, I have a separate session that doesn't run XGL and Compiz Fusion, and the game ran perfectly fine.

Is there a way that I can play games in the same session as XGL and Compiz Fusion, and not have to log out whenever I play games.

---

### Post by cogadh on 2007-08-16
Running 3D applications while running a 3D accellerated desktop manager is not really recommended. I always disable Compiz/Beryl/Fusion before running any games and then turn it back on when I'm done. There is no need to logout at all.

---

### Post by luisromangz on 2007-08-16
If you are using XGL, you have to start a normal session without XGL before having good performance and no crashes with games. Just disabling Compiz won't work. XGL adds another layer between apps and the xserver, and that layer provides just the necessary to run the accelerated window managers. If you were using AIGLX, disabling Compiz would do the trick.

---

