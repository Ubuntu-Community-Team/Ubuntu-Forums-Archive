---
title: "Large file problem ( &gt; 4GB )"
date: 2005-10-16
forum: Desktop Environments
---

### Post by stimpack on 2005-10-16
I cannot seem to create files larger than 4GB. When I recently "backed up" my WoW, Everquest and GTA San Andreas directories with 'tar' they all got capped at 4gb which i didnt notice untill I "needed them" :( 

Also using qemu I am unable to create a diskfile that is larger than 4GB, is there some kind of hardcap on filesizes, and if so how can it be increased? I am using ReiserFS, thanks.

---

### Post by rpimn on 2005-11-11
Hi stimpack,

The problem may be caused by ReiserFS.
You can have a look at [http://www.suse.de/~aj/linux_lfs.html](http://www.suse.de/~aj/linux_lfs.html)
about file size limit and filesystem size limit

---

### Post by mlomker on 2005-11-11
I always use partimage for backups and have never had a problem.  I found [this article]("http://answers.google.com/answers/threadview?id=25116").  I have a VMWare file that is 8 Gig and I also run Reiser.

---

### Post by vince32 on 2005-11-26
The best backup program is Acronis. I only use Reiserfs. I have Ubuntu and Gentoo with WinXP in Grub. Never have any problems with backups or reliability of the backups. Try it!

Vince32:p

---

### Post by miatawnt2b on 2008-01-20
> **stimpack said:**
> I cannot seem to create files larger than 4GB. When I recently "backed up" my WoW, Everquest and GTA San Andreas directories with 'tar' they all got capped at 4gb which i didnt notice untill I "needed them" :( 

Also using qemu I am unable to create a diskfile that is larger than 4GB, is there some kind of hardcap on filesizes, and if so how can it be increased? I am using ReiserFS, thanks.

I too have this problem trying to transfer a bunch of DVD ISO's between two USB drives.  Any idea what's going on?

Thanks,
-J

---

### Post by Steveway on 2008-01-20
> **miatawnt2b said:**
> I too have this problem trying to transfer a bunch of DVD ISO's between two USB drives.  Any idea what's going on?

Thanks,
-J

What filesystems do the drives have?
Most come with Fat and Fat doesn't support files bigger than 4GB -1byte.
You have to change the filesystem to something different like ext3. (Well better ext2 for a USB-drive.

---

