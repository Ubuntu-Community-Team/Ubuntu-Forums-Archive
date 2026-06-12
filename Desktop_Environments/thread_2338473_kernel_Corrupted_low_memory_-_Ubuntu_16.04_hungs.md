---
title: "kernel: Corrupted low memory - Ubuntu 16.04 hungs"
date: 2016-09-28
forum: Desktop Environments
---

### Post by anthonywc on 2016-09-28
I have ran into this bug that has been around for awhile [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/324894](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/324894) from checking my log and I think it may possibly have caused my laptop to hang twice.

```
 
Sep 28 11:16:06 alto kernel: [425113.621296] Corrupted low memory at ffff880000003000 (3000 phys) = 007a26a6
Sep 28 12:04:06 alto kernel: [427993.705933] Corrupted low memory at ffff880000003000 (3000 phys) = 007a8a7a
Sep 28 13:03:07 alto kernel: [431533.912246] Corrupted low memory at ffff880000003000 (3000 phys) = 007b0e8b
Sep 28 13:06:17 alto systemd[1]: Started CUPS Scheduler.
Sep 28 13:17:01 alto CRON[8715]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 28 13:28:07 alto kernel: [433033.990343] Corrupted low memory at ffff880000003000 (3000 phys) = 007b56ca  
```

---

