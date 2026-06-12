---
title: "Uninstalling driver from command line"
date: 2009-06-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by worm94 on 2009-06-18
Hi, I recently updated the driver for my graphics card and now I can't log into my system, when it should show the login screen, instead it shows a black screen with some weird color patterns... I've already tried reverting xorg.conf to an old date backup, but it did't work, so now I'm wondering if there's any way to undo that last update or going back to the driver I was using before the update or something in those lines... thanks in advance.

---

### Post by Amilo1718 on 2009-06-18
did you use a restricted river?

---

### Post by worm94 on 2009-06-18
I think so... it was the driver for my Ati Radeon Xpress 1150

---

### Post by worm94 on 2009-06-19
I ended up backing my files using Live CD and made a clean install... I suppose that means this thread is closed :P

---

### Post by InlawBiker on 2009-06-19
I suppose that would work, but next time you can boot to command line and run aptitude.  It's a menu-driven package manager that works very well, once you get used to the key commands.

---

### Post by ugm6hr on 2009-06-19
> **worm94 said:**
> I think so... it was the driver for my Ati Radeon Xpress 1150

9.04 does not support restricted drivers for a lot of ATI cards; hence the problem.

This is due to lack of ATI support.

---

