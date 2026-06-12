---
title: "Fglrx error, running mesa now"
date: 2006-09-16
forum: Desktop Environments
---

### Post by KenSentMe on 2006-09-16
Since a couple of days (maybe since the kernel update) my Ati drivers aren't loaded anymore and my system uses the mesa drivers, so i can't play 3d games anymore. When i look in dmesg i get these errors:

> 
[17179612.448000] fglrx: disagrees about version of symbol boot_cpu_data
[17179612.448000] fglrx: Unknown symbol boot_cpu_data


I've tried reinstalling restricted modules but that didn't help.

Some things about my system. I run a Pentium 4 cpu with an Ati Radeon 9800 Pro card. I run dual desktop which i got working thanks to this Howto: [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174) (i use the Big-Desktop method).

This is my xorg.conf: [http://lab.vandenieuwenhof.nl/files/xorg.conf](http://lab.vandenieuwenhof.nl/files/xorg.conf)

Anyone have a clue how to get my fglrx use 3d again?

---

### Post by Johnathon on 2006-09-16
Every time you update your Kernel, you need to rebuild/install your ATI drivers. Just follow the how-to you used to install them again.

---

### Post by KenSentMe on 2006-09-16
> **Johnathon said:**
> Every time you update your Kernel, you need to rebuild/install your ATI drivers. Just follow the how-to you used to install them again.

Yes, that solved it. Thanks for the tip

---

### Post by KenSentMe on 2006-09-20
Okay, after another kernel update i get the same problem, but i can't solve it by rebuilding the ATI drivers.

Here is my Xorg.0.log:

[http://lab.vandenieuwenhof.nl/files/Xorg.0.log](http://lab.vandenieuwenhof.nl/files/Xorg.0.log)

And these are the errors i get in dmesg:

> 
[17179591.976000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179591.980000] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[17179591.980000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[17179614.152000] [fglrx:firegl_unlock] *ERROR* Process 4799 using kernel context 0


This is process 4799:

> 
root      4799  8.6  2.2  35108 23744 tty7     Ss+  12:02   0:11 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7


Does someone see where i go wrong?

---

