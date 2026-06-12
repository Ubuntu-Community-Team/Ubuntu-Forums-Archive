---
title: "[SOLVED] m1330 kernel panics on attempt to resume from acpi suspend?"
date: 2008-12-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Zaventh on 2008-12-09
=== 
Originally posted in the general Hardware / Laptop forums. Didn't see this Dell specific one. No replies and couldn't figure out how to delete original. ^_^ 
===

Hello,

I am have a (slightly) unusual problem with suspend mode and my Dell M1330. I have read many posts from many forums and while it seems most people are able to get suspend (to RAM) working at least 3/4 times, I cannot get it to work at all. The peculiarity of my problem is that when I attempt to resume from RAM-suspend, absolutely nothing happens. The machine is completely unresponsive in all respects (even cap locks, etc doesn't work) and no logs are generated.

I am running Intrepid and have a the latest proprietary nvida driver. I have tried extensive permutations of editing the /etc/defaults/acpi-support file, including the recommended nvidia settings. I've also setting SUSPEND_METHODS to just "acpi-support", but no change. I've tried adding a quirk as suggested somewhere on here to /usr/share/hal/fdi/information/10freedesktop, but with no effect as well.

I suspect this behavior may be due to a kernel panic on resume... but it seems like this would at least be logged somewhere.

Any ideas are welcome at this point... thanks.


==== EDIT ====
Solved by downgrading to Hardy ^_^

---

