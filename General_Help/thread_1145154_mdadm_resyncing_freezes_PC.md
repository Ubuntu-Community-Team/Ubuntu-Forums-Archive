---
title: "mdadm resyncing freezes PC"
date: 2009-05-01
forum: General Help
---

### Post by canadian-joe on 2009-05-01
Hi everyone,

I got a VIA EPIA EX 1500G with 1GB RAM and 3 HDDs (1x 80GB for Ubuntu and 2x 1TB just for data/media). I would like to use it as a server and media center, so I would like to use the two 1TB HDDs as Raid1 with mdadm. Making it work is not the problem, but once it is running and resyncing the drives, the computer freezes, this can happen after a few minutes but it can also run without problems for up to 3 hours. The main problem is, that the resyncing process at least take 4 hours, so this has never been finished and starts all over again once I turn the computer back on.
I also tried ```
echo 20000 >/proc/sys/dev/raid/speed_limit_max
``` 
but it still keeps freezing. This also occurs when the PC chassis is opened, but I also did not think that it would be too hot in there, since its a pretty big chassis with some fans in it.
During the resyncing process the load average is always pretty high, something between 1.1 and 1.5, while it is below 0.4 when not resyncing and no raid configured. Could this be the problem?
Here is the top screen when it froze the last time:
```
top - 18:31:37 up  1:20,  2 users,  load average: 1.49, 1.21, 1.11
Tasks: 115 total,   3 running, 112 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.7%us,  4.3%sy,  0.0%ni, 90.7%id,  0.0%wa,  0.0%hi,  4.3%si,  0.0%st
Mem:    896300k total,   200948k used,   695352k free,     1492k buffers
Swap:  2931820k total,        0k used,  2931820k free,    37276k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 3537 root      15  -5     0    0    0 R  3.0  0.0   2:28.47 md0_resync
 3533 root      15  -5     0    0    0 S  1.0  0.0   1:00.98 md0_raid1
    4 root      15  -5     0    0    0 S  0.3  0.0   0:00.78 ksoftirqd/0
 2458 haldaemo  20   0  6696 2568 1772 S  0.3  0.3   0:10.17 hald
 3327 hk        20   0  7916 3100 2376 S  0.3  0.3   0:02.76 gvfs-hal-volume
 3353 hk        20   0  8644 1608 1004 S  0.3  0.2   0:04.93 sshd
 4688 hk        20   0  2448 1184  912 R  0.3  0.1   0:16.62 top
    1 root      20   0  3084 1888  564 S  0.0  0.2   0:02.13 init
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.58 events/0
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0
   10 root      15  -5     0    0    0 R  0.0  0.0   0:00.27 kblockd/0
   11 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
```

The PC freezes under Ubuntu 9.04, Xubuntu 9.04 and Ubuntu Server 8.10, which is clear since I am using the same version of mdadm, but on Ubuntu Server 8.10 I always get a Bad EIP Value and therefore Kernel Panic - not syncing: Attempted to kill the idle task! have a look at the attachment for more information about that, theres a photo of the screen.

So I don't know what else I should do or try, since I do not think that this Computer will once be running long enough to finish the resyncing process. Decreasing the resyncing speed did not work and did not reduce the load average. 
Without the mdadm and with one 1TB HDD mounted (too lazy to mount the other one) the PC ran immediately about 4 hours.
So I got no idea what else to try or do, hope somebody here can help me any further.

Thanks and greets,
Andi

---

