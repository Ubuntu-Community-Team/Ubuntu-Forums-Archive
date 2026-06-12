---
title: "Common filesystem for windows/linux?"
date: 2005-06-05
forum: Desktop Environments
---

### Post by sideh on 2005-06-05
Afternoon'

I've just installed windows xp and ubuntu on a new hd and I'm trying to find a way to create a partition that I can use with both operating systems. 

I can't use NTFS as writing from linux isn't recommended. FAT32 is limited in size. I did try a ~30gb fat32 partition but it gets lot of "operation not permitted errors". Especially from Azureus. And for some reason amaroK claims mp3's aren't writeable despite having full access.

Essentially, I need a filesystem that I can read/write from both windows and linux. It'll be around 160gb or so. 

Anyone know if this is possible?


cheers,
rich

---

### Post by mtron on 2005-06-05
vfat (Fat32) filesystems work very good on both, linux & win. the limitation is that files must not be larger then 4 GB. 

theoretical maximum size is 8 TB (Terra Byte) for a vfat fs. Windows does not allow to create larger Fat32 partitions then 32 GB i think, but with linux it should be no prob. 

did you use gparted to create the partition, and formatting went ok? 

about fat:
FAT - Linux calls these "msdos, umsdos, vfat" There are three variants: MSDOS, UMSDOS, and VFAT. Their core is based on the FAT filesystem. MSDOS is a traditional DOS file system with 14 character filename contraint, and is the most simple variant of FAT filesystem. UMSDOS, which was not widely used and likely won't be, is a method of storing long filenames without making any change to the FAT structure itself. It's running on FAT also. VFAT is the latest filesystem used by Windows 95/98 to store long filenames. Linux supports FAT32(next FAT) implicitly. This filesystem does not have automatic defragmentation and wastes some space in management, but has high-recovery ratio.

---

### Post by sideh on 2005-06-05
Ah, many thanks. 

I originally created the partition in windows xp and you'r right, 32gb was the max size it would let me create. 

Just created a 160gb vfat partition in linux and its working beautifully. 

cheers m8

---

### Post by crash369 on 2005-06-05
that's weird.  i created my 2x50G fat paritions in winxp no problem...

---

### Post by mtron on 2005-06-06
Perhaps MS did not include  this limitation in WInxp. my last Windows OS was Win98, and there was the limitation 32 GB. anyway, my harddisk was only 40 GB, what was huge in these times... and now? 

Well, my P3 is still serving as firewall and dhcp server.

---

