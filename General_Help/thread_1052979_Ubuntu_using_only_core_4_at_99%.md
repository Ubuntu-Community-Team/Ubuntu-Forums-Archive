---
title: "Ubuntu using only core 4 at 99%"
date: 2009-01-28
forum: General Help
---

### Post by rhardie on 2009-01-28
I seeing that Ubuntu is maxed out at 98.9% on core 4 of my system for a long time.  I began to notice this when my flash wasn't playing or plays very, very slowly on my Firefox.  The system temporarily balances between all 4 cores, then goes back to core #4.  Any way to resolve this?

System:
AMD 9500 Quad Core (64 Bit)
Memory 3 GB
Ubuntu 8.10 (32 Bit) with latest updates
Gnome 2.24.1

Processes:
No single process appears to be above 2 - 6% CPU utilization

Applications Running:

Evolution
Firefox
System Monitor

---

### Post by Nepherte on 2009-01-28
That's because flahs only uses one thread. You can't divide the work of 1 thread over several cores. There's nothing you can do about that. In this case, the flash thread is crashing which explains the 100% on one core.

---

### Post by rhardie on 2009-01-28
That would be consistent with my observations.  Now, I must find a solution to my crashing Flash.  I can't seem to view my favorite web pages and Firefox is so slow that I want to eat nails.

Thanks for your response.

---

