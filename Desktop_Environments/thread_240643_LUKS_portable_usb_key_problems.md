---
title: "LUKS portable usb key problems"
date: 2006-08-21
forum: Desktop Environments
---

### Post by napsy on 2006-08-21
I tried to make a portable LUKS usb key by creating two partitions, sda1 being formatted in fat32 (8 MB) and FreeOTFE on it. The other partition, sda2 being luks formatted FAT32 (498 MB) with luksformat -t vfat /dev/sda2.

The problem is that when I plug in the key, Linux just mounts the sda2 LUKS partition as a normal unencrypted drive. What am I doing wrong?

I think it has something to do with the filesystem when creating the LUKS partition using luksformat:
Enter LUKS passphrase:
key slot 0 unlocked.
Command successful.
mkfs.vfat 2.11 (12 Mar 2005)
unable to get drive geometry, using default 255/63

---

### Post by Meson on 2008-04-11
Did you put an entry for your usb drive in crypttab?

---

