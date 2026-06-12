---
title: "dual boot ubuntu/windows 7 - not enough disk space when upgrading"
date: 2010-11-15
forum: Desktop Environments
---

### Post by week_man on 2010-11-15
Im new to ubuntu and I used the ubuntu windows installer:
[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

and im dual booting windows 7 and ubuntu 10.4. Im trying to upgrade ubuntu to 10.10 and every time i try, the updater says i don't have enough disk space even though my hard drive is not even half way full.

here's some of the disk info:
sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xabe056f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1044     8381440   27  Unknown
/dev/sda2   *        1044       30402   235814072    7  HPFS/NTFS
weeks@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G   16G  232M  99% /
none                  2.0G  332K  2.0G   1% /dev
none                  2.0G  296K  2.0G   1% /dev/shm
none                  2.0G   88K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda2             225G   96G  130G  43% /host

i realize the /host is the windows, and the / is ubuntu but ubuntu is installed under the same partition as windows and i cant add any space to it. How can i get ubuntu to recognize i have more space? Or, a better question is what should i do so it can upgrade?
a screenshot of what gparted says is attached.

Thanks for any help you can give!

---

### Post by gordintoronto on 2010-11-15
Your Ubuntu file system is contained within a Windows file, and it's too small. I wouldn't use this setup (WUBI install) for anything but evaluating Ubuntu. Issue 41 of Full Circle magazine includes instructions on how to use Windows 7 to free up space to create a normal partition for Ubuntu.

If you don't want to do that, I would back up my Ubuntu data onto the Windows partition (or maybe a DVD) and remove the WUBI install. Then you could do another WUBI install of 10.10, then restore the data. You might want to give Ubuntu more space this time.

---

### Post by bcbc on 2010-11-15
And don't upgrade the wubi install to 10.10. There is a bug in the upgrade (documented in the release notes) that hasn't been fixed  (and probably won't be anytime soon).

There really is nothing different in 10.10 that is that different that is worth upgrading from 10.04 anyway - unless you have a specific hardware issue that you need a newer kernel to fix.

If you want to migrate your wubi install to a partition - create the partitions and then use this howto [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

