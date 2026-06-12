---
title: "My fstab doesn't like Windows 7..."
date: 2009-02-15
forum: General Help
---

### Post by GlenboLake on 2009-02-15
My computer has been dual-booting XP and Ubuntu for some time now.  I have no problem booting into either OS, and I had my fstab set up so I could see the contents of my XP partition easily (automounting the XP drive).  Around a week ago though, I added a third partition: The Windows 7 Beta.  I tried to edit my fstab so I could mount the W7 partition from Ubuntu on login so I wouldn't have to go use sudo to do it, but for some reason, XP keeps getting automounted and W7 doesn't.  Here's my blkid output and my fstab:

```
glen@Apollo:~$ blkid
/dev/sda1: UUID="0010B08410B081E8" LABEL="C" TYPE="ntfs" 
/dev/sda2: UUID="604CA3634CA33328" TYPE="ntfs" 
/dev/sda3: UUID="3ace81fd-57b5-46ec-8993-32a0106923b9" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb5: LABEL="GIGANTOR" UUID="1BF7-3766" TYPE="vfat" 
/dev/sda4: UUID="48ab5d3c-6a71-4dd3-8ab3-5665373df667" TYPE="swap" 
/dev/sdb1: LABEL="GYGES" UUID="16F5-1356" TYPE="vfat" 
glen@Apollo:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1, Windows XP
UUID=0010B08410B081E8	/media/windows	ntfs	nls=utf8,user,umask=000,rw	0	0
# UUID=0010B08410B081E8	/media/windows	ntfs	uid=user

[B]# /dev/sda2, Windows 7
UUID=604CA3634CA33328	/media/W7	ntfs	nls=utf8,user,umask=000,rw	0	0[/B]

# /dev/sda3, Ubuntu
UUID=3ace81fd-57b5-46ec-8993-32a0106923b9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4, Swap
UUID=48ab5d3c-6a71-4dd3-8ab3-5665373df667 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```

/dev/sda1 is my XP partition.  I assume the one with no label must be my Windows 7 partition.  The bold part of fstab is what I just added, everything else was there before installing 7.  Windows XP also used to be identified as /dev/sda1 instead of by the UUID.  I partly changed it to the UUID to see if it would affect whether C automounted (it didn't).  How can I get Windows 7 to automount?


and as long as I have my blkid output in a thread... gigantor is an old external drive that I not only don't use anymore and don't have connected to the computer, but that's not even the drive label anymore.  It's been several months.  Does anybody know why it's still listed?

---

### Post by logos34 on 2009-02-15
try using ntfs-config

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by GlenboLake on 2009-02-18
Oddly enough, when I ran ntfs-config, nothing happened and nothing changed.  But then when I booted into Windows and back again, the problem solved itself....

---

