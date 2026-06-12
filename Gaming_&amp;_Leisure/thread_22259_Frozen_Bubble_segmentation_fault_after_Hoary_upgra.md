---
title: "Frozen Bubble segmentation fault after Hoary upgrade"
date: 2005-03-26
forum: Gaming &amp; Leisure
---

### Post by calvinpriest on 2005-03-26
I can't play Frozen Bubble after dist-upgrade to Hoary.  If I run from a shell I see the error "segmentation fault".  I tried removing and reinstalling, for what that's worth.

I'm starting to go through withdrawals.  Anyone know what's going on?

---

### Post by calvinpriest on 2005-03-27
Ok, I'm also getting segfaults in Tuxracer and Chromium.

I can however run Wesnoth fine.  Also all the gnome games seem fine.

I've tried reinstall various packages without luck.

Thoughts anyone?

---

### Post by mglukhovsky on 2005-03-27
Maybe in the upgrade from Warty->Hoary, and subsequently from XFree86->Xorg, the drivers for your OpenGL compatibile card didn't carry over. What card do you have? Perhaps you ought to read some of the howtos, reinstall the drivers for the appropriate windowing system (i.e. there is a Xorg-specific and XFree86-specific package for ATI cards on one of the repositories.) The thing I'd suspect most would be your Xorg configuration file- read some other related threads and see if this may be the issue.

---

