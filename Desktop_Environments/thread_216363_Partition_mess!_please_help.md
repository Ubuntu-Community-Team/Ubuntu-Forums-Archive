---
title: "Partition mess! please help"
date: 2006-07-15
forum: Desktop Environments
---

### Post by routerstu on 2006-07-15
i am dual booting xp pro and dapper as you can see by the screenshot.   i made my windows partition smaller thus freeing up 10g, my question is how do i add this to the ubuntu partition so i can grow it?  is it impossible since they are not in order?  any ideas?

thanks

---

### Post by utnubu001 on 2006-07-15
i dont think u can resize ext3 file systems
make a completely new partition instead
make it ntfs or fat32 to be able to also view it on windoze
or make it ext3 so only linux can use it

---

### Post by routerstu on 2006-07-15
thanks!   hmmm, i may be in for a new install................

---

### Post by mmcmonster on 2006-07-15
If you are doing a new installation, here is a little advice:

Make /home a separate partition, containing most of the free space.  10GB for the root partition is more than enough.  Both of these partitions should be ext3.  If you need to access the data from windows, install [ext2 Installable Filesystem]("http://www.fs-driver.org/") under windows.  It will let you access both ext2 and ext3 filesystems under windows.

The benefit of making /home a separate partition is that if you do a new installation at a later date, all your data is still safe.

---

### Post by utnubu001 on 2006-07-15
well that sucks
didnt know that u could anyhow acces linux from windoze....

---

### Post by mmcmonster on 2006-07-17
Yeah. I have used [ext2ifs]("http://www.fs-driver.org/") for the better part of a year.  With it you can both read and write data in ext2 and ext3 partitions from within windows.

The only caveat is that you have to be careful not to crash windows while it's writing to the ext2/3 partition, since it has reportedly caused trashing of the filesystem.

---

### Post by mdelorme on 2006-07-17
Another thing to keep in mind if you plan on creating, dropping, and resizing partitions is using the alternate install disk (or the DVD) and using LVM.  This will let you create, drop, and resize your logical volumes (which get mounted the same way partitions do) without worrying about how your partitions are laid out physically on your drive.

---

