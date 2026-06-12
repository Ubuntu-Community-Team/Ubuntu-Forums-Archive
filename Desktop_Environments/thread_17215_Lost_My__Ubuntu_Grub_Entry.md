---
title: "Lost My  Ubuntu Grub Entry"
date: 2005-02-26
forum: Desktop Environments
---

### Post by Joe on 2005-02-26
I installed Mepis on another partition of my hard drive and let it install it's MBR and I ended up losing my Grub entry on Ubuntu.  I was running Warty.  Can anyone give me an idea of what should be in my /boot/grub/menu.lst?  I have 3 different partitions on my hard drive.  Ubuntu is on hda1, Mepis is on hda2 and my swap space is hda3.

---

### Post by alastair on 2005-02-27
Perhaps something like this for Ubuntu - if you are right about it being on hda1 (root) :

title           Ubuntu, kernel ?
root            (hd0,0)
kernel          /boot/vmlinuz-? root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-?
savedefault
boot

The "?" are because I do not know what your kernel is. You can find out by (temporarily) mounting /dev/hda1 in Mepis perhaps i.e.

sudo mount /dev/hda1 /mnt/tmp

Then :

ls -l /mnt/tmp/boot

to see kernels etc.

---

### Post by Joe on 2005-02-27
Thanks.  I wasn't thinking.  I just accessed the partition that Ubuntu was on and copied over the grub entry from there.

[QUOTE=alastair]Perhaps something like this for Ubuntu - if you are right about it being on hda1 (root) :

title           Ubuntu, kernel ?
root            (hd0,0)
kernel          /boot/vmlinuz-? root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-?
savedefault
boot

The "?" are because I do not know what your kernel is. You can find out by (temporarily) mounting /dev/hda1 in Mepis perhaps i.e.

sudo mount /dev/hda1 /mnt/tmp

Then :

ls -l /mnt/tmp/boot

to see kernels etc.[/QUOTE]

---

