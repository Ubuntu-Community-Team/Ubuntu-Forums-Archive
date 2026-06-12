---
title: "Making a new partition"
date: 2005-12-31
forum: General Help
---

### Post by Mazin on 2005-12-31
I have a 160 GB hard drive, arranged as

159.5 GB (active) for Linux (ext3)
0.5 GB swap
using up all the space.

I want to shrink the main partition to create a couple gigs for a FAT partition so I can share stuff with Windows on another hard drive.  How do I do that (hopefully keeping my data)?  I tried QTParted, but couldn't figure out how.

---

### Post by zoiks on 2005-12-31
You might need to use a live CD to do this since it likely doesn't want to resize a mounted partition.  I know qtparted (and gparted, I think) is in knoppix, it may also be in ubuntu live.

---

### Post by Omnios on 2005-12-31
I partitioned my 120gig win drive a long time ago and this is what I did.

 [http://ubuntuforums.org/showthread.php?t=45605]("http://ubuntuforums.org/showthread.php?t=45605")

 ALso you can use partition magic but its like $60 so I did it the linux way.

---

### Post by az on 2005-12-31
[QUOTE=Mazin]I have a 160 GB hard drive, arranged as

159.5 GB (active) for Linux (ext3)
0.5 GB swap
using up all the space.

I want to shrink the main partition to create a couple gigs for a FAT partition so I can share stuff with Windows on another hard drive.  How do I do that (hopefully keeping my data)?  I tried QTParted, but couldn't figure out how.[/QUOTE]
Yep.  You cannot partition a drive with a mounted partition on it.  You need to run a live cd like the installer (using parted from a virtual console in text mode) or using the ubuntu live cd (You need to unmount your swap, as that gets mounted automatically)

---

### Post by Mazin on 2005-12-31
I tried using QtParted from both a Knoppix Live CD and Ubuntu, but I either don't know how or it won't do it.

It lists the two partitions, but all I can do is adjust the swap partition.  The options are mostly grayed out for my main Linux partition.  All I can do is format it (I don't want to lose it).  I think it may have something to do with it set as Active. Does anyone know why it's doing this?

---

### Post by Omnios on 2005-12-31
If I remember properly Qt requires one or two plugins from synaptic to read and write (resize ntfs) and one for fat32 which is supposidly not to reliable. You definatly need the ntfs plug in. I did mine from within Linux as my Linux is on its own drive. Im not shure but I don't think you can do it if the disk is mounted though not shure on that one.

---

### Post by Mazin on 2005-12-31
I don't think I would need the ntfs plugin because I'm not messing with my windows disk.  I just need to shrink my ext3 partition and make a new partition with the resulting space.

---

### Post by Omnios on 2005-12-31
du whaps self lol. I ran into a similar problem when I first tryed as you can not create a partition in a partition so it has to be actualy resising it which leaves free space that can then be partitioned.

---

### Post by Mazin on 2005-12-31
The problem is just that currently I **can't** resize the partition.  Can someone point me out on how to maybe do this on the command-line?

---

