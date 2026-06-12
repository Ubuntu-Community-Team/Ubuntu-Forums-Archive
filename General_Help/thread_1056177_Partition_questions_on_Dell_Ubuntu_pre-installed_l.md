---
title: "Partition questions on Dell Ubuntu pre-installed laptop"
date: 2009-01-31
forum: General Help
---

### Post by kiwi8mail on 2009-01-31
I am in possession of a Dell Inspiron 1525 with Ubuntu pre-installed.  I want to create a separate partition to separate the OS from my created files (docs, photos etc) that I will be adding to it, and I have a few questions.   The documentation from Dell on Ubuntu is pretty-much non-existent, but I do have some prior experience with Ubuntu.

(The hard drive already contains a number of existing partitions - I've created a list below my posting.)

So far, I have upgraded to 8.10 and installed a few other things (VLC, gparted etc), but the computer is untouched otherwise.   My questions are:

(1) Do I really _need_ to create a separate partition like this?   I have separate partitions on my older ubuntu laptop.   That was incidentally a dual boot XP/Ubuntu machine where there had to be a separate fat32 partition that both OSs could use for documents, but even with just a one-OS machine, I was under the impression that it was good practice to have the OS and docs on separate partitions.

(2) Is 15GB enough for for the OS partition, to allow for installation of additional programs? Or too large?

(3) Any particular reason to choose ext3 over fat32 for the document partition? No file is over 4GB, my back-up drive is in fat32 - I ask this because I've noticed in the past that reading and writing between the two formats can be slow.

(4) There is an existing small fat32 partition on the laptop already (see below).   Do I need this?   It has a [misleading?] label of "OS" and mounts as a separate drive on startup.   It seems to be some sort of recovery partition, or place to store utilities.   It contains material in a variety of folders (named: casper, debs, dists, docs, grub, isolinux, misc, pool, preseed, and scripts).  I'm going to make a recovery disk anyway (a link/utility on the desktop encourages me to do this).   Once that's done, if I can copy the contents of this partition to an external drive, do I still need this partition?

EXISTING PARTITIONS:
The 250GB drive came from the factory divided as follows:
   /dev/sda1	A fat16 partition of 109MB, only 9MB of which is used
   /dev/sda2	A fat32 partition of 3GB, 1.87GB of which is used.   
   /dev/sda2	An ext3 partition of 228GB, of which about 10GB is used.   This is of course the boot partition
   /dev/sda4	A 1.92GB extended partition
   /dev/sda6	A 1.92GB linux-swap partition

---

### Post by Toet on 2009-01-31
2) Same I always use, and is a perfect size I think.

3) ext3 is a lot more reliable

---

### Post by Gizenshya on 2009-01-31
2)  Its what I use now.  My last install was 8 or so GB if I remember correctly, and it wasn't enough for doing basic things that I like to do.

3)  I've had problems with ext3 and windows/mac.  fat32, on the other hand, is automatically recognized and fully compatible across the board.  I would prefer to use it over ext3 because of that, and for the 4gb file limit.  ISO's can get over that easily nowadays (though you said that shouldn't be a problem for you).  I've never had a problem with reliability on FAT32.  Theoretically, yes, ext3 is better for reliability, but I was quite content with my fat32 drives.

---

### Post by Toet on 2009-01-31
> I would prefer to use it over ext3 because of that, and for the 4gb file limit.

Fat32 has a 4GB filelimit.

---

### Post by mb_webguy on 2009-02-01
1)  Need?  Well, no.  You can live just fine with everything on one big partition.  But having a separate /home partition can make reinstalling your operating system considerably easier.

2)  15GB is more than enough for Ubuntu.  I would recommend 8 to 12GB.  I personally have Ubuntu on a 12GB partition.  I'm only using about 6.5GB of that, and I have a considerable amount of software installed.

3)  You should use ext3.  FAT32 is a very old filesystem, and more modern filesystems like ntfs and ext3 have quite a few features lacking in FAT32, such as journaling.  FAT32 also is not capable of handling Linux-style file permissions, and the entire partition would have to be mounted with the same user, group, and permissions.  FAT32 should only be used for portable storage, because while it is a sub-optimal filesystem, it's the most widely supported across multiple platforms.

4)  You don't need this partition.  I've had numerous Dell computers over the years, and I have never once used a recovery partition.  In fact, I generally reformat my drive upon receiving a Dell to reclaim this waste of space.  All you really want is a / partition of between 8 and 12GB, a swap partition equal in size to your system memory, and a /home partition that takes up the rest of the drive.

---

