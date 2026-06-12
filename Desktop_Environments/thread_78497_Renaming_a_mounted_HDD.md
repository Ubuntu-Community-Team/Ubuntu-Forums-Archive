---
title: "Renaming a mounted HDD"
date: 2005-10-18
forum: Desktop Environments
---

### Post by Gordonbp531 on 2005-10-18
I have an external firewire HDD with two partitions. One is a 30GB FAT32 partition called "transfer" which shows up on my desktop as a drive called "Transfer". the other is an Ext3 formatted partition, which, try as I might I CANNOT renme it from it's current name of"44.3 GB Disk"! How do I get the name changed?

thanks

---

### Post by steve.horsley on 2005-10-19
Try using "mount" or "df" to find the device name for the disk. Then unmount it with "sudo umount /dev/WhateverItIs". Then make a directory to mount it at, and mount it there:
sudo mkdir /media/NewNameForDisk
sudo mount -t vfat /dev/WhateverItIs /media/NewNameForDisk

For permanent renaming, after reboot etc, look at the file /etc/fstab, which lists where each disk should be mounted.

---

### Post by Gordonbp531 on 2005-10-19
Hi,
Thanks for that - I actually was told about the e2label command in another forum - that works!

---

