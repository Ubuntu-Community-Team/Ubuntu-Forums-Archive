---
title: "Unreal Tournament breaks VSync in Unity"
date: 2014-02-16
forum: Gaming &amp; Leisure
---

### Post by Brandon_MacEachern on 2014-02-16
When I play Unreal Tournament on my system (Windows version through Wine), the game plays great and very well.  However, when I quit the game, dragging windows around and videos in Unity, no longer have VSync, and shows tearing.  Logging out and back in always fixes it.

In CCSM Vsync is on.  Toggling it off and on in the OpenGL section doesn't help.

I am using a Radeon 4870 with Ubuntu 13.10 so only the open source driver is an option for me.

---

### Post by stevephillipgreen on 2014-02-20
I would try running it by changing "do not allow window manager to decorate/control windows" in wine config.

---

### Post by knpoe on 2014-02-23
honestly - composite managers should be off when running a game. And don't use vsync.  if you can, set maxfps to your monitors frequency if you really care about frame-tearing, and call it a day. **vsync = input lag, mouse smoothing = input lag.**

i play all my games in a window manager with no composite managing by default, '*awesome*'. When I want transparent things-*and-glitter* i just turn on '*unagi*'.

you should try awesome

---

