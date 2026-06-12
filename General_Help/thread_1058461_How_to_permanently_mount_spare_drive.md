---
title: "How to permanently mount spare drive"
date: 2009-02-02
forum: General Help
---

### Post by Stolea on 2009-02-02
I got a spare 40gig drive on my system. It is formated ext3. I want to use it for my system backups. Currently my backups are on /var/backups, but it uses a lot of disk space which causes problems. Hence my plan to use the spare 40gig drive.
How do I make this drive a permanent part of the system?

---

### Post by cdtech on 2009-02-02
Just add it to your fstab file. You'll need to know which device it is. Open a terminal and post the output of:
```
sudo fdisk -l
```
This needs to be done with the device plugged in.......

---

### Post by Stolea on 2009-02-02
this is my disk setup:

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92e392e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4870    39118243+   5  Extended
/dev/sda5               1        4870    39118212   83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe47de47d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         122      979933+  83  Linux
/dev/sdb2             123       24321   194378467+   5  Extended
/dev/sdb5             123        2554    19535008+  82  Linux swap / Solaris
/dev/sdb6            2555        6201    29294496   83  Linux
/dev/sdb7            6202       24321   145548868+  83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8e3f8e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sdc2            2551       38913   292085797+   f  W95 Ext'd (LBA)
/dev/sdc5            2551       37383   279796041    7  HPFS/NTFS
/dev/sdc6           37384       38913    12289693+  17  Hidden HPFS/NTFS

---

### Post by todak on 2009-02-02
Try this: [https://help.ubuntu.com/community/InstallingANewHardDrive/#Create A Mount Point](https://help.ubuntu.com/community/InstallingANewHardDrive/#Create A Mount Point) and see if it helps ;)

---

### Post by cdtech on 2009-02-02
You would need to make a directory to mount your partition (drive):
```
sudo mkdir /mnt/backup
```
And this would go into your /etc/fstab:
```
/dev/sda5 /mnt/backup ext3 relatime   0   2
```
Then mount it using:
```
sudo mount -a
```
Then you could just move all of your existing data from /var/backup to /mnt/backup:
Either cp, or tar to copy the old data to the new partition:
```
$ cd /mnt/backup
$ cp -pr /var/backup/* .
```
or tar and move it over:
```
$ cd /var/backup
$ tar cpf /mnt/backup.tar ./*
$ cd /mnt/backup
$ tar xpvf backup.tar
```
Then once **your sure** you have moved all of your data to the new location, you can remove the old backup directory:
sudo rm -R /var/backup

---

### Post by Stolea on 2009-02-03
Cheers guys, your blood is worth botteling. It worked a treat. Thanks

---

### Post by cdtech on 2009-02-03
Good luck.......

---

### Post by pbpersson on 2009-02-03
> **Stolea said:**
> Cheers guys, your blood is worth botteling. 

Is that a saying in Australia?  Here in the states, it makes you sound like an Ubuntu Vampire  :o

---

### Post by cdtech on 2009-02-03
Wouldn't that be Ubampire?

---

### Post by Stolea on 2009-02-03
I must admit I have always had problems trying to work out where that expression came from. Transylvania perhaps:evil:

Something you guys might be able to answer:
My Ubuntu is set up as /boot 1gig, /root 30gig, /swap 20Gig, /home 138gig. I have /windows 320 on a separate drive and got a permenantly mounted windows drive that lives on another machine

This configuration has worked flawless until a couple of days ago when VMware said it didn't have enough room for its temp files (/tmp/vmware-peter)
I went and got rid of unnecessary files and freed up 150meg. I have now created the backup drive as set out in the post and that got rid of 17gig of backup files to the new drive.
However the partition manager tells me that I still have only 50mb free space on the drive. And Vmware certainly still is complaining about the lack of space.
Any suggestions?

---

### Post by cdtech on 2009-02-04
> My Ubuntu is set up as /boot 1gig, /root 30gig, /swap 20Gig, /home 138gig. I have /windows 320 on a separate drive and got a permenantly mounted windows drive that lives on another machine
You must mean 2G for your swap. That would be way overkill for 20G.

Using "df -h" will show you the partitions and amount used. This command will give you an idea which files are eating up your disk space, Top disk usage:
```
sudo du -s ***** | sort -k1,1rn | head
```
The bold is the directory to check, ie.. /home/user - /var, the asterisk checks the entire filesystem.

---

### Post by Slim Odds on 2009-02-04
> **cdtech said:**
> You would need to make a directory to mount your partition (drive):
```
sudo mkdir /mnt/backup
```And this would go into your /etc/fstab:
```
/dev/sda5 /mnt/backup ext3 relatime   0   2
```Then mount it using:
```
sudo mount -a
```Then you could just move all of your existing data from /var/backup to /mnt/backup:


/mnt is really meant for temporary mounts.

Why not just mount the new backup drive to /backup  ?

---

### Post by cdtech on 2009-02-04
Any filesystem mounted via the /etc/fstab file is considered temporary. By using the generic mount point /mnt for all of your devices or partitions keeps from littering your filesystem with mount-points. Your not forced to use the /mnt directory, I myself mount my backup device to a top level /backup directory which I mount only during backups and umount afterwards. I just feel it's more of an orginizational thing (from my point of view) keeping your mounted filesystems in one location.

---

### Post by Slim Odds on 2009-02-04
> **cdtech said:**
> Any filesystem mounted via the /etc/fstab file is considered temporary.

This is **not** true.

/etc/fstab is what defines the persistent mount points.

---

### Post by Stolea on 2009-02-04
I spent some time reading up on this and discovered that the room had been gobbled up by some trash file in /root/.local/share/trash.
It would appear that when you delete files with sudo nautilus it creates a trash file as any normal deletion does. However this trash file is hidden in /root/.local/share/trash. Aparently you have to "shift-delete" a file to bypass the trash can. I had a bit of hassle getting rid of the files but finally succeeded.
see the attached link
[http://ubuntuforums.org/showthread.php?t=1059439](http://ubuntuforums.org/showthread.php?t=1059439)

One never stops learning. And its fun to find something new.
Cheers all

---

