---
title: "Permission denied error with &quot;resume-trace&quot; debugging procedure"
date: 2016-10-01
forum: Desktop Environments
---

### Post by arto-o-makkonen on 2016-10-01
I've reported a Launchpad bug about suspend-resume problems, and I'm trying to run the "resume-trace" debugging procedure for finding buggy drivers following the instructions in [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend) 

Tracing will not work because of this permission denied error

$ sudo sh -c "sync && echo 1 > /sys/power/pm_trace && pm-suspend"
sh: 1: cannot create /sys/power/pm_trace: Permission denied


Haven't received any help from the launchpad team to my bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1618550](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1618550) but maybe there's someone here familiar with Ubuntu who can help?

---

