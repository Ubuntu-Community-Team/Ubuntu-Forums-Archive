---
title: "Corrupted files / file system"
date: 2009-01-10
forum: General Help
---

### Post by jelevin on 2009-01-10
Ubuntu 8.10. Reboot failed, with suggestion to run fsck manually on a Raid-1 array. This ran with a ton of errors that presumably were fixed. After the next reboot the raid status was reported to be something like 98.5% for a bit. Now I see this message in syslog:

*Jan 8 18:17:08 computername kernel: [27946.849051] EXT3-fs error (device dm-1): htree_dirblock_to_tree: bad entry in directory #23248900: directory entry across blocks - offset=0, inode=526135583, rec_len=18256, name_len=83*

I tried *sudo find -inum 526135583* which I thought would tell me which file was bad.  It complained about a bunch of files with Stale NFS file handles.

Any thoughts?  After several reboots and repeat fsck -y there are about 100 files in the lost+found directory, but the syslog messages continue.

---

### Post by fjgaude on 2009-01-10
From what I can see you have a bad drive.

After bootup, what does this show:

sudo mdadm -D /dev/md[n]

if you are using software raid. If not, what does your raid utility say about the array?

---

### Post by linuxisevolution on 2009-01-10
> **jelevin said:**
> Ubuntu 8.10. Reboot failed, with suggestion to run fsck manually on a Raid-1 array. This ran with a ton of errors that presumably were fixed. After the next reboot the raid status was reported to be something like 98.5% for a bit. Now I see this message in syslog:

*Jan 8 18:17:08 computername kernel: [27946.849051] EXT3-fs error (device dm-1): htree_dirblock_to_tree: bad entry in directory #23248900: directory entry across blocks - offset=0, inode=526135583, rec_len=18256, name_len=83*

I tried *sudo find -inum 526135583* which I thought would tell me which file was bad.  It complained about a bunch of files with Stale NFS file handles.

Any thoughts?  After several reboots and repeat fsck -y there are about 100 files in the lost+found directory, but the syslog messages continue.

Run fcsk when the partition is not mounted, use a livecd.

---

### Post by jelevin on 2009-01-11
> **fjgaude said:**
> From what I can see you have a bad drive.

After bootup, what does this show:

sudo mdadm -D /dev/md[n]

if you are using software raid. If not, what does your raid utility say about the array?

```
$ sudo mdadm -D /dev/md1
/dev/md1:
        Version : 01.00
  Creation Time : Sat May 31 23:49:52 2008
     Raid Level : raid1
     Array Size : 175815288 (167.67 GiB 180.03 GB)
  Used Dev Size : 351630576 (335.34 GiB 360.07 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sun Jan 11 08:19:36 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : 1
           UUID : 2be6958b:b6cd12f7:02192719:c40cc1c3
         Events : 1800

    Number   Major   Minor   RaidDevice State
       0       8       18        0      active sync   /dev/sdb2
       2       8       50        1      active sync   /dev/sdd2

```

I have installed some SMART monitoring, and can't find evidence of a bad drive.  I have also run fsck multiple times on the array.  Each time it finds errors that I have it fix, but I still see errors in syslog.

---

### Post by fjgaude on 2009-01-11
The superblock data is good but likely the rest of one of the drives is falling apart... I don't have any suggestions other than get a new drive... hope you have full backup for important data.

---

### Post by jelevin on 2009-01-11
> **fjgaude said:**
> The superblock data is good but likely the rest of one of the drives is falling apart... I don't have any suggestions other than get a new drive... hope you have full backup for important data.

Thanks.  Is there any way to tell which of the two drives in the software raid 1 array is failing?

---

### Post by fjgaude on 2009-01-12
Gosh, I have not had this issue before... you could use mdadm to --fault a drive and then see if fsck still gives errors.

Ran across this super link covering much of what we go through with raid:

[http://linux-raid.osdl.org/index.php/Detecting%2C_querying_and_testing](http://linux-raid.osdl.org/index.php/Detecting%2C_querying_and_testing)

In case you haven't read, studied it.

Remember, if you take a drive out of an array it cannot be used again, ever: unless you fault it, then remove it using mdadm. Then you have to zero-superblock before you can then add a new filesystem to it.

I'm not sure if you want to test it as a drive while it is still in the array. You could try by stopping the array, umounting it first. All this could be done using a liveCD to boot.

Let us know how you are doing.

---

