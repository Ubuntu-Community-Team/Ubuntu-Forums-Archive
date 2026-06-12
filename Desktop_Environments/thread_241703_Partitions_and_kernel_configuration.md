---
title: "Partitions and kernel configuration"
date: 2006-08-22
forum: Desktop Environments
---

### Post by Steven_B on 2006-08-22
I did a bunch of messing around with my partitions recently, and installed Ubuntu in a second partition (after changing the partitions).
My disk changed from:

2) swap
1) NTFS
4) ext3 (/ for boot #1)
3) FAT

to:
4) swap
1) NTFS
2) extended
    5) ext3 (/ for boot #2)
    6) ext3 (/ for boot #1)
3) FAT
When booting #1, I got a kernel panic:
```
Attempt to access beyond end of device
hda2: rw=16, want=8, limit=2
Kernel panic - not syncing: I/O error reading memory image
```
Boot #2 works fine.  I copied the files from /boot #2 to /boot #1, and then I was able to boot onto hda6.

Somehow, kernel #1 is not configured correctly for the different disk partitions.  How can I fix the kernel options so it understands the new disk geometry?

It isn't a problem with fstab.  The entries are correct, and the copied kernel can boot fine.

It isn't a problem with the grub menu entries.  Here is the working one, and the broken one below it.
```
title		Ubuntu, kernel 2.6.15-25-k7
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-25-k7 root=/dev/hda6 ro noapic nolapic quiet splash
initrd		/boot/initrd.img-2.6.15-25-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-k7 -broken
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/hda6 ro noapic nolapic quiet splash
initrd		/boot/initrd.img-2.6.15-26-k7
savedefault
boot
```

---

### Post by Steven_B on 2007-03-21
If I recall correctly, I had to add "resume=/dev/hda4" to the end of the kernel line in menu.lst:
```
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda5 ro noapic nolapic quiet splash resume=/dev/hda4
```
This tells the kernel to look for the swap partition on /dev/hda4, rather than wherever it thought it should be.

---

