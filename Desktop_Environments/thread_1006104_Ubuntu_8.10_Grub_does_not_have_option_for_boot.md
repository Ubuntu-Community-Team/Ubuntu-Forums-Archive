---
title: "Ubuntu 8.10 Grub does not have option for boot"
date: 2008-12-09
forum: Desktop Environments
---

### Post by newDrapersDrakeUser on 2008-12-09
Hi 

I am trying to install ubuntu 8.10 on my Desktop to have a dual boot with XP. The installation goes fine without any issues, but grub gets entry only for Memtest and XP but there is no entry for booting into the Ubuntu from the disk. I tried to verify contents of the /boot folder but could not find the vmlinuz file in it. 

Partition details to hold ubuntu 8.10 :

1. SWAP 5 GB
2. /HOME ext2 5 GB
3. /   ext2  20 GB

Please suggest if i have done some mistake in installing ubuntu.

Thanks in advance.



:confused:

---

### Post by taurus on 2008-12-09
See if you can reinstall GRUB to MBR with the LiveCD.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by caljohnsmith on 2008-12-09
How about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
From the above output, determine which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
ls -lR /mnt/boot
cat /mnt/boot/grub/menu.lst
```
That should help clarify your setup.

---

