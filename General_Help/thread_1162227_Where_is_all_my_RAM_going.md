---
title: "Where is all my RAM going?"
date: 2009-05-17
forum: General Help
---

### Post by rexeast on 2009-05-17
I have 512 MB of RAM on my Ubuntu virtual private server, and only 80 MB free. I can't figure out why this is. ```
ps faux
``` and ```
top
``` don't show any programs using a lot of memory; the highest is mysql with 1.5 %MEM. Up until a few days ago, I had at least 400 MB to work with, and I don't think I'm doing anything different.

Any ideas from the community on how to debug this?

---

### Post by s.fox on 2009-05-17
Hi,

Have you tried:

```
/proc/meminfo
```

Could you post the output please?

Thanks,

-Ash R

---

### Post by rexeast on 2009-05-17
Hi Ash,

Thanks for the reply. I just rebooted my machine, and now have 382 MB free. I'll post again if this becomes a problem.

---

### Post by rexeast on 2009-05-24
OK, the problem has reoccurred, and I have to admit I am frustrated, since I'm getting seemingly different readings from different places. I am hoping an expert can clue me in on what is happening.

Here is my /proc/meminfo:

```
MemTotal:       524508 kB
MemFree:        119544 kB
Buffers:         47628 kB
Cached:         252012 kB
SwapCached:          0 kB
Active:         169668 kB
Inactive:       154032 kB
SwapTotal:     1048568 kB
SwapFree:      1048568 kB
Dirty:              24 kB
Writeback:           0 kB
AnonPages:       24176 kB
Mapped:           5840 kB
Slab:            54164 kB
SReclaimable:    41520 kB
SUnreclaim:      12644 kB
PageTables:       1828 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   1310820 kB
Committed_AS:    35832 kB
VmallocTotal: 34359738367 kB
VmallocUsed:       708 kB
VmallocChunk: 34359737659 kB

```However, Webmin tells me that I have around 400 MB free! To add to my confusion, the "size" column doesn't seem to match up with either of these figures -- is the below saying that I have 6 processes that are each consuming around 70 MB of RAM? If you add up the below processes, they total over 512 MB RAM, so this doesn't make sense to me. Is kB supposed to mean KBits?

[IMG]http://dl.getdropbox.com/u/302783/Webmin.PNG[/IMG] 
When I try to track down the application that is taking up all my memory, I don't know what to make of the output of "ps faux". Which columns here are significant? I would assume "%MEM", but that's not giving me much to go on.

```

root@slice31364:/proc# ps faux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
[..... a bunch of processes]
root         1  0.0  0.1   3984   844 ?        Ss   May17   0:02 /sbin/init
root      2272  0.0  0.2  17164  1264 ?        S<s  May17   0:46 /sbin/udevd --daemon
syslog    3719  0.0  0.1  12296   752 ?        Ss   May17   0:25 /sbin/syslogd -u syslog
root      3768  0.0  0.1   8132   588 ?        S    May17   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      3771  0.0  0.4   5620  2272 ?        Ss   May17   0:00 /sbin/klogd -P /var/run/klogd/kmsg
root      3795  0.0  0.2  50916  1164 ?        Ss   May17   0:23 /usr/sbin/sshd
root     30638  0.0  0.5  67972  2764 ?        Ss   May23   0:00  \_ sshd: chris [priv]
chris    30641  0.0  0.3  68264  1736 ?        S    May23   0:01  |   \_ sshd: chris@notty
chris    30643  0.0  0.3  39852  1804 ?        Ss   May23   0:02  |       \_ /usr/lib/openssh/sftp-server
root     30703  0.0  0.5  67972  2908 ?        Ss   May23   0:00  \_ sshd: chris [priv]
chris    30707  0.0  0.3  68108  1860 ?        S    May23   0:00      \_ sshd: chris@pts/0
chris    30709  0.0  0.4  18132  2168 pts/0    Ss   May23   0:00          \_ -bash
root     10954  0.0  0.2  31260  1160 pts/0    S    04:24   0:00              \_ su
root     10955  0.0  0.3  17616  1872 pts/0    S    04:24   0:00                  \_ bash
root     11802  0.0  0.1  14780   996 pts/0    R+   04:56   0:00                      \_ ps faux
root      4081  0.0  0.4  36684  2128 ?        Ss   May17   0:18 /usr/lib/postfix/master
postfix   4133  0.0  0.3  38784  2088 ?        S    May17   0:01  \_ qmgr -l -t fifo -u
postfix  10359  0.0  0.3  38740  2044 ?        S    03:52   0:00  \_ pickup -l -t fifo -u -c
root     10463  0.0  0.5  43404  3024 ?        S    04:04   0:00  \_ smtpd -n smtp -t inet -u -c -o stress
postfix  10464  0.0  0.3  38740  2064 ?        S    04:04   0:00  \_ proxymap -t unix -u
root      4158  0.0  0.1  18616   972 ?        Ss   May17   0:04 /usr/sbin/cron
root      4264  0.0  0.1   3864   584 tty1     Ss+  May17   0:00 /sbin/getty 38400 tty1
root      9267  0.0  2.9  73368 15368 ?        Ss   03:02   0:01 /usr/bin/perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf

```To my non-expert eyes, the output of "top" is equally nondescript about which programs are hogging memory:

```
Tasks:  65 total,   1 running,  64 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni, 96.7%id,  0.0%wa,  0.0%hi,  0.0%si,  3.3%st
Mem:    524508k total,   404980k used,   119528k free,    47628k buffers
Swap:  1048568k total,        0k used,  1048568k free,   252032k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
   39 root      15  -5     0    0    0 S    0  0.0   1:03.55 events/3
    1 root      20   0  3984  844  592 S    0  0.2   0:02.98 init
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.54 migration/0
    4 root      15  -5     0    0    0 S    0  0.0   0:00.30 ksoftirqd/0
    5 root      RT  -5     0    0    0 S    0  0.0   0:02.68 watchdog/0
    6 root      15  -5     0    0    0 S    0  0.0   1:04.86 events/0
    7 root      15  -5     0    0    0 S    0  0.0   0:00.02 khelper
   18 root      15  -5     0    0    0 S    0  0.0   0:00.00 xenwatch
   19 root      15  -5     0    0    0 S    0  0.0   0:00.00 xenbus
   28 root      RT  -5     0    0    0 S    0  0.0   0:00.14 migration/1
   29 root      15  -5     0    0    0 S    0  0.0   0:00.12 ksoftirqd/1
   30 root      RT  -5     0    0    0 S    0  0.0   0:02.56 watchdog/1
   31 root      15  -5     0    0    0 S    0  0.0   0:59.29 events/1
[..... a bunch more]

```Can someone give me some help so I can figure out what is going on?

---

### Post by ramjet_1953 on 2009-05-24
All that is happening is that Ubuntu is using spare RAM for cache.
This is perfectly normal and speeds disk transfer up.
Ubuntu coders have the correct attitude that unused RAM is useless.

Regards,
Roger :D

---

### Post by mcduck on 2009-05-24
Forget trying to find what's using the RAM, the above poster is correct, all your RAM that is not used by programs is used for buffers and cache for recently accessed data. The part of RAM that is used for cache still counts as available for programs as they can use it any time they need. Some system monitor programs count it as free, some as used.

To get proper view of your memory usage run "free -m" in a terminal, and look at the "-/+ buffers/cache"-line. This tells you how much memory your programs are using, and how much is still available for them.

---

