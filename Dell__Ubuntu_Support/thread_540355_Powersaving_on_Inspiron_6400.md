---
title: "Powersaving on Inspiron 6400"
date: 2007-09-01
forum: Dell  Ubuntu Support
---

### Post by misos on 2007-09-01
I'm running Feisty Fawn with kernel 2.6.22 from Gutsy on my Inspiron 6400. In my powetop log, the power consumption is around 25W when idle, and I get at least 160 wakeups from idle. The batery lasts about 2 hours, 1-2 hours less than in Windows XP.

In the logs I found that the PS/2 keyboard/mouse/touchpad is responsible for most of the wakeups (> 50%). It seems that the touchpad driver is making them, but I couldnt find a way to minimise it. 

Any ideas?

---

