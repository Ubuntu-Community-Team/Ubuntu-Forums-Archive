---
title: "how do isee the other two drives with xandros and mepis from ubuntu"
date: 2005-10-14
forum: Desktop Environments
---

### Post by kazuya on 2005-10-14
ichigo@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0    1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
ichigo@ubuntu:~$

how do i see the other two drives with xandros and mepis from ubuntu 5.10

how do i add or mount those drives?

---

### Post by Stormy Eyes on 2005-10-14
[QUOTE=kazuya]ichigo@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0    1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
ichigo@ubuntu:~$

how do i see the other two drives with xandros and mepis from ubuntu 5.10

how do i add or mount those drives?[/QUOTE]

Question: did you configure LVM yourself, or did Ubuntu do it for you when installing?

---

### Post by kazuya on 2005-10-14
ubuntu did it for me.

It recognized the external hard drive and usb dvdrom though.
Why not the drives with mepis?

---

### Post by Stormy Eyes on 2005-10-14
[QUOTE=kazuya]It recognized the external hard drive and usb dvdrom though.
Why not the drives with mepis?[/QUOTE]

To be honest, I don't know. What do you see if you run **sudo fdisk /dev/hda** and press "p" to display the partition table?

---

