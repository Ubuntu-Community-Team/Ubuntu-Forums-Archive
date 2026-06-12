---
title: "Want to move Wubi to an external hard drive"
date: 2009-02-16
forum: General Help
---

### Post by SBDxAric on 2009-02-16
**If your like me andwant to skip the story, just go down to the numbers.**

So I recently installed Ubuntu on my desktop (on a partition) and i loved it! I then introduced it to my friend who installed Wubi on his laptop. He likes it too, and wanted to increase its size. He had 8.10, so after multiple uses LVPM didnt work. So he decided he wanted to put it on a partition. OProblem is he doesnt have the space to make a swap partition equal to his RAM so he went out and bought a WD Hard Drive from Best Buy. He now wants

1.Wubi to be transferred to his hard drive
2. For it to be a "full installation" ( like on its own partition and not dependent on Windows)

My question is: How should we go about doing this?

---

### Post by SBDxAric on 2009-02-16
Oh also he is running Windows XP MCE (i am too)

---

### Post by SBDxAric on 2009-02-17
No help? Is this in the wrong section?

---

### Post by lvleph on 2009-02-17
There is a script that you can use to migrate wubi to any drive. You will have to partition the drive first and then use the script to migrate. Here is the directions from the [WubiGuide](https://wiki.ubuntu.com/WubiGuide).
> Existing Wubi/Lubi installations can be upgraded to an installation on a dedicated partition via LVPM. The main site for LVPM is at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html) and the guide and support forum is at [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591).

As an alternative, the following script can be used with Wubi 8.04.

Download [wubi-move-to-partition](https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=wubi-move-to-partition)

Open a terminal and run:

sudo sh wubi-move-to-partition /dev/sda9 /dev/sda10

Replace /dev/sda9 with the partition where you would like to migrate the Wubi installation to, and /dev/sda10 with the appropriate swap partition (you can omit the second argument completely, in which case no swap will be setup). The two partitions must already exist and be empty (you can use any partitioning tool such as gparted to create them in advance). Note that the script will install grub as main bootloader replacing the existing bootloader, and it may not be easy to undo the changes (if things do not work as expected you will have to boot from a Live CD and replace/edit the bootloader manually). Also note that if you have multiple hard-disks, the disk order might have to be adjusted manually. 

---

### Post by SBDxAric on 2009-02-17
Thank you, will check it out right away

---

