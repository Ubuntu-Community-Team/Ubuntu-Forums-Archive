---
title: "Hidden Fat32 'stealing' disk space?"
date: 2009-12-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JKPM on 2009-12-27
Hi there,

I have recently purchased a Dell Inspiron 10v running Ubuntu 8.04.  I was having a look at Disk Usage Analyzer and noticed that my total filesystem space was around 6Gb, which is 2Gb short of the quoted size of the 8Gb solid state disk.  I have a look at the partition set-up with fdisk and then GParted and have discovered that there is a partition '/dev/sda3' that is hidden and of type HIDDEN W95 FAT32.  Furthermore, it is almost 2Gb in size and is amost three quarters full.

The computer as purchased from Dell was a Ubuntu-only system.  However, would anybody have any idea as to why this partition is present?  Furthermore, there is apparently nearly 2Gb of data within this partition and I have no idea as to what this is.  Also, due to this hidden partition, it would appear that 2Gb of the disk is essentially inaccessible to me as a Ubuntu user.  For your information, the fdisk output is as follows:

Disk /dev/sda: 8012 MB, 8012390400 bytes
255 heads, 63 sectors/track, 974 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           3       24066   de  Dell Utility
/dev/sda2   *           4         791     6329610   83  Linux
/dev/sda3             792         974     1469947+  1b  Hidden W95 FAT32

Thanks for your help.

---

### Post by diablo75 on 2009-12-27
Typically partitions like this are built-in recovery partitions which house a fresh copy of Ubuntu and any other software that came pre-loaded with the system.  I'm going to assume that you're using a netbook that doesn't have a CD-ROM.  While you could easily reinstall from a USB drive if you wanted, Dell probably did the majority of their customers a favor by making restoration as easy as a few keystrokes... Now that I think about it, it saves their tech support department a lot of trouble, too.  Imagine calling them up and telling them "I formated my SSD and don't have any USB sticks or a spare computer sitting around.  What should I do?"  They'd tell you to mail it in... you wouldn't want to do that.

You could easily get away with deleting this partition and expanding the ext partition that houses your Linux install, but you'd be on your own if something went foul with your system and you had to reinstall from scratch.  Make a Live USB stick with another computer and that can be your Plan B.  You should also be able to make a live Gparted USB stick for the purpose of deleting the FAT32 and expanding the ext, should you choose to do this.  Again, do so at your own risk.

---

### Post by JKPM on 2009-12-27
Thank you very much for this information.  This would certainly make sense.  The Netbook did come with a DVD and I have duly purchased an external optical media drive anyway.  While this would seem a pragmatic thought by Dell, their lack of information regarding this is not so good, as essentially they are offering an 8Gb drive, but only making a subset of this accessible without a [potentially tricky] repartition.

Thanks again for your response.

---

