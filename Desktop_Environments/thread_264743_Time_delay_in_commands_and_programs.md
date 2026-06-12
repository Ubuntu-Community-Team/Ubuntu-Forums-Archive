---
title: "Time delay in commands and programs"
date: 2006-09-25
forum: Desktop Environments
---

### Post by utab on 2006-09-25
Dear all,

When I am using my system, trying to open thunderbird, mozilla and even shell commands on the console work with a delay. I have still places to use in y hard drives so I pasted the output the result of my df command for your examination. This delay is much more obvious in mozilla and thunderbird(It was not the case before they were starting quite fast).


Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             10578780   7252544   2788864  73% /
varrun                  517984       136    517848   1% /var/run
varlock                 517984         4    517980   1% /var/lock
udev                    517984       168    517816   1% /dev
devshm                  517984         0    517984   0% /dev/shm
/dev/sda8             11132168   5714156   4852528  55% /home
/dev/sda1                96154      7422     88732   8% /media/sda1
/dev/sda2             31453176  23246008   8207168  74% /media/sda2
/dev/sda5              4000348   1329168   2671180  34% /media/sda5
//filesrv/pool        16513792   5572864  10940928  34% /home/utab/documents/MECH_POOL
//10.33.175.17/utabak
                     146792448 137691136   9101312  94% /home/utab/documents/MECH_HOME
tmpfs                   517984     18856    499128   4% /lib/modules/2.6.15-27-386/volatile
tmpfs                   517984     18856    499128   4% /lib/modules/2.6.15-26-386/volatile

Any comments are highly appreciated.

Regards.

---

### Post by kidders on 2006-09-25
On most filesystems, the amount of free disk space is fairly unrelated to performance. The one notable exception is FAT, of course.

Of more use might be the output of "top". Try the following:

1. Leave your computer doing nothing and use "top" to take a look at your CPU usage stats. They should (obviously) be quite low. Listen to your disk drives, to see if they're doing anything.

2. Launch Firefox/etc. and see what happens. CPU usage should climb to 100%. Other (more important) things should happen too, but explaining them all would be very long-winded lol. One thing you could do though is note the %age called "wa". On my PC, it usually stays at (or close to) zero while loading firefox.

There are some quick questions worth asking though:
[LIST]
[*]Can you associate the drop in performance with any hardware/software change?
[*]How much swap are you using, and is it still alive?
[/LIST]

---

### Post by utab on 2006-09-25
1. Leave your computer doing nothing and use "top" to take a look at your CPU usage stats. They should (obviously) be quite low. Listen to your disk drives, to see if they're doing anything.

This is OK

2. Launch Firefox/etc. and see what happens. CPU usage should climb to 100%.

Almost %30. wa nearly %0.

While launching thunderbird wa climbs to %70, and cpu almost %30 again.


There are some quick questions worth asking though:
[LIST]
[*]Can you associate the drop in performance with any hardware/software change?

I have not done sth special I can remember so far.
[*]How much swap are you using, and is it still alive?

According to top 

Swap:   987956k total,    37700k used,   950256k free,   880648k cached

Looks OK to me.

[/LIST][/QUOTE]

---

### Post by kidders on 2006-09-25
Damn. None of what you posted is in any way unreasonable. Having thought about it for a while, I can't imagine why performance has deteriorated so much over time :-(

Ordinarily, I would make various suggestions to people concerned about performance issues, such as tinkering with "hdparm", prelinking (prebinding) applications, spreading swap space over multiple physical disks, unloading unnecessary kernel modules, and so on, but I hesitate to do so in your case, since you have only recently become dissatisfied with your PC's speed.

Are you using a 64-bit architecture btw?

I don't seem to have been much use to you ... perhaps if you bend the forum rules a bit and re-post this issue in another thread, someone smarter might respond. Sorry. :confused:

---

