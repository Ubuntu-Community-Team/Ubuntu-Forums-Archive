---
title: "Sometimes windows don't refresh"
date: 2009-05-06
forum: Desktop Environments
---

### Post by dargaud on 2009-05-06
Hello all,
I have a strange problem since the 9.04 upgrade (kubuntu): sometimes (actually quite often), a window will not refresh its content. If I change its width/height, some times it will start working again at this stage, other times not. 

The mouse will change to the appropriate shapes when I mouseover what _should_ be on the window, just to say that the content is there, simply not visible. Sometimes the old content stays, sometimes I get a blank page.

It happens with firefox, VirtualBox, Dolphin, Kuickshow... Very annoying.

---

### Post by conxorxa on 2009-05-29
*bump*.  I have the same problem.  Any solutions?

---

### Post by dargaud on 2009-06-02
It apparently has to do with kde4 compositing, but I&#7743; not sure what it is or how to disable it. Anyway, things have gotten better with the latest fixes, although I still have it on some Wine apps.

---

### Post by HDave on 2009-11-10
I have this on 9.10....anybody solve it?

---

### Post by Metrol on 2009-11-19
This was a serious problem for me on Kubuntu 9.04, but only on my desktop machine.  My laptop never seemed to have this problem.  Upgrading to 9.10 fixed a lot of it, but it's still happening.

My desktop is running dual screen with the nVidia drivers.  It's also running 64-bit.

My laptop is running 32-bit, obviously a single screen, and also the nVidia drivers.  With compositing and all that it works just fine.

I recently installed Ubuntu 9.10 64-bit on my desktop.  It worked pretty well with compositing for a couple of days, then Firefox started having this window refresh problem.  I'm also starting to see this problem show up with other applications as well.  Seems it's not just a KDE issue.

Since Gnome seems to be having similar problems, and annoying little glitches I can't quite seem to live with (Move app to desktop broken, alt-rmb resize inop, etc...) I'm going to try a fresh install of Kubuntu 9.10 32-bit and see if that's the problem.

I really don't want to be running 32-bit since everything else runs sweet as 64-bit except for this darn window refresh problem.  Sigh.

---

### Post by rockdj on 2010-01-03
> **Metrol said:**
> Since Gnome seems to be having similar problems

I'm running 32-bit 9.10 Ubuntu and have had what seems to be the same issue for as long as I can remember using Ubuntu (since 8.04?).  

Essentially, things will work fine for the most part but some large windows (I like to have Firefox near on full screen) won't refresh until their size is brought back to about half the screen height.  Then, once it does start working again, the window continues to work fine; eg this window I'm typing in now 'glitched' and has been resized down and is now working again.  If I was to up the size again over what seems to be the half-screen height, it would stop working again.  Seems to just happen very intermittently -- some days it won't be a problem but just happened now.

It's a dual-screen setup, with Compiz enabled and working (seemingly) fine with Nvidia 190.42 drivers.

---

### Post by meyerm on 2010-12-24
Any new hints until now? I just experienced the same problems.

---

### Post by Al_Berto on 2011-01-24
For me it was fixed by switching from trilinear to bilinear texture filtering.

---

