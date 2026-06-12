---
title: "Annoying 3d problem - some games stutter/skip frames, low FPS some OK"
date: 2007-02-04
forum: Gaming &amp; Leisure
---

### Post by psantucc on 2007-02-04
I've really no idea where to begin.

Recently (though after no particular event I can identify) some of my 3d games started running badly. I would call the problem a low FPS, but as you will see below, there is some evidence to the contrary. The best description I can manage is a frame skip or stutter - the net effect is slow, but not smoothly so. Audio seems to be affected as well, stuttering along with video.

These games work as expected:
Neverball
Neverputt
PlanetPenguin Racer (shows 125 FPS)

These games show the stutter:
Slune (shows 0 - 2.5 FPS)
Torcs (shows 60 - 180 FPS)
Tremulous (shows 48 FPS)

Slune and Torcs used to run as expected. Tremulous is newly installed.

FWIW, glxgears shows about 10 FPS.

My card is pretty capable - nVidia Quadro FX 1500.

I'm running 6.10 Edgy Eft and using nVidia commercial driver 1.0-9746

Any help appreciated - I'm lost.

---

### Post by Sammi on 2007-02-05
You're running the new beta driver. Try uninstalling it and installing the stable driver from the repositories.

---

### Post by conjur3r on 2007-02-05
How long ago did you last install your nvidia drivers?  Some updates overwrite (or remove) the nvidia kernel object which requires you to reinstall them.  This may not be the case here though, as you can still run 3d accelerated programs.  But it doesn't hurt to try?

Try running **top** in the background next time you run those games that do not work properly.  When a spike occurs, glance over to top to see if anything caused it.

---

### Post by Sammi on 2007-02-05
I love top :D

---

### Post by psantucc on 2007-02-05
> **Sammi said:**
> You're running the new beta driver. Try uninstalling it and installing the stable driver from the repositories.

Can't believe I didn't notice that. I installed the stable when I first installed Edgy Eft in November; I think it was my attempt to use Envy to fix the problem I'm having that gave me that beta.

I have now uninstalled the beta totally and reinstalled. I'm back to  1.0-8776, and I have the same symptoms as before. It had to be done, and I thank you for pointing it out, but no net progress.

---

### Post by Sammi on 2007-02-05
Actually I am running the beta drivers, which I installed using Envy :D

Just thought that you should at least see if the stable ones gave different results.

---

### Post by psantucc on 2007-02-06
> **conjur3r said:**
> How long ago did you last install your nvidia drivers?  Some updates overwrite (or remove) the nvidia kernel object which requires you to reinstall them.  This may not be the case here though, as you can still run 3d accelerated programs.  But it doesn't hurt to try?

Try running **top** in the background next time you run those games that do not work properly.  When a spike occurs, glance over to top to see if anything caused it.

Well, here's an interesting thing...

When I ran top, I noticed that a zombie Tremulous server was taking up about 50% CPU. To get a clean test, I killed it.

Since then, I"ve had no 3d problems.

Now, I had the problem before I ran Tremulous for the first time, and that zombie survived at least 3 shutdowns... so I think there's a mystery here that I will never solve. For now, though,  I can play!

Thanks for the help, all.

---

