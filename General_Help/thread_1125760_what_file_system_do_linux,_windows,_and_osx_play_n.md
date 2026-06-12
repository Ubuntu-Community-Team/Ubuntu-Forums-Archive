---
title: "what file system do linux, windows, and osx play nice with?"
date: 2009-04-14
forum: General Help
---

### Post by smellyoulater on 2009-04-14
Hi,

Ok. so i need some help.

I have a netbook that is triple booting ubuntu, XP and OSX.
Now I don't care if any of those partitions can see each other.

What I do care about is my new external harddrive.  I want to keep all my music and other user files on the external.  What file system is best so that all three os's can read/write to the external HD. I want to be stable, and I don't want fat32.  I want to keep the external as one big glorious 500gig partition.

Is there the equivalent of [http://www.fs-driver.org/](http://www.fs-driver.org/) for osx?

This what i've understand from going through the forums. 

 

NTFS
ubuntu ok/windows ok (stable) /OSX (getting there)

HFS
osx ok/  ubuntu? /windows?

EXT2
OSX ?  / ubuntu OK / Windows OK  

Ext3
?????

Fat32
I'm really trying to avoid this


 I'm leaning towards ext2. If you've got advice, let's hear it.

---

### Post by shaggy999 on 2009-04-14
ext3 is just ext2 + journaling, so any ext2 driver should be able to easily read and write to an ext2 file system. Honestly, your best bet is fat32, but if you don't want to do that then ext2/3 is probably your next best bet. I believe there is an osx driver for ext2/3 on sourceforge.

---

### Post by 3Miro on 2009-04-14
NTFS is well supported by both Linux and Windows and Fat32 should be avoided (it actually gives problems on newer systems).

I am surprised Mac doesn't read NTFS well, didn't they sell dual booth Win-Mac machines at one point?

---

### Post by mb_webguy on 2009-04-14
FAT32 is the most widely recognized file system, and is therefore commonly used when cross-system compatibility is a priority.

There is a Mac OS X version of [ntfs-3g]("http://macntfs-3g.blogspot.com/") that will allow Mac OS X to use ntfs just as Linux does.  

The [ext2fsx]("http://sourceforge.net/projects/ext2fsx/") driver will allow Mac OS X to mount ext2/ext3 partitions.  Likewise, the [ext2ifs]("http://www.fs-driver.org/") driver will allow Windows to mount ext2/ext3 partitions.

One note about both ntfs and ext3...  Even with those drivers, each OS will be unable to take advantage of journaling with the non-native filesystem.  So Windows (and Mac OS X?) will mount ext3 as ext2, without journaling.  Linux and Mac OS X will mount ntfs as ntfs, but do not support ntfs journaling.

---

### Post by smellyoulater on 2009-04-14
> **mb_webguy said:**
> FAT32 is the most widely recognized file system, and is therefore commonly used when cross-system compatibility is a priority.

There is a Mac OS X version of [ntfs-3g]("http://macntfs-3g.blogspot.com/") that will allow Mac OS X to use ntfs just as Linux does.  

The [ext2fsx]("http://sourceforge.net/projects/ext2fsx/") driver will allow Mac OS X to mount ext2/ext3 partitions.  Likewise, the [ext2ifs]("http://www.fs-driver.org/") driver will allow Windows to mount ext2/ext3 partitions.

One note about both ntfs and ext3...  Even with those drivers, each OS will be unable to take advantage of journaling with the non-native filesystem.  So Windows (and Mac OS X?) will mount ext3 as ext2, without journaling.  Linux and Mac OS X will mount ntfs as ntfs, but do not support ntfs journaling.


That osx implementation of ext2/3 looks a little old.  Any idea how stable it is, or if there is anything out there that has had more recent updates?

Has anyone tried the this ntfs-3g for osx?

---

