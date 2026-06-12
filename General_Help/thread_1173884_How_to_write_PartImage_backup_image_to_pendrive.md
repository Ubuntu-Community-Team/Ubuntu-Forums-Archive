---
title: "How to write PartImage backup image to pendrive?"
date: 2009-05-30
forum: General Help
---

### Post by Pipps on 2009-05-30
I receive the following error message when trying to use the SysRescCD to write a PartImage backup to a recently reformatted pendrive:

> Error: Cannot create temp file [/media/partimage/pi650e1e82.tmp]
Please check there is enough space and you have access rights."

(Where: '/media/partimage' is a folder within the mounted pendrive.)

I do not understand why I receive this error message, as:
- There is 4.0GB free for backing up my 100MB image.
- I have already performed 'chown' on the pendrive from the 'root@sysresccd' prompt, prior to running PartImage.

Please tell me where I am going wrong!

---

### Post by Pipps on 2009-05-30
Can anyone help me?:oops:

---

### Post by drs305 on 2009-05-30
Skip all this: go to Post #10 for the solution.

Normally error messages like this are the result of mounting the wrong backup partition or designating the wrong partition to back up. 

You might try following the instructions in this link to ensure you have set up the instructions properly:
[http://www.debianadmin.com/backup-and-restore-linux-partitions-using-partimage.html]("http://www.debianadmin.com/backup-and-restore-linux-partitions-using-partimage.html")

---

### Post by Pipps on 2009-05-30
Thank you for your advice.

---

### Post by Pipps on 2009-05-31
I have consulted the recommended PartImage usage instructions. It has confirmed to me that I have been doing everything right in that respect.

However, I am still receiving the 'permissions' error message when I try to create a backup image in a directory on my external USB drive. Why am I receiving this message?

Can i 'chown' the drive to give me the permissions I need to write to it?

Can anyone help me please?

---

### Post by Pipps on 2009-05-31
At the PartImage 'root@sysresccd / root %' prompt, I try each of the following three commands:
- touch /media/partimage
- chown root /media/partimage
- chmod 666 media/partimage

And each time, I receive the following error message:
'Changing permissions of 'media/partimage': Read-only file system'

How can I grant PartImage root access rights to this directory?

If root cannot grant access rights, then who can???

Please help!!

---

### Post by drs305 on 2009-05-31
Are you sure this external drive is formatted as ext3? Please post the results of:
```

sudo fdisk -l
mount | grep "sd"
ls -la /media/partimage

```

---

### Post by Pipps on 2009-05-31
Thank you for your reply.

The external drive comprises a single 500GB NTFS partition.

I am currently running in Ubuntu Live USB mode, and the output of the commands which you have kindly provided ae as follows:

```
**sudo fdisk -l**

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd9d9d9d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7380    59279818+   7  HPFS/NTFS
/dev/sda2            8419        9729    10530607+  83  Linux
/dev/sda3            8176        8418     1951897+   5  Extended
/dev/sda4            7381        8175     6385837+  83  Linux
/dev/sda5            8176        8418     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 1002 MB, 1002438656 bytes
255 heads, 63 sectors/track, 121 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x006beaa5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         122      978912+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(120, 254, 63) logical=(121, 222, 37)

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae82b228

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001    7  HPFS/NTFS

```

My external drive is located at /dev/sdd1.

```
**mount | grep "sd"**

/dev/sdc1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/sdd1 on /media/LG_EXT_HDD type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
```

And to make the third command work, I had to mount sdd1 at the appropriate mount-point. So I did the following:

```
sudo su
umount /dev/sdd1
mkdir /mounter (as '/media' and '/mnt' already exist as mount-points)
mount /dev/sdd1 /mounter
cd /mounter/partimage
ls -la /mounter/partimage
```

```

**ls -la /mounter/partimage**

total 8
drwxrwxrwx 1 root root    0 2009-05-31 09:48 .
drwxrwxrwx 1 root root 8192 2009-05-31 09:48 ..
```

I look forward to hearing what you think. Thank you for your help.

---

### Post by drs305 on 2009-05-31
Once again, this turned out not to be the issue. The problem was mounting an NTFS partition while running the SystemRescueCD. Go to Post #10 for the solution.

Thank you for posting that information. The mounting of sdd1 appears normal and you *should* be able to read/write to it.

Since you are trying to back up this image on an NTFS drive, I suspect one of two issues: permissions or file system problems.

Can you change or add any files to the external drive? 

There have been several posts recently of non-linux drives becoming read-only. If changing the mount options doesn't solve the problem, my guess is the problem is a corrupted NTFS. 

For NTFS, you may get an unclean shutdown error message when attempting to access the partition. It is corrected by 1) remounting and then using the "Safely remove" option in Windows or 2) installing ntfsprogs and running "ntfsfix" on the affected partition. You didn't report seeing this message but I thought I'd mention it in case you did.

For many other NTFS problems and definitely for FAT32 read-only issues, the read-only problem has been difficult to solve without reverting to backing up data to another location and then reformatting the partition. 

Specifically to your situation, as long as you can't copy or edit anything to this partition using "sudo" you are not going to be able to do it with partimage either. If root can't access the drive in normal operations, it won't work in partimage either.

Note 1: "chown": For NTFS/FAT32 file systems which do not support permissions, the owner and permissions are set at the time of mounting. There are various mount options that can establish who the owner is, who can access the files, etc. Once mounted, you can't change these settings. So running *chown* or *chmod* will have no effect.

Although this external drive should automount, try unmounting it and mounting manually so we know the exact parameters it's mounted with:
```

sudo umount /dev/sdd1   # change if sdd1 is not your backup partition.
sudo mount /dev/sdd1 /mounter

```

This command mounts the device as root, with rw ability for you. Now, *as root*, try to add or edit any file on /mounter. You can use "sudo" with an applicable command in terminal or open nautilus with "gksudo nautilus /mounter" and try to add or edit a file that way. We are trying to do this as root since you will be "root" when running partimage.

Report back if you are able to modify any files in this manner.

Note 2: I noticed the external drive is mounted as "LG_EXT_HDD". Is that a label you gave it? If not and you prefer some other label, once you can make changes to the partition, you can use gparted to change the label. Open gparted ("gksu gparted" or System, Administration, Partition Editor), select the partiton, then Partition, Label and enter the new name. I recommend no spaces in the name.

You can also label it this way:
```

sudo apt-get install ntfsprogs
sudo ntfslabel /dev/s[COLOR="DarkRed"]dd[/COLOR] [COLOR="DarkRed"]newlabelname[/COLOR]

```

I replied to your PM. Please check your Inbox.

---

### Post by drs305 on 2009-05-31
The Solution:

Using the [SystemRescueCD]("http://www.sysresccd.org/Main_Page"), which includes Partimage 0.6.7, you must mount an NTFS partition a bit differently that a normal NTFS mount in linux.

The command to mount an NTFS backup partition from a SystemRescueCD is:
```

ntfs-3g /device  /path.to.mountpoint

```
Example:  ntfs-3g /dev/sdb1 /media/backup

Of course the mount point must be created and the backup partition mounted at the command prompt of the SystemRescueCD before running Partimage.

Thanks to Pipps for putting up with an extended IM session to figure this out.

---

### Post by Pipps on 2009-05-31
Thanks to Mr DRS for being the kindest and most helpful person I have ever met on the UbuntuForums, or anywhere!

Thank you! :)

---

