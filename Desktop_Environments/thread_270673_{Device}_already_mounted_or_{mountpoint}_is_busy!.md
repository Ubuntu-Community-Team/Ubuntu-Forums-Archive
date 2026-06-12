---
title: "{Device} already mounted or {mountpoint} is busy!"
date: 2006-10-03
forum: Desktop Environments
---

### Post by warbread on 2006-10-03
Ok, so I'm installing a FAT32 drive post-install, but Ubuntu's not letting me mount it with proper permissions.  If I go through Disk Manager, I can browse and format the disk just fine, but I can't write to it.  

I tried editing my fstab, and here's what I put down for my disk:

/dev/hdd	/mnt/music	vfat	iocharset=utf8,umask=000  0    0

It's the correct drive, and I did a $sudo mkdir for the /mnt/music folder, just in case anyone's wondering.  I do a mount -a and this is what I get:


mount: /dev/hdd already mounted or /mnt/music busy

$sudo umount /dev/hdd and $sudo umount /mnt/music does nothing.

[This link seems like it would be helpful, ]("http://www.ubuntuforums.org/showthread.php?t=264624&highlight=already+mounted") but I don't understand what the solution was.   

I appreciate any help.

---

### Post by GreenMarine on 2006-10-03
Warbread, they are recommending you get this patch to fix the problem: [http://evms.sourceforge.net/install/kernel.html#bdclaim](http://evms.sourceforge.net/install/kernel.html#bdclaim)

I haven't tried the patch, so I know nothing beyond that.

---

