---
title: "System fails to boot after automatic disk check (done at boot time)"
date: 2008-12-10
forum: General Help
---

### Post by fu.linux on 2008-12-10
At the next restart after automatic disk check at Ubuntu boot,
the system drops to BusyBox with an initramfs prompt after
showing the followind message:

"Gave up waiting for root device. Common problems:
...
ALERT! /dev/disk/by-uuid/6f2c7171-3bf0-4ab5-a491-0b7880abbfd5 does not exist."

then continuing with the following message block several times
(after which the initramfs prompt finally shows up):

[ 35.820113]: ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ .........]: cmd a0/01:00:00:80:00/00:00:00:00:00/b0 tag 0 dma 16512
[ .........]: cdb 5a 00 2a 00 00 00 00 00 80 00 00 00 00 00 00
[ .........]: res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ .........]: ata1.01: status {DRDY}

then if I simply hit Control-D, it tries to resume from disk with id 47fa0689-d5f2-4b7b-a014-b822a8b6589b, succeeding in starting the system,
but if rebooted, the same problem occurs.

I would be glad to know how could I fix the problem.
(I've searched for solutions, backed up my /boot/initrd.img-2.6.27-9-generic file and run the following commands, but the problem did not disappear:
sudo mkinitramfs -o /boot/initrd.img-2.6.27-9-generic
sudo update-grub)

As a note, when changing from graphic boot splash screen to text mode, I can see "Booting from (hd0,5)" near by the id 6f2c7171-3bf0-4ab5-a491-0b7880abbfd5; but after I press Control-D, I can see that it uses dev(8,1) which has near by id mentioned above (47fa0689-d5f2-4b7b-a014-b822a8b6589b), I don't know the exact meaning of these though.


My system information regarding this problem:
Using Ubuntu 8.10, GNOME 2.24.1 (Ubuntu 2008-10-24),
KERNEL 2.6.27-9-generic (#1 SMP Thu Nov 20 21:57:00 UTC 2008),
GCC version 4.3.2 (i486-linux-gnu)
---------------------------------------------------------------

/dev/disk content
1c1b75f2-28bc-43a7-a25c-808641eb4ae2 -> sda7
6f2c7171-3bf0-4ab5-a491-0b7880abbfd5 -> sda6
40ba53b3-cdad-4258-bccb-8b938644a55c -> sda5
47fa0689-d5f2-4b7b-a014-b822a8b6589b -> sda1

sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x117d117d

   Device Boot Start End Blocks Id System
/dev/sda1 * 1 267 2144646 82 Linux swap / Solaris
/dev/sda2 268 9964 77891152+ 5 Extended
/dev/sda5 268 297 240943+ 83 Linux
/dev/sda6 298 2729 19535008+ 83 Linux
/dev/sda7 2730 9964 58115106 83 Linux

/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda6
UUID=6f2c7171-3bf0-4ab5-a491-0b7880abbfd5 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda7
UUID=1c1b75f2-28bc-43a7-a25c-808641eb4ae2 /home ext3 relatime 0 2
# /dev/sda5
UUID=40ba53b3-cdad-4258-bccb-8b938644a55c /tmp ext3 relatime 0 2
# /dev/sda1
UUID=47fa0689-d5f2-4b7b-a014-b822a8b6589b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

/boot/grub/menu.lst

title Ubuntu 8.10, kernel 2.6.27-9-generic
uuid 6f2c7171-3bf0-4ab5-a491-0b7880abbfd5
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=6f2c7171-3bf0-4ab5-a491-0b7880abbfd5 ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid 6f2c7171-3bf0-4ab5-a491-0b7880abbfd5
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=6f2c7171-3bf0-4ab5-a491-0b7880abbfd5 ro single
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
uuid 6f2c7171-3bf0-4ab5-a491-0b7880abbfd5
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=6f2c7171-3bf0-4ab5-a491-0b7880abbfd5 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid 6f2c7171-3bf0-4ab5-a491-0b7880abbfd5
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=6f2c7171-3bf0-4ab5-a491-0b7880abbfd5 ro single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
uuid 6f2c7171-3bf0-4ab5-a491-0b7880abbfd5
kernel /boot/memtest86+.bin
quiet

---

