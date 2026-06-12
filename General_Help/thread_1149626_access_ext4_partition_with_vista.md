---
title: "access ext4 partition with vista??"
date: 2009-05-05
forum: General Help
---

### Post by tdietz87 on 2009-05-05
I have recently installed ubuntu and since I am still new I use both Ubuntu and Vista currently depending on what I'm trying to accomplish.  I've seen videos of people who boot up vista open up "my computer" and next to the C:/ you can see and access your other partitions.  However I cannot see anything besides the C drive.
 
Any ideas how to access my ubuntu partition (ext4) from vista so I can open files that I keep on that partition?
 
troy

---

### Post by michy99 on 2009-05-05
You need a special driver in Windows to access linux filesystems. This article explains how to do it:

[http://www.linuxjournal.com/article/9449](http://www.linuxjournal.com/article/9449)

---

### Post by the8thstar on 2009-05-05
That article is quite dated. I'm afraid there is no solution yet if your system is formatted with EXT4.

---

### Post by tdietz87 on 2009-05-05
> **the8thstar said:**
> That article is quite dated. I'm afraid there is no solution yet if your system is formatted with EXT4.

Thank you for response

---

### Post by opticyclic on 2009-09-03
A bit of an old thread, I know, but Virtual Volumes has a development driver that can access ext4 partitions.
You need to contact the developer to get it though as it is not released yet.
[http://www.chrysocome.net/virtualvolumes](http://www.chrysocome.net/virtualvolumes)

---

### Post by bodhi.zazen on 2009-09-03
You can mount ext4 file systems with fs-driver

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Starks on 2009-09-06
Only if you don't have extents enabled. If you have extents enabled like 99% of ext4 users, then you're screwed.

I have spoken to the devs and they are working hard on a solution to allow ext4 mounting.

---

### Post by copracr on 2010-02-01
> **Starks said:**
> Only if you don't have extents enabled. If you have extents enabled like 99% of ext4 users, then you're screwed.

Whats an extent?  Can it be disabled to allow reading?  I run vista on a jump drive and it would be handy to be able to copy from a work (XP) or home(vista gaming rig) computer.

---

### Post by M1GEO on 2010-02-01
[http://www.diskinternals.com/linux-reader/]("http://www.diskinternals.com/linux-reader/")

Their website claims it only supports ext2/ext3.  However, [thread 1145598]("http://ubuntuforums.org/showpost.php?p=7219555&postcount=5") claims it works.

---

### Post by samantha_ on 2010-02-01
> **copracr said:**
> Whats an extent?  Can it be disabled to allow reading?  I run vista on a jump drive and it would be handy to be able to copy from a work (XP) or home(vista gaming rig) computer.

you would need to have mounted ext4 with
```
-o noextents
```
that would maintain backwards compatability with ext3 and would allow you to revert to it any time you want.
but, as the above poster noted, ext4 is by default, created without the tag.
Oh, and you cant disable it once its enabled.

---

### Post by flipper9 on 2010-04-24
You could try this userspace program which says it can read EXT4...
 
[http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)

---

### Post by catalin.hritcu on 2010-06-20
> **flipper9 said:**
> You could try this userspace program which says it can read EXT4...
 
[http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)

ext2read (AKA ext2explore) has indeed [support for ext4 partitions]("http://ext2read.blogspot.com/2010/04/ext2read-22-released-now-with-lvm2-and.html"). It's not perfect, but it seems to do the job if all you care is copying files from Windows (you can't mount Linux partitions with this).

---

### Post by opticyclic on 2010-06-20
You have to make sure you run these programs as an administrator though.
It can be quite confusing to see the program start but not see the ext4 partition.

---

### Post by haringwati on 2011-02-21
> **flipper9 said:**
> You could try this userspace program which says it can read EXT4...
 
[http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)

Or you can also try Ext2Fsd.  The latest release (version 0.50) claims to have readonly support for ext4 partitions created with the extents flag on.

Hop over to [http://www.ext2fsd.com/](http://www.ext2fsd.com/)

---

