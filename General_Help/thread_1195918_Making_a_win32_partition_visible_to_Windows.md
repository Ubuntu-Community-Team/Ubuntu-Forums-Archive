---
title: "Making a win32 partition visible to Windows?"
date: 2009-06-24
forum: General Help
---

### Post by Rippy on 2009-06-24
I've organized my drive roughly like this:

Ubuntu - 15GB
Windows Vista - 50GB
swap - 4GB
data - remainded of the drive (about 270GB)

So I set all this up in gparted, because initially the first 15GB partition was a backup partition and the remainder of the drive was the Windows partition. But when I boot into Vista now, the only drive it sees is Local Disk D:, which it seems as having 0 size. I know it shouldn't see the ext4 or swap partitions, but why won't it see the win32 one? Do I have to do something special for it to work? From windows my only option is to format the whole drive, but I'm afraid that would format my Ubuntu and swap partitions as well... I suppose if it comes down to it, I can format it in Windows, then re-install Ubuntu and resize the now-detected win32 partition in the process... that'd be a lot of work though.

Any help is appreciated,

-Rippy

(By the way, I'm using 9.10 Alpha 2. I know it has its own forum, but I'm posting here because I don't think the Ubuntu version is relevant for this. I hope that's okay.)

---

### Post by michy99 on 2009-06-24
What is the output of this command?```
sudo fdisk -l
```

---

### Post by Rippy on 2009-06-24
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x788f6226

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1827    14675346    5  Extended
/dev/sda2   *        1828        7907    48828125    7  HPFS/NTFS
/dev/sda3            7908        8405     4000185   82  Linux swap / Solaris
/dev/sda4            8406       38913   245055510    b  W95 FAT32
/dev/sda5               1        1827    14675314+  83  Linux

---

### Post by Legace on 2009-06-24
Open Disk Manager (or whatever its called in Windows) and see if you can see the partition there.
Then, try to mount it

[http://www.windowsreference.com/windows-vista/how-to-use-disk-management-in-vista/](http://www.windowsreference.com/windows-vista/how-to-use-disk-management-in-vista/)

---

### Post by Rippy on 2009-06-24
That did it! Man, Vista's disk settings are well-hidden...

I formatted it as NTFS inside Vista and the partition is recognized. Weird, though, because I formatted it as FAT32 in gparted, but Windows saw it as "RAW". I'd still like it as FAT32, but ubuntu's pretty good about accessing NTFS filesystems now so I suppose it's no big deal. Thanks! (especially since I see now that this wasn't really an Ubuntu question/problem at all...)

---

