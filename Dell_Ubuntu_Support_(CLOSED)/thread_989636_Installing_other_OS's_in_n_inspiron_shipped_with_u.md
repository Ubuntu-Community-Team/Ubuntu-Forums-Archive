---
title: "Installing other OS's in n inspiron shipped with ubuntu"
date: 2008-11-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by geo909 on 2008-11-21
Hello everybody.

I have purchased a Dell inspiron 1525 laptop shipped with ubuntu.
I'm really happy with it though I had in my mind to install
some other OS's too. I was thinking about triple booting 
with ubuntu, arch or gentoo and windows XP.

Now that I got the laptop, I see that there are already too many 
partitions (You can see the partiotioning [here]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Default_Partitions"))

Also here is my fdisk:
```
jorge@dell-desktop:~$ sudo fdisk -l
[sudo] password for jorge: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2              11         402     3148740    b  W95 FAT32
/dev/sda3   *         403       14342   111973050   83  Linux
/dev/sda4           14343       14593     2016157+   5  Extended
/dev/sda5           14343       14593     2016126   82  Linux swap / Solaris

```

I was wondering what could I do with the partitioning.
It's getting too much.
I haven't understood yet what is the "utility partiotion" (sda1) and the extended partiotion (sda4)...

Before I got the laptop I had in my mind a small ext2 boot partition, a primary ntfs partition for Windows, a primary partition for Ubuntu, and a extended partition for Arch with smaller partitions for /home, /var etc..

Anyway, that seems to be too much.. There is also the swap partiotion..
Any recomendations? I'm not so familiar with complicated partitioning..

I was thinking about erasing all the extra partitions that the disk was set by default. I could make a [reinstall DVD]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/OS_Reinstallation") in case I ever want to make everything like when I received the laptop.

---

