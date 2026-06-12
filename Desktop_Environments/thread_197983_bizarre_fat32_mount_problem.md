---
title: "bizarre fat32 mount problem"
date: 2006-06-16
forum: Desktop Environments
---

### Post by MattCarp on 2006-06-16
Ok - this is strange.  My partition isn't being handled properly.  But, if I umount it, I can still access it and then it works!

Here's my fstab:

```

/dev/hdc1       /home/data  vfat iocharset=utf8,umask=000 0 0
/dev/hda1       /home/windows  vfat iocharset=utf8,umask=000 0 0

```

hdc1 is a fat32 drive.

Here's the output of ls:

```

matt@earth:/$ ls -alh /home/data
total 68K
drwxrwxrwx 5 root root  16K 1969-12-31 19:00 .
drwxr-xr-x 6 root root 4.0K 2006-06-16 11:41 ..
drwxrwxrwx 8 root root  16K 2006-05-14 09:11 App Archive
drwxrwxrwx 2 root root  16K 2006-06-14 20:39 Recycled
drwxrwxrwx 3 root root  16K 2006-06-14 12:14 System Volume Information
matt@earth:/$

```

There are directories missing from this listing.  So, if I umount it and then do an ls,  here's what I get:

```

root@earth:/# umount /dev/hdc1
root@earth:/# ls -al /home/data
total 20
drwxr-xr-x  5 matt root 4096 2006-05-14 09:36 .
drwxr-xr-x  6 root root 4096 2006-06-16 11:41 ..
drwx------ 16 matt root 4096 2006-06-05 10:38 App Archive
drwx------ 31 matt root 4096 2006-06-01 23:04 Data
drwx------  9 matt root 4096 2006-05-14 09:37 Kathy
root@earth:/#

```

This is what I would expect.  In fact, I'm able to navigate the disk and properly interact with the file system.

hda1 works fine.

What gives?

Note- I used to have this in my fstab:

/dev/hdc1       /home/data  vfat rw,user,noauto 0 0

This worked, but I only later learned that this didn't automatically mount my file system ("noauto") at boot time.  This was weird, because again, I could interfact with the filesystem without a problem.

So, should I use the following in my fstab?

/dev/hda1        /home/windows  vfat rw 0 0
/dev/hdc1        /home/data        vfat rw 0 0


For completeness, here's fdisk:

```

root@earth:/etc# fdisk -l

Disk /dev/hda: 27.3 GB, 27325218816 bytes
255 heads, 63 sectors/track, 3322 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3321    26675901    c  W95 FAT32 (LBA)

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14593   117218241    b  W95 FAT32

```

-Matt

---

