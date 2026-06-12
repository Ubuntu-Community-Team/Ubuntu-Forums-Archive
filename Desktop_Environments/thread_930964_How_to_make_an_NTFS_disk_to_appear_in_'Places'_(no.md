---
title: "How to make an NTFS disk to appear in 'Places' (not in bookmarks)"
date: 2008-09-26
forum: Desktop Environments
---

### Post by zespri on 2008-09-26
Hello, can some one tell me why ubuntu can see only two if my three ntfs disks in 'Places'?
I can mount the missing disk allright, I can even set it up in /etc/fstab and add to bookmarks but it is not the same as the other two disk.
The other two disks are in 'Places' not in the bookmark section, they are absent in /etc/fstab and yet they are working. Is it possible to configure the third disk the same way?

Thank you in advance,
Andrew

---

### Post by zekopeko on 2008-09-26
post the output of

sudo fdisk -l 

and 

less /etc/fstab

---

### Post by zespri on 2008-09-26
Thank you,

here is the output, as requested:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
102 heads, 51 sectors/track, 120173 cylinders
Units = cylinders of 5202 * 512 = 2663424 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120173   312569947+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd2637c0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    1  FAT12

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70b80d50

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFS




```

sdb1 is in fact ntfs partition, not FAT as recognized by fdisk. And this is the one of the three that isn't displayed in 'Places' however if i issue
mount /dev/sdb1 /media/New
it does seem to mount allright and I have read/write access to it as expected.

And

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by zespri on 2008-09-27
Please let me know if there is anything I can add to the above to help troubleshoot the problem.

---

### Post by zespri on 2008-10-01
Still hoping for help...

---

### Post by Bucky Ball on 2008-10-01
The second post in this thread is a short description: 

[http://ubuntuforums.org/showthread.php?t=439196](http://ubuntuforums.org/showthread.php?t=439196)

More detailed:

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

Remember: unmount the drive (umount -a) before trying this and good idea to back up the fstab:

**sudo cp /etc/fstab /etc/fstab.backup**

... or whatever you want to call the backup in case of any unforeseen mishaps. :)

---

### Post by zespri on 2008-10-01
Thank you for your reply. Unfortunately this is not what my problem is. I can manually mount the drive successfully, and I don't require auto-mount as such. Also all changes to /etc/fstab work as expected. All I want, that my second drive (out of three) automatically appeared in 'Places' along with the rest.

---

### Post by Bucky Ball on 2008-10-01
> **zespri said:**
> All I want, that my second drive (out of three) automatically appeared in 'Places' along with the rest.

Unless it is auto-mounted I am not sure that it will. When you mount it manually it will appear on the desktop, as you have already found I imagine.

Mine are in 'Places' no problem, but they are all mounted by the fstab at boot. :)

Good luck with it.

---

### Post by zespri on 2008-10-03
And those of mine that are in 'Places' are not in fstab. As far as I understand ubuntu mounts them when you click on them for the first time.

---

### Post by Bucky Ball on 2008-10-04
> **zespri said:**
> As far as I understand ubuntu mounts them when you click on them for the first time.

Yup. What you would imagine ....

---

