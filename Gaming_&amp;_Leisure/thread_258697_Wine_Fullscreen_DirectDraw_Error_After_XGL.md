---
title: "Wine Fullscreen DirectDraw Error After XGL"
date: 2006-09-16
forum: Gaming &amp; Leisure
---

### Post by QuartersMostly on 2006-09-16
After I installed XGL (I believe that was the only change I made), whenever I try to run Diablo II in fullscreen, I get a DirectDraw error #22. It runs windowed just fine. Do you think I just need to reinstall wine? I think I might have also messed with the winecfg and changed the Windows version to XP from 98, but changing it back had no effect. Shutting down Compiz did not have any effect.

---

### Post by hanzomon4 on 2006-09-16
Try this, if it works xgl is the problem

1. press alt+ctrl+F1, and login
2.type this in, startx -- :1 This will start an xsession on alt+ctrl+F8.
3. try your game if it works the problem is xgl(the xserver compiz runs on)

Depending on how you run xgl ,as a session or with gdm, you can add an option that lets you run apps om the regular xserver within xgl.

---

### Post by QuartersMostly on 2006-09-16
Well, that was definitely it. Do you know how to run xserver from within XGL? I start XGL as a session.

---

### Post by hanzomon4 on 2006-09-16
Yes add this to the xgl command in your session script "-xorgAc" here is an example 

```
Xgl -fullscreen :1 -ac [COLOR="Red"]-xorgAc[/COLOR] -accel glx:pbuffer -accel xv:fbo & sleep 2 && DISPLAY=:1
```

If you are on a nvidia card then you would start your game like this.

```
DISPLAY=:93 /run/game
```

I'm not sure which display ati users use.

---

### Post by QuartersMostly on 2006-09-16
That worked perfectly! And it solved the problem of the gnome panels showing up during the game. Thanks!

---

