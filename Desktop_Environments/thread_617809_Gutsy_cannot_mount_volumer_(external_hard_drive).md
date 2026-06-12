---
title: "Gutsy cannot mount volumer (external hard drive)"
date: 2007-11-19
forum: Desktop Environments
---

### Post by barrack on 2007-11-19
Alrighty, I upgraded from Feisty to Gutsy. I also have an external hardrive (FAT32).

In Festy, there was no problem. I was able to plug it in and back up my files no problem.

In Gutsy, when I plug it in I get this message:

> Cannot mount volume.
Unable to mount the volume "BARRACK'.

Details
mount:wrong fs type, bad option, bad superblock on /dev/sdb1,      missing codepage or helper program, or other error        In some cases useful info is found in syslog - try        dmesg | tail or so

Any thoughts on what this means? Why would this have easily worked in feisty and not gutsy?

---

### Post by taurus on 2007-11-19
See if you can mount it by hand from a terminal.  What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by barrack on 2007-11-19
> **taurus said:**
> See if you can mount it by hand from a terminal.  What's the output of this command from a terminal?

```
sudo fdisk -l
```

I got this: 

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a0e2a0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc6c95314

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    b  W95 FAT32
```

I do'nt know what to make of it. But my external is 250GB.

---

### Post by taurus on 2007-11-19
Try

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
ls -la /media/sdb1
```

---

### Post by barrack on 2007-11-19
Okay I did all that and this is what I got. All the items are in green, which I think is a good thing.

```
total 46756
drwxrwxrwx 21 root root    32768 1969-12-31 16:00 .
drwxr-xr-x  4 root root     4096 2007-11-19 17:06 ..
drwxrwxrwx 18 root root    32768 2006-08-25 14:15 academic
drwxrwxrwx  3 root root    32768 2006-08-25 14:15 ato
-rwxrwxrwx  1 root root  1703936 2007-11-12 15:15 Desktop DB
-rwxrwxrwx  1 root root    45778 2007-11-12 15:15 Desktop DF
drwxrwxrwx  2 root root    32768 2007-11-12 15:24 Desktop Folder
-rwxrwxrwx  1 root root    15364 2006-12-25 01:33 .DS_Store
drwxrwxrwx  4 root root    32768 2007-01-23 22:00 evsc
-rwxrwxrwx  1 root root     2944 2007-11-12 16:06 finder.dat
drwxrwxrwx  2 root root    32768 2006-08-25 14:15 guitar
-rwxrwxrwx  1 root root  8887767 2005-11-27 10:59 Guitar Pro 5.0 full - no RMS.exe

```

But now I cannot unmount.
```

Cannot unmount volume

The volume 'BARRACK' was probably mounted manually on the command line.

Details
Device to unmount is not in /media/.hal-mtab so it is not mounted by HAL
```

Thoughts?

---

### Post by taurus on 2007-11-19
```
sudo umount /dev/sdb1
```

---

### Post by Ken Jannot on 2007-11-19
Will all this be necessary every time another drive needs mounting? I'm having the same problem, with two separate drives that worked just fine in Feisty. Looks like may others are, too, judging from what I found when searching the forums for this topic. It certainly seems to be a bug.

---

### Post by barrack on 2007-11-20
Yeah, Feisty worked much better with all the "it just works" type stuff. I'm hoping that the Heron addresses all of this.

---

### Post by barrack on 2007-11-22
I reformatted my external harddrive to ext3 and the plug-in recognition works just fine. It's still a pain to deal wth fat32 though, which i think is weak. I think I might downgrade back to 7.04.

---

