---
title: "reformatting usb hard drive"
date: 2009-02-14
forum: General Help
---

### Post by djhvt on 2009-02-14
hello all. Well i have finally said good bye to apple and am solely on Ubuntu now. I just yanked my 60 gig hard drive out of my old mac laptop to be used as a usb storage device in my nice shiny new usb case. Any idea as to the most strait forward way to blank this of the old mac file system and make it so i can read and write to the disk regularly without a hitch under Ubuntu?

I thank everyone in advance, these forums rock:guitar:

---

### Post by ugm6hr on 2009-02-14
Format as ext3 (Gparted) and automount on boot:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by djhvt on 2009-02-15
since i wasn't setting up a partition on my primary drive, but rather reformatting an external drive in its entirety for storage i got a bit turned around with that tutorial. The good news is i WAS able to use gparted to have only one ext3 partition with nothing on it....but i messed up the permissions part and now i cant write to the disk, just view it. If i go into the properties of the drive it says the permissions could not be defined. Any ideas in those huge pulsating brains out there? As always thanks so much in advance:KS

---

### Post by djhvt on 2009-02-15
ok so i reformatted it to fat32. now it automatically mounts on both my ubuntu laptop, and my works xp machine. i also can view the permissions, but cant change them as they are set to Root. How do i make it so its not set to root and anyone could use it?

---

### Post by ugm6hr on 2009-02-15
Post the output from:
```
sudo fdisk -l
cat /etc/fstab
cat /etc/fstab_backup
```

And tell us where you want the HD mounted
(e.g. /storage or /media/storage)

And we'll edit those commands for you specific scenario.

The fact that you are using a single partition on a HD rather than multiple partitions is irrelevant.

---

### Post by sonu 1807 on 2009-02-15
format it as FAT 32 on XP.... I had the same problem with my pendrive... now its working

---

### Post by djhvt on 2009-02-15
thanks for your continued speedy help! Im thinking /media is fine. Here is the code that came out:

aftertwilight@aftertwilight-laptop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b75e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7132    57287758+  83  Linux
/dev/sda2            7133        7296     1317330    5  Extended
/dev/sda5            7133        7296     1317298+  82  Linux swap / Solaris

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002a362

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7296    58605088+   b  W95 FAT32
aftertwilight@aftertwilight-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=90c480e5-3292-47de-badd-b0a690289e57 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2e1527ad-ea66-4887-a351-e050cf8cc193 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by ugm6hr on 2009-02-15
Did you want to stick with fat32 (to allow easy use with Windows / Mac), or ext3 (for predominantly Linux only)?

---

### Post by djhvt on 2009-02-15
Sonu,

Unfortunately i cant reformat or do really anything beyond the basics on my work computer because my employer has locked me out of everything for "productivity reasons"....interestingly he left all 9 of the games on the computer, and left us with unrestricted internet access though lol

Anyway i have completely shifted to Ubuntu for my personal computing needs and only occasionally run into these "duh" moments, so id like to know what to do if i run into this problem in the future. i like to learn, and darn it i want some crazy coffee title like the grand masters on here have someday lol

---

### Post by djhvt on 2009-02-15
ugm6hr,

 ya i think ill stick with Fat32 so i can use it on the widest array of computers. thanks again!

---

### Post by ugm6hr on 2009-02-15
Look at this: [http://ubuntuforums.org/showpost.php?p=6646629&postcount=7](http://ubuntuforums.org/showpost.php?p=6646629&postcount=7)

Select /dev/sdb

I'd suggest you change the label to something memorable (e.g. OldMacHD) for sdb1 (this will ensure you recognise it whenever you plug it in).

Ensure you formatted to -> fat32

When you reboot, it should appear in Nautilus as OldMacHD (or whatever you called it) in left column.  Double-clicking will mount it, and should allow whichever user mounted it (i.e. you) to read & write.

fat32 does not have actual permissions, so anyone can write to it.  The reason that you don't have permission to access it at the moment is probably because it was mounted by GParted, which is always run as root.  Hence, the mountpoint was set with root permissions.  I suspect that unmounting in GParted and then remounting in Nautilus will allow you access to it (or rebooting).

---

