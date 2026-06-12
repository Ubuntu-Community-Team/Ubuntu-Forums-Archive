---
title: "Monitor sleeps when gnome starts with free ati driver"
date: 2009-01-06
forum: General Help
---

### Post by boombox1387 on 2009-01-06
Here's the situation:

I start up my computer.  Ubuntu loads and I can see the usplash as expected.  When X/Gnome starts to load, the screen goes black and then goes to sleep.  Moving the mouse and typing don't wake it up (the computer isn't asleep, just the monitor).

As a temporary fix, I changed the xorg.conf to use the failsafe graphics.  This works fine, but is ugly like nobody's business.  Previous to this problem I had been using the free ati driver with a Radeon X1300 graphics card on Ubuntu 8.10.

I recently got a bunch of updates, and I think some of them were video driver updates.  I don't know if this caused the problem, but I was wondering if anyone else is having any problems or if anyone can suggest a fix.  Thanks in advance for the help.

---

### Post by kixome on 2009-01-06
install the proprietary drivers.

The envy drivers work great.

---

### Post by boombox1387 on 2009-01-07
I'd really rather not.  The free driver supports full 3d with my card.  Actually, compositing was running quite a bit smoother with the free driver when EXA was enabled.

Anyway, I may settle for the proprietary driver if I can't get anything else to work.

---

### Post by boombox1387 on 2009-03-17
Just as an update on the situation, based on things that I've learned since my original post, in case anyone with a similar problem stumbles upon this thread:

I installed Intrepid at the Release Candidate stage.  At that point, ATI hadn't released drivers that were compatible with the latest version of X.Org, which was used in 8.10.  Since fglrx (the proprietary drivers) were incompatible, the Intrepid RC only gave the option for the free drivers, which worked surprisingly well with Compiz.

Sometime right around the beginning of 2009, an update to the free driver (xserver-xorg-video-ati) was released through Ubuntu's update manager.  Installing this update caused video to break when the X session loaded with my Radeon X1300 graphics card.  At that time, I had no choice but to switch to the proprietary drivers, because I didn't (and still don't) know how to roll back a problematic update in Ubuntu.

Since this whole fiasco, I reinstalled Ubuntu (in February).  I found out that even with a fresh install + updates, my computer boots with a sleeping monitor.  My best workaround so far has been to do a clean install and immediately lock the xserver-xorg-video-ati package at the current version, before installing any updates.

Hopefully all of this will be a moot point when Jaunty comes out in ~ 1 month.

---

