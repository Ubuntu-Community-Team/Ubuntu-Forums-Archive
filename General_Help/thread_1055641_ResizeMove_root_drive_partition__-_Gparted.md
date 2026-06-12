---
title: "Resize/Move root drive partition  - Gparted"
date: 2009-01-30
forum: General Help
---

### Post by shanmugamt on 2009-01-30
Hi, I want to increase my root drive disk space. But i am unable to do using Ubuntu-Gparted. For some reason, my root drive's effective space is 4.5GB but i have 10GB space on that drive. So Ubuntu says more than 90% of the disk space has been utilized. I have attached my GParted screen-shot with this thread. Could some one help me to resize my disk space?

Here is more info about my problem:
[http://ubuntuforums.org/showthread.php?t=1038896](http://ubuntuforums.org/showthread.php?t=1038896)

The resize/move option is disabled in GParted. So i couldn't resize also.
My Ubuntu is running short of memory, even though i have enough space. Your help is much appreciated.

Thanks,
Shan

---

### Post by unutbu on 2009-01-30
Since your /host/ubuntu/disks/root.disk is mounted at /, I think you must be using Wubi. To resize the / virtual disk, follow the instructions here: 

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

Scroll down (or use Find) to where it says "Resizing virtual disks using LVPM".

---

