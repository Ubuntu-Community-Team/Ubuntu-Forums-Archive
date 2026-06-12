---
title: "slow boot"
date: 2005-04-03
forum: Desktop Environments
---

### Post by dukeinlondon on 2005-04-03
On boot, it seems ubuntu is looking for a vfs on an ext3 partition and it's taking ages. I doesn't find it cause my boot partition is reiserfs. How can I disable this annoying behaviour ?

---

### Post by MaX on 2005-04-15
[QUOTE=dukeinlondon]On boot, it seems ubuntu is looking for a vfs on an ext3 partition and it's taking ages. I doesn't find it cause my boot partition is reiserfs. How can I disable this annoying behaviour ?[/QUOTE]
 Grub can't boot from an ReiserFS partition directly, that's why you get the message, when I had Gentoo I had a 50Mb ext3 partition as boot and my / as reiserfs.

---

### Post by dewey on 2005-04-15
Put /boot on an ext2 or ext3 partition, and it solves that little problem.

---

### Post by dukeinlondon on 2005-04-16
[QUOTE=dewey]Put /boot on an ext2 or ext3 partition, and it solves that little problem.[/QUOTE]
 I've replaced grub with lilo and that does it. Thanks for the info on grub !

---

### Post by man.life on 2005-04-17
I have the same problem described above but want to keep grub. I've already moved my /boot files into /dev/hda4 (ext3, 50MB) and modified /etc/fstab to mount /dev/hda4 as /boot. But grub still gives the same message. What should I do?

---

### Post by strawberry on 2005-04-17
Keep grub but change to ext3fs. Is there any disadvantage?

---

### Post by trash-can on 2005-04-17
I actually believe it is not grub fault. Grub supports booting from reiserfs.
```
$ ls /boot/grub/*stage1_5
/boot/grub/e2fs_stage1_5  /boot/grub/jfs_stage1_5    /boot/grub/reiserfs_stage1_5
/boot/grub/fat_stage1_5   /boot/grub/minix_stage1_5  /boot/grub/xfs_stage1_5
```

Notice reiserfs_stage1_5 file! IIRC, this file is responsible for booting from reiserfs partition.

I myself have jfs ROOT partition and yes there is this VFS message, but it takes just a few seconds. I suspect that problem is with initrd image.
```
$ sudo mount -o loop -t cramfs /boot/initrd.img-2.6.10-5-386 /mnt/
$ cd /mnt/
$ cat linuxrc.conf 
RESUME=/dev/hda2
DELAY=0
BUSYBOX=
**FSTYPES=ext3,ext2,jfs,vfat,cramfs**
IDE_CORE=ide-core
VERSION=0.1.77ubuntu3
```

Maybe if you make slightly tweaked initrd image, it would work better. Just a thought.

---

