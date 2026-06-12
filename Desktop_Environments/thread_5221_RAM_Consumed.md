---
title: "RAM Consumed"
date: 2004-11-16
forum: Desktop Environments
---

### Post by Crisp on 2004-11-16
I've noticed that my RAM is always at least 80% used under Gnome, but usually closer to 95%.  I have 512MB DDR, so I find it hard to see where 500MB of RAM is going to keep Gnome, Gaim, BitchX and Firefox open, plus a service or two.  Oh yeah, I use some gDesklets too, which I am aware take up quite a bit of memory, but I have no more than three active.  

Basically, I'd just need to see exactly what is using how much memory; what's the best way to view this information?  If I can attribute the memory usage to whatever is using them, then I can check it's all above board. 

I've heard about FireFox having memory leak issues, which could explain why memory usage seems to increase within the 6 hour period from boot to power off, despite nothing substantially memory intensive being called upon during that period.

Or is it possible that gDesklets are giving false information, because system performance doesn't seem to be dropping much, despite this apparent high memory usage.  I'm basing this information from such a desklet, and it's not the first time it seems to have given dubious information.  Infact system monitor seems to tell me that the problem isn't really a problem.

What gives?

-Crisp

---

### Post by dataw0lf on 2004-11-16
I'd suggest using top (a command)  or the system monitor in Gnome to correlate if the gdesklets are reporting correctly.  They're probably not.
dataw0lf

---

### Post by Crisp on 2004-11-16
```

top - 21:48:26 up  7:40,  4 users,  load average: 0.49, 0.34, 0.23
Tasks:  88 total,   1 running,  87 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.4% us,  0.3% sy,  0.0% ni, 91.3% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    516608k total,   509576k used,     7032k free,    38004k buffers
Swap:   497972k total,        0k used,   497972k free,   251464k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
11423 root      15   0  112m  28m  99m S  4.7  5.6  11:41.38 XFree86
11540 crisp     15   0 70052  36m  20m S  3.7  7.2  13:18.50 gdesklets
11531 crisp     15   0 31992 7028  14m S  0.3  1.4   0:03.22 gnome-cups-icon
25990 crisp     16   0  2036 1032 1820 R  0.3  0.2   0:00.14 top
    1 root      16   0  1492  512 1340 S  0.0  0.1   0:00.94 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root       5 -10     0    0    0 S  0.0  0.0   0:00.26 events/0
    4 root      11 -10     0    0    0 S  0.0  0.0   0:00.00 khelper
    5 root      15 -10     0    0    0 S  0.0  0.0   0:00.00 kacpid
   50 root       5 -10     0    0    0 S  0.0  0.0   0:00.07 kblockd/0
   60 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
   61 root      15   0     0    0    0 S  0.0  0.0   0:00.11 pdflush
   63 root       5 -10     0    0    0 S  0.0  0.0   0:00.00 aio/0
   62 root      15   0     0    0    0 S  0.0  0.0   0:00.03 kswapd0
  205 root      25   0     0    0    0 S  0.0  0.0   0:00.00 kseriod
  301 root      16   0     0    0    0 S  0.0  0.0   0:00.78 kjournald
  379 root       6 -10  1472  372 1320 S  0.0  0.1   0:00.01 udevd

```

So it seems most of my memory really is being used, but I still don't know from where.  As I thought, X and gDesklets take their fair chunk, but according to that table, I still don't know/can't see where the rest of it is going.

Oddly, System Monitor reports 219Mb usage, far from the 498Mb or so reported in top and the gdesklet.  Judging from system performance, I'm leaning towards 219Mb being the actual number, but it'd be nice to know.

-Crisp

---

### Post by jdong on 2004-11-16
The rest of your RAM is dedicated to caches. Linux heavily and aggressively caches your data, resulting in high performance. On a 1GB RAM workstation @ school, Linux usually leaves less than 10MB free, and after a day of use practically everything from Firefox to Openoffice is cached, launching almost instantaneously...

As soon as another application needs more RAM, Linux will let go of some caches and turn that freed RAM over.

Truly "free" RAM is wasted RAM.

---

### Post by Crisp on 2004-11-16
Oh right, well if that's the case, then that's great.  I just wanted an explanation for this, as under Windows I'd get an average of about 50% used.  Extreme caching is fine by me, and that explains why my system performance seemed to be great despite my memory question.

Thanks a lot jdong, 

-Crisp

---

### Post by jdong on 2004-11-16
You're welcome. This is actually a very common question, and has caused many Linux newbies to go back to Windows, claiming Linux is a RAM hog.

True, Linux is a RAM hog, but hey, it hogs ram efficiently! LOL

---

### Post by zenwhen on 2004-11-16
When I first started dabbling in Linux this was one of my main "issues", but the people I asked about it were too concerned with defending the OS to tell me what the truth was.

Luckily, you asked here and jdong is not that kind of Linux user. 

I have 1GB of PC3200, and thanks to Linux's superior memory management, my system ROARS.

---

### Post by clarke.rainey on 2005-02-08
Well I was wondering why my machine only uses about 200MB of RAM or so... no matter how much stuff I have open... like ~10 torrents, about 5 firefox tabs, alot of gdesklets, xmms, a few terminals, and a word processor?... I would think that would take alot more ram...

---

### Post by Mr_Radarkontakt on 2005-02-15
After an uptime of about 8 hours all my memory is used, and half of my swap.. (512 mb memory) This wouldn't be a problem if the machine had gone all right, but it isn't. It gets really slow and eventually I have to restart it.. It's very anoying when I'm downloading stuff. It doesn't matter if I close all the applications running, or just don't start them from the beginning.
How can this be? 


//Mr Radarkontakt

---

### Post by El Guapo on 2005-02-16
I have never noticed any of my swap partition being used.  I have 512MB of RAM and I made 1024MB of swap.  None of it ever gets used and I was wondering if maybe it isn't being seen or it isn't mounted properly.  Although using '*top*'  it has the swap listed, but 0k used.

Any ideas?

---

### Post by nocturn on 2005-02-16
[QUOTE=El Guapo]I have never noticed any of my swap partition being used.  I have 512MB of RAM and I made 1024MB of swap.  None of it ever gets used and I was wondering if maybe it isn't being seen or it isn't mounted properly.  Although using '*top*'  it has the swap listed, but 0k used.

Any ideas?[/QUOTE]

Your swap will only be used when there is not enough memory because reading/writing to HD is much slower then memory.
If you have enough RAM, your swap will never be touched.

BTW, if you find a testprogram that can consume all your available RAM, you will see swap being used.

---

### Post by rwabel on 2005-03-02
well I've about the same symptoms. I've 1 gb ram and I'm on ubuntu hoary. cpu usage is normal. But it seems that memory is always completly used. Maybe it's something different. But it's funny to see windows XP in vmware running even faster than ubuntu (without having vmware running).

[QUOTE=Mr_Radarkontakt]After an uptime of about 8 hours all my memory is used, and half of my swap.. (512 mb memory) This wouldn't be a problem if the machine had gone all right, but it isn't. It gets really slow and eventually I have to restart it.. It's very anoying when I'm downloading stuff. It doesn't matter if I close all the applications running, or just don't start them from the beginning.
How can this be? 


//Mr Radarkontakt[/QUOTE]

---

### Post by tdell on 2005-03-02
Maybe I am doing something wrong but my RAM usage rarely goes above 25% and my swap is always at 0. I have 512M RAM. Should I be worried?

Tom

---

