---
title: "TestDisk Help?"
date: 2009-04-20
forum: General Help
---

### Post by MrSootentai on 2009-04-20
I've recently lost my Ubuntu 8.10 EXT3 partition. I read from another forum poster that I could use TestDisk to recover my files. After running through the app and doing a 'deeper search', TestDisk showed that it found the drive ([http://img186.imageshack.us/my.php?image=screenshot10.png](http://img186.imageshack.us/my.php?image=screenshot10.png)). The drive is labeled with a 'D' and it's sector size is 301909545. After that I wrote the partition table, and labeled the found drive as 'P' (for primary), and the app told me I would have to reboot for the changes to take effect.
Problem is I've rebooted, and my Live Ubuntu (running off of my USB) install doesn't detect the Linux Partition that I am trying to access. Rather Gparted just shows it as an 'unknown partition'. Now the funny thing is, if I run TestDisk under a live ubuntu install I can't hit 'p' and list the files on the partition, but if I run it off of UBCD the files are listed, but my home directory is unviewable.

**My question is how do I go about to access this drive/recover it?** All I need is to access my home folder to recover some important school files.
Please any help is appreciated, and this is dire. I've recovered Vista/XP files from crashed partitions but I just don't understand what I am doing wrong here with the EXT3 partition.

Note:
Using Jaunty 9.04 x64 off of a USB drive, and running TestDisk in this environment.

---

### Post by jo4hnc on 2009-04-20
If it's any help, here is the testdisk homepage. 

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by MrSootentai on 2009-04-20
Thanks for the reply @jo4hnc, but I've searched through there for so long. I still can't find what I'm looking for so I decided to try to get some help here.

---

### Post by jo4hnc on 2009-04-20
Maybe PhotoRec would help.

[http://www.linux.com/articles/56588](http://www.linux.com/articles/56588)

---

### Post by MrSootentai on 2009-04-22
@jo4hnc
Thanks for the tip! I don't know why I didn't even think of using that, it was right there...
But anyways I've been playing with PhotoRec for the past few hours and I recovered well over 250,000 files. The problem was these files were nothing of what I wanted. I checked all the folders (after sorting them by extension type), and all the files were just misc files.
**I need to recover files from my home folder, but PhotoRec didn't do any of that. Is there anything else I can?**

---

### Post by jo4hnc on 2009-04-22
There are some other options in this post from a couple of months ago.

[http://ubuntuforums.org/showpost.php?p=6780152&postcount=7](http://ubuntuforums.org/showpost.php?p=6780152&postcount=7)

---

