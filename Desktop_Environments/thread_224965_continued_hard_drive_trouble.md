---
title: "continued hard drive trouble"
date: 2006-07-28
forum: Desktop Environments
---

### Post by poingjam on 2006-07-28
Starting a new thread because the problem stated earlier seems different.

So I've installed Ubuntu, but I can't access my other hard drive which has Windows XP installed on it and is formatted as NTFS.  The drive is in fact mounted, but it says I don't have the permissions to view its contents.  I've tried dismounting it, but it says it's not below the media directory, so I tried changing the access point to below the media directory but it didn't actually change, it just stayed where it was, in tmp.  So what do I do now?  I've been to the NTFSmount page and the MountingWindowsPartitions page, and the InstallingANewHardDrive page and everything else I could think of and that was given to me, and it's not helping.

EDIT: Oh, and I went to the disk's properties, and under permissions, read is checked for all user types.

---

### Post by taurus on 2006-07-28
You need to set the permission for your NTFS in /etc/fstab.  It should look something like

```

/dev/hda1   /media/windows   ntfs   defaults,umask=0222   0   0

```
Make sure you have the "umask=0222" in there if you want a user to view the content of your NTFS...

---

### Post by poingjam on 2006-07-29
I tried that and rebooted.  It ended up being possible to unmount the drive (sort of), but I still couldn't change the location of the access point, and most importantly, I still couldn't access the content.

For some reason, fstab didn't have a line for the drive at all, I had to add it myself.  Then when I added it, it made a false partition in the system/administration/disks thing, which was 0 bytes in size.  So I deleted the line from fstab.

---

### Post by scxtt on 2006-07-29
what's your output for:
[indent]sudo fdisk -l[/indent]

---

### Post by poingjam on 2006-07-29
Here it is:

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30017   241111521   83  Linux
/dev/sda2           30018       30394     3028252+   5  Extended
/dev/sda5           30018       30394     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdc: 1023 MB, 1023933952 bytes
255 heads, 63 sectors/track, 124 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          10       80293+   0  Empty
/dev/sdc2              11         124      915705    b  W95 FAT32


It's the 160 gig drive, the sdb.

---

### Post by poingjam on 2006-07-29
Oh, and now that I've unmounted the drive, I can mount it again.

---

### Post by bullgr on 2006-07-29
mount the disk as it was (better do this from the command line) and after that change the permission (that i believe makes the trouble)
> sudo chmod -R 777 /mnt/d
where /mnt/d put your mount-point of your disk

hope i help...

---

### Post by poingjam on 2006-07-29
Never mind, I'm giving up.  This thing crashes more than anything I've used since Windows ME.  And I tried that, the drive won't mount again.

---

### Post by bullgr on 2006-07-29
don't give up...
i had too, to handle with many problems in many distros i try.
but when you finaly done and work without any problem, when it's like a dream...
and the best distro for this is ubuntu, believe me...

---

