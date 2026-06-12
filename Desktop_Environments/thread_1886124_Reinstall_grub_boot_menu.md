---
title: "Reinstall grub boot menu"
date: 2011-11-24
forum: Desktop Environments
---

### Post by CJ_Hudson on 2011-11-24
Please, I had to reinstall Windows on one partition of my Hard Drive and now I can't get into Ubuntu on the other partition.
Please, how do I re install the boot grub menu where I can choose which OS I boot into?
Many Thanks in advance.

---

### Post by sudodus on 2011-11-24
Try to follow the instructions in the following link
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Good luck!

---

### Post by drs305 on 2011-11-24
The Boot Repair app mentioned in the previous link should do the job.

If you are already on the LiveCD and your Ubuntu files haven't been altered, you should be able to just restore the MBR to point to your Ubuntu partition (and Grub will overwrite the MBR Windows info). Do NOT use the partition number in the second command.

X is the drive (a,b,c etc), TY is the Ubuntu partition (1,2,3,5 etc)
```
sudo mount /dev/sd**XY** /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /dev/sdXY

```

Reboot and select Ubuntu. If the Windows OS doesn't appear in the Grub menu, after rebooting without the CD run:
```
sudo update-grub
```

---

### Post by neu5eeCh on 2011-11-24
My 2 Cents here.

I always keep a copy of Super Grub Disk available just for emergencies like these. You can find it [here]("http://www.supergrubdisk.org/"). 

It will find old grub configurations (even if they've been removed from the MBR), and allow you to boot into a given Linux OS (all else being equal).

---

### Post by neu5eeCh on 2011-11-24
One other thought - If you prefer a GUI environment, I recommend Grub Customizer. You can find it [here]("http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html"). If you use Super Grub Disk then, once in your Linux OS, you can install Grub Customizer and use the GUI environment to write Grub back to your MBR. Then again, using terminal is easy too (but less idiot proof).

---

### Post by CJ_Hudson on 2011-11-25
Thankyou all very much.

It works! (dances about the room)

Boot repair first time.

---

