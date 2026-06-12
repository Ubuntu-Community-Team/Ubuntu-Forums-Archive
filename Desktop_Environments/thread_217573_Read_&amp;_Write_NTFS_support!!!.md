---
title: "Read &amp; Write NTFS support!!!"
date: 2006-07-17
forum: Desktop Environments
---

### Post by DJ Ubuntu on 2006-07-17
INTRODUCTION
 ============
 
 The ntfs-3g driver is an open source, GPL licensed, third generation Linux 
 NTFS driver for 32-bit, little-endian architectures which was implemented 
 by the Linux-NTFS project. It provides full read-write access to NTFS, 
 excluding access to encrypted files, writing compressed files, changing 
 file ownership, access right.
 
 Technically it's based on and a major improvement to the third generation 
 Linux NTFS driver, ntfsmount. The improvements includes functionality, 
 quality and performance enhancements. 
 
 The driver currently is in BETA status: before release of this software we 
 haven't experienced any driver crashes or data loss during our heavy quality testing, however we are aware of some minor issues which will be resolved in the near future. We listed all of them in a below section. Please report any new problem to linux-ntfs-dev@li... if it's not listed yet in the latest release of this software. 

Requires FUSE:
[http://prdownloads.sourceforge.net/fuse/fuse-2.5.3.tar.gz?download](http://prdownloads.sourceforge.net/fuse/fuse-2.5.3.tar.gz?download)

**Install**
```
$ sudo ./configure --prefix=/usr
$ sudo make
$ sudo make install
```

**Download ntfs-3g**
[http://mlf.linux.rulez.org/mlf/ezaz/ntfs-3g-20070714-BETA.tgz](http://mlf.linux.rulez.org/mlf/ezaz/ntfs-3g-20070714-BETA.tgz)

**Install**
```
$ sudo ./configure --prefix=/usr
$ sudo make
$ sudo make install
```



```
$ sudo modprobe fuse
$ sudo ntfs-3g /dev/hda1 /media/windows
$ su
# cd /media/windows
```
Read & Write access WORKS!!.

Umount:
```
# fusermount -u /media/windows
```

Regards.

Font:
[http://developers.slashdot.org/article.pl?sid=06/07/15/1346250](http://developers.slashdot.org/article.pl?sid=06/07/15/1346250)


Regards.;)

---

### Post by mrbaz on 2006-07-17
I'll try this later on my laptop and report back with my findings.

---

### Post by givré on 2006-07-17
Hi guys, i made an easy HowTo (with package) for that here [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)
Check it ;)

---

### Post by taurus on 2006-07-17
You don't really need to use "sudo" for both .configure & make!

---

### Post by DJ Ubuntu on 2006-07-17
> **taurus said:**
> You don't really need to use "sudo" for both .configure & make!
Sorry....is a custom....:neutral:

---

