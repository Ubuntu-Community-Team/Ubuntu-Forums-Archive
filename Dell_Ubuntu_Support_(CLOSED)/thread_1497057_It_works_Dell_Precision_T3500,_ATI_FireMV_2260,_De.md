---
title: "It works: Dell Precision T3500, ATI FireMV 2260, Dell 3008WFP 30inch monitor, Lucid L"
date: 2010-05-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mwang25 on 2010-05-30
Hi,

Just wanted to post a working config in case there are people out there thinking about buying this config and wondering if it will work:

Dell Precision T3500
Dual Core Xeon W3503 2.4GHz, (32 bit)
4GB 1066MHz DDR3
256MB ATI FireMV 2260, 2 Display port connectors only
(Purchased around March 2010)

Dell 3008WFP 30inch 2560x1600 LCD monitor (purchased around June 2009)

Ubuntu 10.04 Lucid Lynx (upgrade from 9.10). I am using the opensource driver that came with Ubuntu. I did not select the use proprietary driver option.

Also works, Dell 2407WPF LCD monitor using a Display port to DVI dongle.

More details at mwang25.blogspot.com

---

### Post by mwang25 on 2010-08-29
Well, maybe I spoke a little too soon.  After using this config for a few weeks, I've noticed two problems:
1. This happens about once every 2-3 days.  The screen gets very fuzzy.  All the letters in the windows are blurry.  Restarting the x server seems to fix the problem, but I lose all of my sessions.  One time, I actually saw the problem go away by itself.  Seems to have something to do with the screen coming out of power save mode.

2. This happens more rarely, maybe once every 2 weeks.  The whole screen goes blank, with about 5 equally spaced vertical orange lines coming down on the screen.  There is no way to recover from it other than rebooting, and sometimes, the entire system locks up so I cannot ssh into the system and reboot.  Must pull the power plug.

I have not updated the packages, don't know if this is already fixed or not.  Does anyone else have similar experience?  (This is with the opensource driver, not the proprietary driver.)

Oh, but I do love the 30" screen.  Makes working in Eclipse and everything else soooo nice.  Far outweighs the minor inconvenience of these small bugs.

---

