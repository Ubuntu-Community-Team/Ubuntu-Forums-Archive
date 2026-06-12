---
title: "Weird memory behaviour (management) on Ubuntu 8.04 x64"
date: 2009-05-09
forum: General Help
---

### Post by stefangr1 on 2009-05-09
I am a regular user of vmware, and have recently switched from Kubuntu 7.10 i586 to Ubuntu 8.04LTS x64. I'm having a serious performance problem that weren't there before.

Hardware: I have a system with a C2D 2.66Ghz processor, and 2GB of RAM, 3 hard disks.

The operating system has it's own hard disk, I'm running two virtual machines who are also both on their own disk. Total memory usage of vmware is around 1400MB, processor usage is 60% at core(1) and 10% at core(2). On Kubuntu 7.10 in a situation like this, there would not be any noticeable performance slowdown on the rest of the system (which is more or less idle), and the VM's would run perfectly. This is as I would expect, since 600mb should be sufficient to run when doing basically nothing, the os has it's own disk, and at least one processor is still 90% idle.

Now on Ubuntu 8.04 my system becomes totally sluggish in a situation like this. A terminal needs 5 seconds to open in stead of the normal <1sec, even putting a different window on the foreground takes time.

It seems that the problem is due to some weird memory management:

             total       used       free     shared    buffers     cached
Mem:       2062876    2021900      40976          0       2084    1667136
-/+ buffers/cache:     352680    1710196
Swap:      1020088     897124     122964

As you can see the system has started swapping without need. If the 900 MB would have been in normal RAM, there would still have been almost 700MB present for caching...

Any ideas how to 'solve' this and improve performance?

---

