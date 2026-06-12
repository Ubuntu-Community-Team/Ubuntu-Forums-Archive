---
title: "fstab entries for mounting windows partitions"
date: 2009-01-18
forum: Desktop Environments
---

### Post by Kiwisaft on 2009-01-18
I did some fstab entries to mount windows partitions:

# /dev/sda1
/home/user/Desktop/WinDocs/sda1	ntfs	defaults	0	2
# /dev/sda5
/home/user/Desktop/WinDocs/sda5	ntfs	defaults	0	2
# /dev/sda6
/home/user/Desktop/WinDocs/sda6	vfat	defaults	0	2

But it doesn't work. After startup, the folders are empty.
If I mount it over Commandline: 
mount -t ntfs /dev/sda5 /home/user/Desktop/WinDocs/sda5

it works perfectly.

Does anyone have an idea what I did wrong?

---

### Post by Kiwisaft on 2009-01-18
sorry, just saw my mistake:

/dev/sda1 /home/user/Desktop/WinDocs/sda1 ntfs defaults 0 2
/dev/sda5 /home/user/Desktop/WinDocs/sda5 ntfs defaults 0 2
/dev/sda6 /home/user/Desktop/WinDocs/sda6 vfat defaults 0 2

---

