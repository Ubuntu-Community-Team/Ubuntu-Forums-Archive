---
title: "Load Average Very High"
date: 2006-09-03
forum: Desktop Environments
---

### Post by the_0ne on 2006-09-03
I saw this post...

[http://www.ubuntuforums.org/showthread.php?t=208517](http://www.ubuntuforums.org/showthread.php?t=208517)

One of the repliers links to a bug report which they seem to say is fixed with a new kernel update.  That update was supposed to be in July 2006, which of course we are now in September 2006.

My system is not fixed.  My load average will hardly ever go down below 2.00.  It's almost like my load average STARTS at 2.00, so 2.00 really means 0.00?  My system is almost fully 100% idle, so it can't possibly be 2.00 load average.

What's really strange is I have 2 systems with the exact same version of Ubuntu with all updates applies.  One has never done this, however, my newest spin has the problem.

Is there something I can do to fix this?

---

### Post by orb9220 on 2006-09-03
Well from what I have seen on the forums here if you do a top and xorg is at the top. 

Then the problem usally is not having the right video drivers installed or/and xorg.conf file is not configured correctlly.

That is the largest reason for high cpu use I have seen on this forum. Could be something else tho.

Sorry couldn't be more help.

---

### Post by maniacmusician on 2006-09-03
yeah, so what does top say?

---

### Post by the_0ne on 2006-09-03
Thanks for the reply.

No, it's usually not xorg.conf and my machine is almost fully idle.  In fact, most of the time I am looking at it now, top is the "top" process.  Even though my machine is fully idle, the load average shows 2.00 2.00 2.00.  :(

Thanks again for the reply.

---

### Post by the_0ne on 2006-09-03
> **maniacmusician said:**
> yeah, so what does top say?

I'll copy/paste it below.  As you can see I am almost fully 100% idle (99.0% at the moment) but my load average is 2.02, 2.01, 2.00.  :(

```
top - 00:58:06 up 16:31,  3 users,  load average: 2.02, 2.01, 2.00
Tasks: 100 total,   1 running,  98 sleeping,   0 stopped,   1 zombie
Cpu(s):  1.0% us,  0.0% sy,  0.0% ni, 99.0% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    776048k total,   456196k used,   319852k free,    28828k buffers
Swap:  2273156k total,    13284k used,  2259872k free,   243216k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4203 root      15   0 72192  33m 9488 S  0.7  4.5   4:03.56 Xorg
29911 dsmorey   16   0  2200 1116  856 R  0.3  0.1   0:00.51 top
    1 root      16   0  1568  532  460 S  0.0  0.1   0:01.56 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 events/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  111 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  112 root      15   0     0    0    0 S  0.0  0.0   0:00.02 pdflush
  114 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  113 root      15   0     0    0    0 S  0.0  0.0   0:00.27 kswapd0
  701 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod
 1825 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1833 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt
 1840 root      15   0     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0
 1915 root      15   0     0    0    0 S  0.0  0.0   0:00.13 kjournald
 2149 root      11  -4  2428  916  368 S  0.0  0.1   0:00.46 udevd
 2975 root      20   0     0    0    0 S  0.0  0.0   0:00.00 shpchpd_event
 3143 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
 3144 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 usb-storage
 4056 root      16   0  2156 1196  644 S  0.0  0.2   0:00.01 acpid
 4149 syslog    16   0  1764  668  548 S  0.0  0.1   0:00.07 syslogd
 4175 root      15   0  1680  496  412 S  0.0  0.1   0:00.03 dd
 4177 klog      17   0  2420 1348  388 S  0.0  0.2   0:00.07 klogd
 4199 root      16   0 10912 1808 1224 S  0.0  0.2   0:00.00 gdm
 4200 root      16   0 11264 2600 1956 S  0.0  0.3   0:00.01 gdm
 4232 hplip     16   0 12868  924  696 S  0.0  0.1   0:00.00 hpiod
 4236 hplip     15   0  9404 4672 1092 S  0.0  0.6   0:00.04 python
 4283 cupsys    16   0  4212 1792 1300 S  0.0  0.2   0:00.28 cupsd
 4308 messageb  16   0  2192  900  672 S  0.0  0.1   0:00.22 dbus-daemon
```

---

### Post by maniacmusician on 2006-09-03
oh i think i misread your problem. is your cpu high all the time or is your load just around 2? 

is this a problem? mine is 1.00, 2.32, 2.16. i dont have any performance problems or anything.

---

### Post by orb9220 on 2006-09-03
Well mine seems normal on a 1.3ghz. machine my top is 

top - 22:06:43 up  2:47,  2 users,  load average: 0.26, 0.24, 0.15
Tasks:  94 total,   1 running,  93 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.3% us,  1.3% sy,  0.0% ni, 84.1% id,  0.0% wa,  3.7% hi,  1.7% si
Mem:    645888k total,   499864k used,   146024k free,    26864k buffers
Swap:   714884k total,    18832k used,   696052k free,   205740k cached

---

### Post by the_0ne on 2006-09-03
> **maniacmusician said:**
> oh i think i misread your problem. is your cpu high all the time or is your load just around 2? 

is this a problem? mine is 1.00, 2.32, 2.16. i dont have any performance problems or anything.

No problem, I was hoping I worded it right.  No, my "actual" load is very low.  The machine doesn't do much, it's just a machine I am messing with.  Most of the time the machine sits almost fully idle.  However, my load average never goes below 2.00.  It's almost like 0.00 became 2.00.  If top is showing 2.00, 2.01, 2.02, in actuality it's really 0.00, 0.01, 0.02.

Hope that explains it.  Definitely one of the stranger problems I've seen with linux.

---

### Post by the_0ne on 2006-09-03
> **orb9220 said:**
> Well mine seems normal on a 1.3ghz. machine my top is 

top - 22:06:43 up  2:47,  2 users,  load average: 0.26, 0.24, 0.15
Tasks:  94 total,   1 running,  93 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.3% us,  1.3% sy,  0.0% ni, 84.1% id,  0.0% wa,  3.7% hi,  1.7% si
Mem:    645888k total,   499864k used,   146024k free,    26864k buffers
Swap:   714884k total,    18832k used,   696052k free,   205740k cached

Right, that's how most of my linux machines are.  I am on a laptop and I am ssh'd into the machine with the problem (Sony Vaio 1.6 ghz).  My laptop hardly ever goes above 1.50 and that's at a pretty full load.  However, the machine I am having the load average problem sits almost 100% idle (most of the time), but still shows 2.00 load average.

---

