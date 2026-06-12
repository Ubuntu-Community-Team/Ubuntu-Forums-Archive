---
title: "Can't boot Ubuntu partition."
date: 2007-05-12
forum: Desktop Environments
---

### Post by bchymist on 2007-05-12
I have been running dual boot on my system for a while with Ubuntu 64 and Win XP Pro. I removed an extra DVD drive I had on my system and all of a sudden Ubuntu wouldn't boot anymore. I replaced the drive and still had the same problem. I have 2 hard drives (both 80GB) and I have the last 10gigs on my first drive devoted to Ubuntu. Now Ubuntu keeps telling me that it can't find hda2, any ideas on what might be the problem and how to fix it? At the very least I would like to be able to recover some pictures off that partition. Other than those there is nothing of any great value on that partition. If I can get those I'll simply wipe the partition and reinstall.

---

### Post by Steven_B on 2007-05-12
Is GRUB still starting?
Try booting a live CD, and then mount your hard drives.  You should be able to do this by clicking on the "x GB Volume" icons in "computer:///".  From there, you should be able to explore the drives and save files off to a network location or CD/DVD.
It may also be that you can use the live CD to edit GRUB's menu.lst to point to the wherever the kernels are.

---

### Post by phidia on 2007-05-12
If you have the live cd you can try and boot from that and open a terminal and type fdisk -l
That should output your hard drives. 

Obviously, or it appears like something went whoops when you removed the extra optical drive-it sounds like removing the drive changed how the drive order is seen by grub, but you didn't give your system specs and I don't know why it would affect the hda drive. Are your optical drives sata?

So if you have the livecd and find your missing install with the fdisk command you can then use mkdir and mount to access that partition. Good luck.

---

### Post by redtrak on 2007-05-12
If its a Grub problem try Super Grub Disk which is a bootable cd (or floppy) that makes repairing grub rather easy. you get get it here [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by bchymist on 2007-05-18
I think it may be a Grub problem. The only thing that concerns me is that I can't mount my linux drive. When I boot normally through Grub it won't mount the root file system and when I boot through the live CD I can't mount it either. Any ideas on that?

---

### Post by bchymist on 2007-05-18
ok, I've booted to my live CD but I still can't mount my linux partition. It is hdc2 with the live DC boot but is normall hda2 in a regular boot and I can't mount it. The Super Grub Boot disk didn't help and I've tried to mount the device using the methods mentioned here. For some reason when I try mounting it the system will not find the mount point. I can mount all my other partitions except that one. hdc1 (my Windows partition) will mount and hdd1 (another NTFS FS) will also mount. hdc2 is a ext3 partition and it will not mount no mater what I try. Anyone got any ideas? Should I just give up and consider my files lost?

---

### Post by bchymist on 2007-05-18
Ok, well, that solves everything. The partition seems to be corrupt. My Windows based partition utility won't even read the properties of it. It will read all the other partitions but not thatone. It shows the amount of space on it and the amount availalbe but that's it.

---

