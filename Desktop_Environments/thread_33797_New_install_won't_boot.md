---
title: "New install won't boot"
date: 2005-05-12
forum: Desktop Environments
---

### Post by jon21 on 2005-05-12
My fresh Ubuntu 5.04 install won't boot.  Here's what I get:

...
Starting Ubuntu...
pivot_root: No such file or directory
/sbin/init: 428: cannot open dev/console: No such file
Kernel panic - not syncing: Attempted to kill init!

Then just nothing.

The installation process from install CD went fine.

I had Ubuntu 5.04 up and running on this machine, but decided to do a fresh install to use the whole hard disk, eliminating several old partitions.

System is a Dell Precision 530, 30GB SCSI drive, nVidia graphics board.

Ideas?

---

### Post by jon21 on 2005-05-13
Found the problem.

For some reason Ubuntu install configured my root drive as /dev/sde1.  I edited /boot/grub/main.lst and changed /dev/sde1 to /dev/sda1 and all worked fine.

FYI I used a Ubuntu Live CD to boot and edit the main.lst file.

I suspect this problem may have been caused by having a memory card reader attached when I did the install.  Perhaps that created extra "drives" that Ubuntu selected.

---

