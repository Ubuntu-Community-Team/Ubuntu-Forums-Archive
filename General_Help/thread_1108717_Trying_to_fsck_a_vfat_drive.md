---
title: "Trying to fsck a vfat drive"
date: 2009-03-28
forum: General Help
---

### Post by mjpatey on 2009-03-28
Hi, all-

I just tried using fsck.vfat on my 500GB external USB 2.0 drive, and here's what happened:

```
$ sudo fsck.vfat /dev/disk/by-id/usb-WDC_WD50_00AAJB-00UHA0_0-0:0

dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 251.

```

I guess I'm too FAT.  Any idea how to resolve this and do a filesystem check?

Thanks in advance!

-Mark

---

### Post by dcstar on 2009-03-28
> **mjpatey said:**
> Hi, all-

I just tried using fsck.vfat on my 500GB external USB 2.0 drive, and here's what happened:

```
$ sudo fsck.vfat /dev/disk/by-id/usb-WDC_WD50_00AAJB-00UHA0_0-0:0

dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 251.

```

I guess I'm too FAT.  Any idea how to resolve this and do a filesystem check?

Thanks in advance!

-Mark

Do not "force" a particular type of check, just use "fsck" and allow that to choose the correct one.

---

### Post by mjpatey on 2009-03-28
Thanks, David.  I'm not home right now to try that again, but that's what I started out doing.  I only remember it yielded a dead-end; wish I could remember what kind!

I'll try it when I get home and post what happens.  Thank you for the input!

-Mark

---

### Post by mjpatey on 2009-03-29
OK, here's what happens when I try "sudo fsck.vfat":

```
mjpatey@Buddy:/dev/disk/by-id$ sudo fsck.vfat /dev/disk/by-id/usb-WDC_WD50_00AAJB-00UHA0_0-0:0
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 251.

```...and here's what happens when I just do "sudo fsck":

```
mjpatey@Buddy:/dev/disk/by-id$ sudo fsck /dev/disk/by-id/usb-WDC_WD50_00AAJB-00UHA0_0-0:0
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/disk/by-id/usb-WDC_WD50_00AAJB-00UHA0_0-0:0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```...so it seems plain old fsck doesn't really apply (unless this message is a sign that things are wrong?)

Does any of this make sense to anybody?  Any idea what I can do to check the integrity of this external USB vfat hard drive?

Thanks for any insight you can provide!

-Mark

---

### Post by dcstar on 2009-03-29
> **mjpatey said:**
> 
........
Does any of this make sense to anybody?  Any idea what I can do to check the integrity of this external USB vfat hard drive?

Thanks for any insight you can provide!


Firstly, you must unmount any drive you try to fsck, and are you **100% sure** it is a FAT32 drive:

```
sudo fdisk -l
```

---

### Post by mjpatey on 2009-03-29
Yes, I'm sure it's a FAT32 drive.  Here's the output of fdisk -l:

```
mjpatey@Buddy:/dev/disk/by-id$ sudo fdisk -l
[sudo] password for mjpatey: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b5439

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18237   146488671   83  Linux
/dev/sda2           18238       43524   203117827+   5  Extended
/dev/sda5           42552       43524     7815622+  82  Linux swap / Solaris
/dev/sda6           18238       42551   195302142   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000618f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    b  W95 FAT32

Disk /dev/sdc: 2031 MB, 2031091712 bytes
16 heads, 32 sectors/track, 7748 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          16        7748     1979456    e  W95 FAT16 (LBA)

```... and here's me fsck'ing it as sdc1, rather than "by ID" as earlier:

```
mjpatey@Buddy:/dev/disk/by-id$ sudo fsck.vfat /dev/sdc1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sdc1: 41 files, 1424/61849 clusters
mjpatey@Buddy:/dev/disk/by-id$ 
```...somehow that returned some info this time!  But it's still not running through a filesystem check...

EDIT:  Oops!  It's sdb1, not sdc1!  So I'm running that now...

...it asks:

```
 mjpatey@Buddy:/dev/disk/by-id$ sudo fsck.vfat /dev/sdb1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
?
```

And now I have to leave for work.  This is getting close to being resolved, though!  Thanks for the help, and if you have any further insight, thanks in advance!

-Mark

---

### Post by Hanine on 2009-10-27
[SIZE=1]> **mjpatey said:**
> Hi, all-

I just tried using fsck.vfat on my 500GB external USB 2.0 drive, and here's what happened:

```
$ sudo fsck.vfat /dev/disk/by-id/usb-WDC_WD50_00AAJB-00UHA0_0-0:0

dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 251.

```I guess I'm too FAT.  Any idea how to resolve this and do a filesystem check?

Thanks in advance!

-Mark[/SIZE]     

[SIZE=5]```
dosfsck -a -w -v /dev/sdb1
```[/SIZE]

---

### Post by mjpatey on 2009-10-27
Thanks, everyone... this was a pretty old thread and my particular problem has been "solved" already.  I gave up and have installed the Karmic Beta, and the new install is treating the external drive just fine.

Hopefully the suggestions given here will benefit others!

---

