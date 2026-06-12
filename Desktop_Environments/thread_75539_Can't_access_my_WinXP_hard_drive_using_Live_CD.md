---
title: "Can't access my WinXP hard drive using Live CD"
date: 2005-10-13
forum: Desktop Environments
---

### Post by digitalstruggle on 2005-10-13
Hi there, folks.  When running the 5.10 Live CD I wasn't able to access my Windows XP (NTFS) hard drive.  It didn't come up anywhere.  I pulled up a disk utility thing and it saw that my hard drive existed, but it wasn't able to do anything to it.  I couldn't mount it or anything, either through this utility or from the command line.

Has anyone seen this problem?

You know, I saw the 5.10 Live CD DVD iso up on the 12th.  It's definitely 5.10.  The release was announced a day later.  Are there two versions of the 5.10 iso?

I'm sorry that I haven't given any more specifics.  I haven't touched Linux in a long time.  I'd really like to use this DVD as a recovery tool.  Please help me find out what's going on.

---

### Post by dbott67 on 2005-10-13
What command did you use to mount?

According the the [Unofficial Ubuntu Guide]("http://www.ubuntuguide.org/"), you need to type:
```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

Please note that this example assumes that your XP NTFS partition is hda1.  Your mileage may vary.  Run fdisk to see your partition info.
```
sudo fdisk -l /dev/hda

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2442    19615333+  83  Linux
/dev/hda2            2443        2550      867510    5  Extended
/dev/hda3   *        2551        4997    19655527+   7  HPFS/NTFS
/dev/hda5            2443        2550      867478+  82  Linux swap / Solaris
```

-Dave

---

### Post by digitalstruggle on 2005-10-13
I'll give that a shot next time I boot the Live CD.  So is the ability to access local hard drives not enabled by default or is it just my machine?

I was hoping for a more Mepis-like experience.

---

### Post by dcarpenter on 2005-10-13
no, ubuntu requires you to mount any drive that is of the FAT32 or NTFS filesystem.  If you do a clean install, you can edit your fstab to make the NTFS partition load up on boot up.

[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

this guide assumes the drive you wish to mount is hda1, like dbott67 said.

---

### Post by aysiu on 2005-10-13
[QUOTE=digitalstruggle]I'd really like to use this DVD as a recovery tool.  Please help me find out what's going on.[/QUOTE] You can use Ubuntu as a recovery tool if you manually mount partitions, but Knoppix is more built to be a recovery tool.

---

