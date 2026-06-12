---
title: "gdl_indexer problem?"
date: 2009-04-27
forum: General Help
---

### Post by MikeB007 on 2009-04-27
I upgraded 8.10=>9.04 yesterday.  There appeared to be no problems and I used the laptop happily for several hours.

Today I booted up and shortly after the cpu fan came on and stayed on.  Also, some screen refreshes, window openings, etc. started to lag.  It turned out the CPU was running at 100%.  The process responsible was gdl_indexer which was using ~90% of the CPU  HOWEVER there were two gdl_indexer processes indicated in sys monitor: one was 'sleeping' (expected) and the other was 'running' (~90% CPU) with 'Wait Channel'=0.  I was only able to stop the running process by using 'kill'.  I have since rebooted a few times and the behaviour is the same.

Any thoughts or insight would be appreciated.  Cheers.

---

### Post by slamen on 2009-06-29
Do you use Google Desktop Search?
If so, try to stop indexation...

---

