---
title: "Why is kded using all my CPU?"
date: 2006-09-09
forum: Desktop Environments
---

### Post by Junx on 2006-09-09
Seriously, this is getting to be quite bad.  According to top, I have two instances of kded running with a combined total of ~34 _hours_ of CPU time (current uptime is about 36 hours to put into perspective).

I'm using Kubuntu with the 3.5.4 packages.  I already know about the KNemo issue, so I don't use that anymore, but kded is back with the resource hogging and battery depletion once again.

So, my question: see thread title.

---

### Post by rhk on 2006-11-16
> **Junx said:**
> Seriously, this is getting to be quite bad.  According to top, I have two instances of kded running with a combined total of ~34 _hours_ of CPU time (current uptime is about 36 hours to put into perspective).


Same here. Yesterday (after I installed ubuntu-desktop - previously I only had kubuntu Edgy w. KDE 3.5.5. I don't know it this matters..) KDE started to act really slow and I found kded - that earlier has not been visible as 'resource eater' on top.

```
rhk@ribantu:~$ top
top - 10:14:54 up 14:32,  3 users,  load average: 5.05, 4.89, 4.86
Tasks: 120 total,   6 running, 114 sleeping,   0 stopped,   0 zombie
Cpu(s): 98.0%us,  0.7%sy,  1.3%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    775580k total,   741864k used,    33716k free,    74788k buffers
Swap:  3140648k total,    17668k used,  3122980k free,   311800k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6944 rhk       25   0 32360  16m  13m R 31.9  2.2 290:41.72 kded
19657 root      23   0 18368  13m  11m R 30.9  1.8   0:02.04 apt-index-watch
 8202 rhk       25   0 32352  16m  13m R 29.9  2.2 279:16.96 kded
10652 rhk       15   0  197m  70m  24m R  6.0  9.3  24:50.84 swiftfox-bin
 4802 root      39  19 11696 5084 1384 R  1.3  0.7  50:36.06 FahCore_78.exe
19658 rhk       16   0  2244 1140  840 R  0.3  0.1   0:00.03 top
    1 root      16   0  1632  600  516 S  0.0  0.1   0:01.80 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:07.06 events/0
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.20 kblockd/0
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   11 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify
   73 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
rhk@ribantu:~$

```

Anyone? What is kded, why it is eating all CPU resources and why it's been quiet for a long time but now suddenly appeared..?



r

---

### Post by rhk on 2006-11-16
There has been similar symptons (google told me that..) every year at least since 2002.. 

Some reps about this:
[http://bugs.kde.org/show_bug.cgi?id=108210](http://bugs.kde.org/show_bug.cgi?id=108210)
[http://lists.suse.com/archive/suse-kde/2006-Oct/0031.html](http://lists.suse.com/archive/suse-kde/2006-Oct/0031.html) (have to check if it's the kwallet)
[http://www.mail-archive.com/debian-kde@lists.debian.org/msg26060.html](http://www.mail-archive.com/debian-kde@lists.debian.org/msg26060.html)

r

---

### Post by ingo on 2006-11-23
Yeah, same happened to me just now (kubuntu 6.10). CPU temperature was going up like you wouldn't believe. killed kded but then all kwallet functions were lost. Simply restarting x won't do, a complete reboot was necessary! 

Thank heavens it has finished...

---

### Post by syväpaahto on 2007-01-14
Just a little afterthought to this subject. How many of you with kded problems have wine installed? How many of you have a link in dosdevices that point to your home folder where .wine/dosdevices resides. Could this loop cause the kded to hang. 

Just a thought that came when I tried to copy .wine folder

---

### Post by ingo on 2007-01-15
I haven't experienced the problem since. To answer your questions:

Yes, I have wine installed.

No, there is no loop.

---

