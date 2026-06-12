---
title: "NTFS Windows partition broken by dd | gzip backup and restore"
date: 2009-04-05
forum: General Help
---

### Post by scs217 on 2009-04-05
Hey guys,

I'm repairing a broken OS for a friend. My plan was to follow the idea shown on this website [http://www.scripts-net.com/viewtopic.php?t=73&f=6]("http://www.scripts-net.com/viewtopic.php?t=73&f=6").

What I did was install XP Pro, some software and service packs, then install ubuntu 8.10. My partitioning table is as follows:

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        4870    39062047+   7  HPFS/NTFS
/dev/sda3            4871        7296    19486845    5  Extended
/dev/sda5   *        4871        6086     9767488+  83  Linux
/dev/sda6            6087        7180     8787523+   b  W95 FAT32
/dev/sda7            7181        7296      931738+  82  Linux swap / Solaris

```

Where sda2 is windows, sda5 is linux, and sda6 is a restore partition holding the file xp.img.gz

The commands I ran (as root) were:

```
umount /dev/sda2

dd if=/dev/sda2 conv=sync,noerror bs=64K | gzip -c > /restore/xp.img.gz

gunzip -dc /restore/xp.img.gz | dd of=/dev/sda2 conv=sync,noerror bs=64K
```

Upon writing the image back to sda2, I can no longer mount the partition, and windows complains of a disk read error. I also saw after unzipping that /sda2 was flagged bootable where it hadn't been before so I changed it back.

Here's what I get from trying to mount the partition:
```
prodigy@prodigy-laptop:~$ sudo mount /dev/sda2 /windows
mount: you must specify the filesystem type
prodigy@prodigy-laptop:~$ sudo mount /dev/sda2 -t ntfs /windows
$MFT has invalid magic.
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

```

Please help me figure out what went wrong with this procedure. Hopefully I can recover all the work that I put into the windows OS!

---

### Post by scs217 on 2009-04-05
bump

---

