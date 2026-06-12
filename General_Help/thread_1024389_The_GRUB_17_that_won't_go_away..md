---
title: "The GRUB 17 that won't go away."
date: 2008-12-29
forum: General Help
---

### Post by ZimZam on 2008-12-29
Howdy.

I have a GRUB problem that I can't seem to figure out, usually it's a non issue, but this time I'm stuck.

I have a dual boot with XP on a SATA HDD and Heron on a IDE HDD, both are in Partitions of their respective HDD. Long story but I had 8.10, I got a GRUB error (which wasn't 17 but I can't remember which) went through a cycle of Fixboot/FixMBR/Bootcfg in XP but then just got a GRUB 17.

I deleted the entire partion that 8.1 was installed on, then redid a FixMBR/Boot/Bootcfg and still had the Grub 17. I reinstalled with 8.04 and then on reboot got the GRUB 17 error again.

Right now the only way that it will boot is if the XP CD is in the CD Drive, then it will give me the GRUB menu with two seperate Linux Kernels and my XP Partition, I can log into my Ubuntu and XP Partitions fine from here.

The theory I'm running with is that it's a mapping issue, however I have tried KGRUBE and QGRUBE and both give different results for the mapping. The other thing that it looks like is that there could be two different GRUB installations? Is that even possible?

I have attached three docs

The results of FDISK -lu
The GRUB menu.lst 
caljohnsmith's bootinfo.txt file from this thread here [http://ubuntuforums.org/showthread.php?t=1014256&page=2](http://ubuntuforums.org/showthread.php?t=1014256&page=2) 

Can anyone shed some light on this for me?

---

### Post by caljohnsmith on 2008-12-29
According to the boot info results you posted, for some reason your Windows sda drive still has Grub in the MBR even though you ran "fixmbr" from the Windows CD. How about from your Live CD do the following:
```
sudo lilo -M  /dev/sda mbr
```
Then reboot, and you should be able to boot Windows (assuming Windows itself doesn't have any issues). How about giving that a shot and let me know how it goes.

---

### Post by ZimZam on 2008-12-30
Hi.

I don't have Lilo installed, so it won't run the command. I get the option to apt-get but it's not there by itself.

Cheers

---

### Post by caljohnsmith on 2008-12-30
> **ZimZam said:**
> Hi.

I don't have Lilo installed, so it won't run the command. I get the option to apt-get but it's not there by itself.

Cheers
Do you have internet connectivity in Ubuntu? If so, how about going ahead and install it:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```

---

### Post by ZimZam on 2008-12-30
Hi.

I installed Lilo from my Ubuntu partition and executed the command, now the system boots directly into XP but no longer presents Grub, so although my Ubuntu partition is still there I can't boot into it.

Thanks

---

### Post by caljohnsmith on 2008-12-30
How about going into your BIOS and change the boot order so that the IDE Ubuntu drive gets booted before the SATA XP drive, and then you should get the Grub menu where you can choose Ubuntu or XP. Your Grub's menu.lst is currently configured to boot from the IDE drive, so you should be fine.

---

