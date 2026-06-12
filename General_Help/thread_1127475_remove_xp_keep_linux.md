---
title: "remove xp keep linux"
date: 2009-04-16
forum: General Help
---

### Post by disco41 on 2009-04-16
Hi all,

Its the title really bin using linux for 6 months now cant find anything that i did in windows that linux wont do ( apart from tomtom updates!)
Now i need to uninstall XP so i can use the hard drive for extra storage.
Help please anybody!;)

---

### Post by codeseer on 2009-04-16
I'd just fire up GParted, delete the XP partition and reallocate it under Ext3. Then you can mount it in /etc/fstab.

---

### Post by disco41 on 2009-04-16
Thanks for rapid reply what would happen to GRUB or would it just boot straight into Linux.

---

### Post by codeseer on 2009-04-16
> **disco41 said:**
> Thanks for rapid reply what would happen to GRUB or would it just boot straight into Linux.

You could remove the windows option:

```

gksudo gedit /boot/grub/menu.lst

```

---

### Post by lisati on 2009-04-16
If you do a fresh install of Ubuntu (don't forget to make backups of important data) using the "Guided: use entire disk" partition option will remove whatever is on your system. Note: This will also wipe recovery partitions.

---

### Post by disco41 on 2009-04-16
OK thanks should of said XP is on a 250gb ide drive and Linux is on seperate 250gb sata drive.
Grub presumibly installed in disc 1 containing XP,so just formating the ide drive should then let Linux boot itself?
sorry learning all the time i'll get there in the end ;)

---

### Post by codeseer on 2009-04-16
At worst, you may have to [reinstall Grub]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by disco41 on 2009-04-16
Cool thanks for info going to loose XP this weekend :D

---

### Post by satish_j on 2009-07-10
are you satisfied with the speed on Linux??
I mean how much time does it take to open a folder in nautilus
iam getting very much frustrated with the response time on Linux,otherwise Linux is good..

---

