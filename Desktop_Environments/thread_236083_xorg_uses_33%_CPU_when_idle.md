---
title: "xorg uses 33% CPU when idle"
date: 2006-08-14
forum: Desktop Environments
---

### Post by tschaboo on 2006-08-14
I've found some threads about unusual high CPU-usage but all of them were about problems with the -686-kernel and/or speedstep. I'm running a -k7-kernel and I have the problem with the high usage since installing Dapper. In Breezy everything works fine (0-2% usage when idle). My CPU is an AhtlonXP 2000+, 1GB of RAM.

```
root@dapper:~# uname -srv
Linux 2.6.15-26-k7 #1 SMP PREEMPT Thu Aug 3 03:40:32 UTC 2006

```

```
root@dapper:~# top

top - 13:29:49 **up  2:11**,  8 users,  load average: 0.70, 1.13, 1.00
Tasks: 117 total,   1 running, 115 sleeping,   0 stopped,   1 zombie
Cpu(s): 31.9% us,  2.0% sy,  0.0% ni, 65.1% id,  0.3% wa,  0.3% hi,  0.3% si
Mem:   1034652k total,  1019004k used,    15648k free,   132992k buffers
Swap:        0k total,        0k used,        0k free,   583456k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4532 root      16   0 64372  45m  10m S **32.2  4.5  42:39.28 Xorg**
 5342 tschaboo  15   0 36788  14m 9984 S  1.3  1.4   1:29.22 gnome-system-mo
 5548 tschaboo  15   0 55992 9308 5208 S  0.7  0.9   0:23.16 xmms
 2105 root      16   0     0    0    0 S  0.3  0.0   0:15.01 kjournald
 9190 root      16   0  2196 1124  856 R  0.3  0.1   0:00.04 top
    1 root      16   0  1564  528  460 S  0.0  0.1   0:01.16 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.05 events/0
    6 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread

```

You can see that Xorg consumed 42,65 minutes CPU-time and the uptime is 131 minutes!

---

