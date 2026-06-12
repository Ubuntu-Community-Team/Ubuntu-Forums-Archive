---
title: "File system fragmentation and Linux filesystems"
date: 2005-08-23
forum: Desktop Environments
---

### Post by blueturtl on 2005-08-23
Well I've searched the web and these forums and a lot of the stuff I read sums up as the following:

1. EXT2 and EXT3 do not fragment considerably unless the volume fills up.
2. ReiserFS or Reiser4 does not fragment, period.
3. GNU/Linux does smarter placement of files than Windows.
4. There are no safe and well known defragmenters available for Linux on the count of 1.
5. FSCK reports file system errors and fragmentation rate.
6. Fragmentation can be fixed by moving files around or resaving them

I have two main partitions on which I put user files, and the other one is reported to have 9.5% non-contiguos inodes (can someone explain nodes / inodes btw?).

Call me paranoid, but even with mild fragmentation over a long period of time I find it odd that there is no tool to fix fragmentation on a Linux FS. #6 is a bit of a lame. If a partition has a lot of data on it, it doesn't make sence to just go moving files around. Even between hard-disks data transfer takes time and we don't all have the luxury of space required to completely defragment a large volume like this (say moving 30 gigabytes worth of files back and forth)!

If someone is more educated on the subject I'd appreciate their opinion or suggestions on the matter.

---

### Post by jasmuz on 2005-08-23
Check these links out they might shine some light over the issue:

[http://www.linuxgazette.com/issue68/dellomodarme.html](http://www.linuxgazette.com/issue68/dellomodarme.html)

[http://linux.org.mt/article/filesystems](http://linux.org.mt/article/filesystems)

[http://www.science.unitn.it/~fiorella/guidelinux/tlk/node94.html](http://www.science.unitn.it/~fiorella/guidelinux/tlk/node94.html)

---

