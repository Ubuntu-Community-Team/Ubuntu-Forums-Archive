---
title: "NTFS broke"
date: 2009-05-05
forum: General Help
---

### Post by wolfestine on 2009-05-05
Hi,

I recently installed a copy of Ubuntu (Jaunty) and accidentally set an incorrect partition on which to install the grub on. I had intended to set it to the same partition as the installation, but it turned out that it was another partition, an NTFS one. Now this NTFS partition does not show up in Linux, and trying to mount it (haven't tried forced mount), fails. The drive does not open in windows either. Is there a way to recover the file system? I am not interested in recovering individual files. I have tried TestDisk and it could not find anything wrong with the partition. Also I would be grateful if someone could please explain to me why the NTFS partition got corrupted. Can't you install a grub on any drive, without ruining the file system?

Thanks

---

### Post by regor210 on 2009-05-05
There something here about mounting NTFS.

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Mounting_NTFS_Partitions_.28with_read.2Fwrite_privileges.29](http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Mounting_NTFS_Partitions_.28with_read.2Fwrite_privileges.29)

4.17.1

---

### Post by wolfestine on 2009-05-05
Thank you for replying, but I don't need help mounting the partition... I am capable of mounting drives. And just to be sure, that I hadn't forgotten how to mount drives, I tried mounting other NTFS drives, without any problems.

---

### Post by regor210 on 2009-05-05
What I would do if I were you is.

**WARNING** I have been told by others that they lost windows using FDISK /MBR . I have never had this problem so proceed at your own risk.
 
1st  I would restore the MBR using a Windows Boot disk.  C:    FDISK /MBR 
If all went well you should be able to boot windows . 

2nd I would reinstall Grub using a &#65279;Jaunty Live cd. I would try this howto first
.[http://www.tipstrs.com/tip/82/Restore-grub-after-installing-windows](http://www.tipstrs.com/tip/82/Restore-grub-after-installing-windows)


If  that did not work I would try using step five only here.
[http://webupd8.blogspot.com/2009/04/convert-your-ext3-file-system-to-ext4.html](http://webupd8.blogspot.com/2009/04/convert-your-ext3-file-system-to-ext4.html)

&#65279;
$sudo bash
$mount /dev/sda1 /mnt
$grub-install /dev/sda --root-directory=/mnt --recheck


The last time I used this to reinstall Grub I had to use /sdb1 as I have 3 hard drives and thats where Ubuntu is.

If all else fails try here.
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by wolfestine on 2009-05-05
Thanks for replying again, but I guess I didn't explain my problem properly. Booting is not a problem. I use Windows boot manager to load the grub, and I have grub installed on 3 different drives, and i also have grub in a pendrive for emergencies, not to mention syslinux in the other flashdrive. So booting is not a problem. The drive that I am not able to access was purely a data disk. Windows says that it is a raw disk, and wants to format it. Ubuntu says that I got the file system wrong when I try to mount it using the mount command.

---

### Post by wolfestine on 2009-05-06
Is there no solution to my problem???

---

### Post by wolfestine on 2009-05-06
What! No one here can help me??? :(

---

### Post by wolfestine on 2009-05-07
Crap... I guess I'll have to format the partition then.

---

