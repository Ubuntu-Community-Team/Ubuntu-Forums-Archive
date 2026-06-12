---
title: "Jaunty Locks Up"
date: 2009-05-26
forum: General Help
---

### Post by jack24 on 2009-05-26
Ever since I installed Jaunty on my laptop, it's been repeatedly crashing and destroying my file system.

Vaio Z750 (AMD64 Dual Core)
Jaunty 64 bit (fresh install -- several)

It locks up and and the leds flash. I can't do anything, even with REISUB or the off switch. The only way to get out is to unplug the laptop and remove the battery.

When I try to boot up again, this is the last and first things in the kernel log:

     May 25 15:48:08 l-laptop kernel: [ 324.288093] CE: hpet increasing min_delta_ns to 15000 nsec
     May 25 16:52:51 l-laptop kernel: [ 4207.164049] CE: hpet increasing min_delta_ns to 22500 nsec

     May 25 21:46:28 l-laptop kernel: Inspecting /boot/System.map-2.6.28-11-generic
     May 25 21:46:28 l-laptop kernel: Cannot find map file.

Earlier (right after boot up), there's a:

     May 25 15:42:59 l-laptop kernel: [ 5.183767] Marking TSC unstable due to TSC halts in idle

and a:

     May 25 15:42:59 l-laptop kernel: [ 6.501104] Clocksource tsc unstable (delta = -145986009 ns)

Whether I can fix the partition with fsck or have to boot to the installation disk, my user directory is gone.

The problem seems to be that something makes the clocksource unstable which eventually causes the crash.

I've found these bug reports that are identical or similar to the problem I'm having:

Bug #355155
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155)

Bug #190414
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190414](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190414)

Bug #367464
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/367464](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/367464)

Bug #375986
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/375986](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/375986)

Bug #375072
[https://bugs.launchpad.net/ubuntu/+bug/375072](https://bugs.launchpad.net/ubuntu/+bug/375072)

Bug #352373
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/352373/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/352373/)

I'd appreciate any help or suggestions.

jack

---

### Post by Per Olav on 2009-06-27
Any luck tracking down this issue? I'm experiencing it too

---

