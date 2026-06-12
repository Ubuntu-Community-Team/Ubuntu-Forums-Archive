---
title: "Excessive cpu usage with Core2 duo on Hardy"
date: 2008-08-30
forum: Desktop Environments
---

### Post by LordPi on 2008-08-30
Ok, so I run a program with wine(Dwarf Fortress), and I see that it is not running faster than on my laptop, which is running vista, and simply should not be as powerful as the desktop I just put a new motherboard, a 3.0 Ghz e8400 Core 2 duo processor and 2Gb of RAM in. System monitor tells me that I have 100% cpu usage on one core, and as I watch, it switches to the other core, leaving the first one at around 8%

It also says that no process is taking that much. With my game paused, I look at top, which shows xorg taking up 100% cpu, and my game taking 10% Anyway, I noticed that as soon as I quit the game, all cpu usage went to normal levels. I thought at first(when I started typing, before I quit DF) that it was a xorg issue, but now it seems more like a wine issue. Quick google search reveals only that the hardy kernel should be equipped to deal with core 2 duo processors.
What gives? Is it likely that swiping DLLs from one of the windows install I have kicking around will help?

---

### Post by LordPi on 2008-08-30
I got it solved. I needed to install the drivers for my nvidia card. software rendering sux.

---

