---
title: "feisty not booting"
date: 2007-06-16
forum: Desktop Environments
---

### Post by mohtasham1983 on 2007-06-16
Hi, i just installed feisty on my machine, but it freezes when splash screen appears after 1%.

pressing Alt+F1 tells me starting up, please wait and then nothing ...

pressing Alt+ctrl+f7 gives me the following error:
udeved-event[1931]:run_program: '/sbin/modprobe' abnormal exit

I have 2 hard disks which i don't have permission to remove any of them. I also don't think that there is any problem with boot partitions and grub menu since menu.lst is pointing everything to the right place.

I think there was a bug in beta version as I searched internet but I didn't find out how this problem is solved in the final version which I am trying to run.

Your help is appreciated.

---

### Post by merlinus on 2007-06-16
This may help:

[http://ubuntuforums.org/showthread.php?t=474734&highlight=two+hard+drives](http://ubuntuforums.org/showthread.php?t=474734&highlight=two+hard+drives)

-merlin

---

### Post by mohtasham1983 on 2007-06-16
there is nothing wrong with partition selection. if grub points to a partition which is not bootable, it will not show splash screen at all.

---

