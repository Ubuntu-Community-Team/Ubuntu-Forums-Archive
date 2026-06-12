---
title: "Software RAID"
date: 2009-05-16
forum: General Help
---

### Post by themagicmanfromtrent on 2009-05-16
I've been following [this]("http://mywheel.net/blog/index.php/software-raid-in-ubuntu/") howto on how to set software RAID up on a jaunty install I have running.

The two disks I want to RAID are /dev/sdc and /dev/sdd, both identical WD 500GB Blue Caviars.

When I get up to this point:

```
fdisk /dev/hdX
```

I follow the instructions and enter the first and last cylinders of the HDD. I then select the type and quit, and it syncs and everything is hunky dory. I do it for both disks, yet when I enter gparted, I am told that although sdc has an "unknown raid partition", sdd is still showing unallocated space. Disregarding this, I continued to reboot, and tried to RAID them, and here's what I get:

```
danny@server:~$ sudo mdadm --create --verbose /dev/md1 --level=0 --raid-devices=2 /dev/sdc1 /dev/sdd1
[sudo] password for danny: 
mdadm: chunk size defaults to 64K
mdadm: Cannot open /dev/sdc1: Device or resource busy
mdadm: create aborted
danny@server:~$ 

```

I'm guessing I did something wrong at the fdisk stage, because neither disk is mounted.

NB: These disks are not the boot disks, nor do I plan on using them as boot disks. I also don't want to re-install, so unless there's a way of setting up RAID automatically without re-installing ubuntu, I'm forced to do it manually...

---

### Post by fjgaude on 2009-05-17
I would think you did something wrong in **fdisk** with creating the partitions on the two drives. Perhaps.

You do not have to re-install the OS to use **mdadm**. It seems that something is using /dev/sdc1... are you sure the two drives are not being used by some program?

Here's some links for info on software raid:

[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)
[http://linux-raid.osdl.org/index.php/Main_Page](http://linux-raid.osdl.org/index.php/Main_Page)
[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)

Good luck!

---

### Post by themagicmanfromtrent on 2009-05-17
Nope, wasn't mounted or anything. I just plugged in a PCI SATA expansion card, booted up Ubuntu, and it sees the disk in gparted with unallocated space. I close gparted and start the fdisk. I tried doing it through webmin as well, and it gave me the same error.

---

### Post by fjgaude on 2009-05-18
Say, try to format the drives using **gparted** instead of **fdisk**. I don't understand why you were using cylinders to partition.

If you have no data on the drives, I'd start over. The command you use for creating the array is correct but there is likely something else not right. Two SATA drives on the same controller should work.

---

### Post by themagicmanfromtrent on 2009-05-18
gparted doesn't let me format the disk. It deletes the partition, creates a new one, but when it comes to format it with ext3, it tells me that the device is busy.

---

### Post by themagicmanfromtrent on 2009-05-18
could this have something to do with the fact that I formatted the drives a couple of weeks ago with FreeBSD's UFS GPT?

---

### Post by fjgaude on 2009-05-19
Man, I'm out of my league when you start talking freeBSD and the like. Happy campin'.

---

### Post by fjgaude on 2009-05-19
Man, I'm out of my league when you start talking freeBSD and the like. Happy campin'. I think you have to use only Linux stuff.

---

### Post by themagicmanfromtrent on 2009-05-19
Aww Thanks anyways

---

### Post by themagicmanfromtrent on 2009-05-19
Aww Thanks anyways :P:P

---

