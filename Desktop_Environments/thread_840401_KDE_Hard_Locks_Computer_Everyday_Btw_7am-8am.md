---
title: "KDE Hard Locks Computer Everyday Btw 7am-8am"
date: 2008-06-25
forum: Desktop Environments
---

### Post by eleqtriq on 2008-06-25
I've been dealing with this for sometime now, trying to figure it out.

Every morning, around 7:20am (but always between 7 and 8), my computer will hard lock.  No KB, Mouse, nothing.  The screen is stuck at whatever it was showing last.

I've logged out of KDE, either back to console or KDM, and the computer won't lockup.  I've gone a week vacation and it didn't lock up.  But if KDE is on, even with all the apps closed, it locks every day.

Anyone have any idea?

BTW, this problem followed me from my old computer to my new one.  Complete, total hardware swap.  Only thing that came over was my /home/eleqtriq directory.  I was/am running Hardy on both.

Please help.

---

### Post by chandra on 2008-06-25
> **eleqtriq said:**
> 
BTW, this problem followed me from my old computer to my new one.  Complete, total hardware swap.  Only thing that came over was my /home/eleqtriq directory.  I was/am running Hardy on both.

This suggests some configuration file in your home directory under ~/.kde.

FWIW, one way to test this is to move ~/.kde to ~/.kde_old and login again to create a new ~/.kde directory and see if the problem disappears.

The flip side is that you lose all your customized settings for a short period. Once you have verified whether or not something in ~/.kde is the cause, you can either revert to your old settings en bloc by renaming ~/.kde_old to ~/.kde or you could revert to it incrementally by adding files and directories one at a time, to trap the settings causing this behaviour.

HTH.

Chandra

---

