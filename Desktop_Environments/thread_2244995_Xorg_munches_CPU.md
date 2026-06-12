---
title: "Xorg munches CPU"
date: 2014-09-20
forum: Desktop Environments
---

### Post by Lars Noodén on 2014-09-20
Xorg is really hungry for CPU and uses between 30% and 50% even when I'm not really doing anything on the desktop.

```

top - 15:21:41 up 8 days,  1:06,  3 users,  load average: 0,83, 0,58, 0,47
Tasks: 275 total,   2 running, 271 sleeping,   2 stopped,   0 zombie
%Cpu(s):  8,7 us,  0,8 sy,  0,0 ni, 90,5 id,  0,0 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem:   8095112 total,  7637516 used,   457596 free,   146100 buffers
KiB Swap:  8305660 total,   207268 used,  8098392 free.  4300632 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 1233 root      20   0  828372 236676 155028 S  50,6  2,9   1409:20 Xorg       

```

What can be done to calm it down?

---

