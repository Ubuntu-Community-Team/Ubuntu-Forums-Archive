---
title: "mount: /dev/fd0 is not a valid block device"
date: 2009-02-26
forum: General Help
---

### Post by MountainX on 2009-02-26
anyone know what my problem is?

$ sudo modprobe floppy
$ sudo mkdir /mnt/floppy
$ sudo mount /dev/fd0 /mnt/floppy/
**mount: /dev/fd0 is not a valid block device**

$ dmesg | grep -i floppy
[   32.365258] Floppy drive(s): fd0 is 1.44M

ls -l /dev/fd0
brw-rw---- 1 root floppy 2, 0 2009-02-11 22:44 /dev/fd0

---

### Post by geraldm on 2009-02-26
I did not get that exact error, but perhaps it means that fd0 is not a line entry in your /etc/fstab file.
What I get here, Ibex
$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda3 sda3 swap swap defaults 0 0
/dev/sdb3 sdb3 swap swap defaults 0 0

Then I try these: 
$ sudo echo "/dev/fd0 /mnt/floppy auto rw,user,noauto 0 0" >> /etc/fstab
$ sudo mkdir /mnt/floppy
$ sudo modprobe floppy
$ sudo mount -t msdos /dev/fd0 /mnt/floppy

Then I get to see the files.

regards,
Gerald

---

