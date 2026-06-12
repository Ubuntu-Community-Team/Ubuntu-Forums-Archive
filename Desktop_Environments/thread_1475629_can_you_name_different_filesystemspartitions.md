---
title: "can you name different filesystems/partitions?"
date: 2010-05-07
forum: Desktop Environments
---

### Post by fuzzylogic25 on 2010-05-07
I have just installed the latest Ubuntu (10.4) with windows xp already installed. I have partitions C (NTFS) & D (NTFS) in addition to the Ubuntu ones. The D partition contains all my data, and the C one is the operating system for win xp which also contains some important data.

I can access these drives in menu PLACES but it just shows up as 20GB FILESYSTEM and 25GB FILESYSTEM. 

My question is can you name these filesystems like you do on windows? in Windows drive C is labeled as "WINXP" and D as "DATA-01". I would like to name them since I plan on adding more hard disks to run at once and they all have specific names containing different data.

---

### Post by nothingspecial on 2010-05-07
```
sudo apt-get install ntfsprogs
```

Then figure out which partition is which

```
sudo fdisk -l
```

I`m going to imagine that fdisk says that your C drive is /dev/sdb1 and your other one is /dev/sdc1 but you will have to change the commands to the correct /dev/sd??

Unmount both partitions - click the eject buttons in the places menu.

```
sudo ntfslabel /dev/sdb1 WINXP
sudo ntfslabel /dev/sdc1 DATA-01
```

Done.

---

