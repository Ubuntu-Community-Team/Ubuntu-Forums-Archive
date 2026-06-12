---
title: "[SOLVED] Nvidia slows 2d render and uses high CPU when moving/resizing windows - meta"
date: 2008-10-24
forum: Desktop Environments
---

### Post by vprasaj on 2008-10-24
Like described in title.

I love GNOME. But this is annoying. Every time I move window any window, CPU jumps like 30%-70%. Move is visually sluggish.

Today I tryed pclos gnome. The same thing like in ubuntu. Strange is that until generic driver was in use, everything was fine. After I installed VGA driver (tryed last two - gnome - ubuntu and pclos), this problem occurs. 3D works fine, but 2D is really slow (compared to xfce, kwin, even ms systems). Not just firefox.

Is this GNOME or nvidia problem? 

Is there any fix/tune/settings?

---

### Post by vprasaj on 2008-10-25
Bump? Anyone?

---

### Post by vprasaj on 2008-10-27
Bump...

---

### Post by vprasaj on 2008-10-29
Bump.

Well, I saw many complains on net for this but no solutions/workaround.

Anyone? Maybe explanation?

---

### Post by jbysmith on 2008-10-29
Are you using the default open source drivers, or the ones from nVidia?  I'm using the 178.80's straight from the nVidia site, and they're actually running *very* well versus the previous versions, at least on my older hardware. (AMD Athlon XP system with a AGP 7800GS OC) 

Might want to hop over to nvnews.net too, they have a forum specifically for Linux and nVidia drivers; found a few good tips there for optimizing the performance of the driver, one of which was blacklisting the default GART driver and forcing the kernel to use the nVidia specific one.  My board is nForce2 based, and the current drivers work better that way.

Direct link to that forum is [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by megabytemonster on 2008-10-29
It could be related to the same issue KDE4 has. The properietry driver for Nvidia apparently causes slow 2D performance because of issues with the Xrender API. 

Apparently the very latest version ( 177.8 ) corrects this issue. In the changelog:

* Improved GPU video memory management coordination between the
NVIDIA X driver and OpenGL implementation; this should
improve performance with e.g. the KDE4 OpenGL compositing
manager.

Intrepid has version 177, though not sure if that means 177.8.

---

### Post by vprasaj on 2008-11-02
Sorry for my extremely "quick" replay. I was away...etc.

I used EnvyNG for drivers and those in the list are older versions. (BTW: EnvyNG is great program.)

I have just installed version 177.8 with nvidia installer. Well, its like day and night.

Now it runs much, much better. This was a driver problem. There is still some lag from time to time (after reorder a couple windows in a row or at rapid movement), but I can live with that.

**Thank you jbysmith, thank you megabytemonster. Thank you for the tips.**:D

Now I know that lag in metacity is caused by drivers. But those are getting better.

This thread is solved.

Thanx again guys.

---

### Post by vprasaj on 2008-11-13
Just update. This thing completely disappears with NVIDIA-Linux-x86-177.82 driver.

OK, firefox is still a little sluggish (but scroll is great), but most of other things works just fine. :)

---

