---
title: "Grub Error 17 After Failed Windows Install"
date: 2009-03-18
forum: General Help
---

### Post by jackace32 on 2009-03-18
Ok before you say "Check this out instead" I've already tried debugging with this guide: ([http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)) and can't save Menu.lst and can't update device.map. Turning off LBA / Large mode causes my BIOS to hang up upon boot, not passing "Checking NVRAM...".

Well I recently had to format my Hard Drive due to corrupted sectors. So I only had a Win7, Ubuntu and various stress test disks available. So I installed ubuntu, downloaded a Windows Vista Ultimate CD and tried to install it (After making various partitions in GParted, see screenshot below). So windows says "Windows Cannot find a partition that meets it's installation requirements" or something. Assuming it was the wrong Format I then deleted & re-created the Primary Windows partition on the disk (Located on the outer rim). Then I gave up and got GRUB Error 17 when I booted. I am now running Ubuntu Live. I really don't want to re-install Ubuntu, because I already have so much custom stuff on here. Also I am willing to install Win7 Beta for the time being.

Thank you
Jake

---

### Post by meierfra. on 2009-03-18
To get back into Ubuntu, you probably just need to reinstall grub. Boot from the LiveCD, open a terminal and type

```
sudo grub
```
and at the "grub>" prompt:

```
root (hd0,3)
setup (hd0)
quit
```

reboot and hope for the best.

---

### Post by jackace32 on 2009-03-18
Ok, it worked, thanks. Now I have Win7 and no way to boot into that... no permissions to save menu.lst. will Google.

---

### Post by MaindotC on 2009-03-18
Windows 7 is on one of the partitions - I'm assuming /dev/sda2 based on your screen shot.  All you have to do is tell Grub that this partition exists and where to look to try and boot to it.  From the menu.lst file:
```

# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1

```

This is saying that the windows parition is on (hd0,0).  You also have a file called device.map.  This file translates (hd) partitions to /dev/sd* partitions.  For example, (hd0,0) should be the equivalent of /dev/sda1, (hd0,1) should be equivalent of /dev/sda2, (hd1,0) should be the equivalent of /dev/sdb1, and so on.  Find out which partition equates to the win 7 partition (using sudo fdisk -l) and place an entry in grub similar to the above example.  Worst case scenario Grub won't be able to boot it and bring you back to the menu to select a different partiton.

---

