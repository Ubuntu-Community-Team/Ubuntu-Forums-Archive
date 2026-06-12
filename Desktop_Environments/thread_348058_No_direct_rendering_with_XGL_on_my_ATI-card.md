---
title: "No direct rendering with XGL on my ATI-card"
date: 2007-01-28
forum: Desktop Environments
---

### Post by SPENEN on 2007-01-28
If I run the ordinary gnome-session the graphics card is working perfectly.
It both have "direct rendering: yes" and OpenGL vendor string: "ATI Technologies Inc." so it seem to work.

But when I choose the XGL session and type glxinfo the vendor string is still the same but "direct rendering: no". In addition to that it sais 'Xlib: extension "XFree86-DRI" missing on display ":1:0".'

So why does direct rendering change from yes to no when I start XGL? If I start XGL in a normal session where direct rendering is on the XGL-session still sais direct rendering is off.

What am I doing wrong?

---

### Post by Ramses de Norre on 2007-01-28
That's normal, it's a little bug in xgl but it causes no harm and the developers prefer fixing other bugs. Your direct rendering is probably working perfect but glxinfo doesn't detect it correctly due to xgl. So if xgl runs fine: nothing to worry about.

---

### Post by PriceChild on 2007-01-28
Yeah as Ramses says, its fine.

Basically xgl sits on top and steals all your GPU. Unless you start sneaky sessions on new Xservers, you can't run anything 3Dish on top of xgl. compositing works with xgl fine though.

---

### Post by SPENEN on 2007-01-28
Ahh, thanks a lot.

But it's kind of wierd because when I run XGL everything is really slow, like it takes forever to write things in the terminal and moving windows are very slow.

When I ran AIGLX everything went smooth, so something has to be wrong with my configuration of XGL or the drivers.

---

