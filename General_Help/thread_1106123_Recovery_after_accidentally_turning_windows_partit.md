---
title: "Recovery after accidentally turning windows partition into linux swap"
date: 2009-03-25
forum: General Help
---

### Post by larrikin on 2009-03-25
Hi,
being totally unexperienced with Ubuntu, I turned my Windows Vista partition into a Linux Swap partition.
Is there any way to restore the data?

---

### Post by kanikilu on 2009-03-25
You didn't backup before installing a new OS?

If you chose to format it during the install, there probably isn't much hope of recovering a lot...also, if you are using the computer now, under Ubuntu, the more you use it, the less likely you are going to be able to recover anything. You're best chance to minimize overwriting is to use a Live CD for now.

You could try using a commercial data recovery software such as SpinRite, but I haven't personally used it, so can't really say much about it that you can't already find in reviews online.

Somewhere on these forums someone mentioned some native linux tools to do data recovery, I can't recall the specific programs, but I would think that if any live cd would have it, perhaps [SystemRescueCD](http://www.sysresccd.org/Main_Page) might...

---

### Post by 3Miro on 2009-03-25
> **kanikilu said:**
> You didn't backup before installing a new OS?

If you chose to format it during the install, there probably isn't much hope of recovering a lot...also, if you are using the computer now, under Ubuntu, the more you use it, the less likely you are going to be able to recover anything. You're best chance to minimize overwriting is to use a Live CD for now.

You could try using a commercial data recovery software such as SpinRite, but I haven't personally used it, so can't really say much about it that you can't already find in reviews online.

Somewhere on these forums someone mentioned some native linux tools to do data recovery, I can't recall the specific programs, but I would think that if any live cd would have it, perhaps [SystemRescueCD](http://www.sysresccd.org/Main_Page) might...

The chance of data recovery working is less than slim. The recovery might work, but I wouldn't get my hopes up.

---

### Post by igor. on 2009-03-25
You could also take a look at the tips from this article: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by coffeecat on 2009-03-25
Since this is now a Linux swap partition, boot into Ubuntu, open a terminal and..

**Edit:** *(I'm assuming you've got a workable Ubuntu installation on the computer with the reformatted Vista partition. If not, boot up with the live CD and do exactly the same. You can install testdisk to a live session - it's a tiny package - except that you'll lose testdisk when you power down.*

```
sudo swapoff -av
```That will stop any more writes to all swap partitions; therefore no more writes to the ex-Vista partition. If you need to boot up more than once, do this each time. Now open Synaptic (System > Adminstration > Synaptic) and install testdisk. This includes the utility photorec. I've never used it myself, but I've heard good reports of it. It's designed primarily to recover image files, but apparently it will cope with many different file types.

From the description in Synaptic:

> It is very useful in recovering lost partitions.
 It works with :
 * DOS/Windows FAT12, FAT16 and FAT32
 * NTFS ( Windows NT/2K/XP )
 * Linux Ext2 and Ext3
 * BeFS ( BeOS )
 * BSD disklabel ( FreeBSD/OpenBSD/NetBSD )
 * CramFS (Compressed File System)
 * HFS and HFS+, Hierarchical File System
 * JFS, IBM's Journaled File System
 * Linux Raid
 * Linux Swap (versions 1 and 2)
 * LVM and LVM2, Linux Logical Volume Manager
 * Netware NSS
 * ReiserFS 3.5 and 3.6
 * Sun Solaris i386 disklabel
 * UFS and UFS2 (Sun/BSD/...)
 * XFS, SGI's Journaled File System
 .
 PhotoRec is file data recovery software designed to recover
 lost pictures from digital camera memory or even Hard Disks.
 It has been extended to search also for non audio/video headers.
 It searchs for
 * Sun/NeXT audio data (.au)
 * RIFF audio/video (.avi/.wav)
 * BMP bitmap (.bmp)
 * bzip2 compressed data (.bz2)
 * Source code written in C (.c)
 * Canon Raw picture (.crw)
 * Canon catalog (.ctg)
 * FAT subdirectory
 * Microsoft Office Document (.doc)
 * Nikon dsc (.dsc)
 * HTML page (.html)
 * JPEG picture (.jpg)
 * MOV video (.mov)
 * MP3 audio (MPEG ADTS, layer III, v1) (.mp3)
 * Moving Picture Experts Group video (.mpg)
 * Minolta Raw picture (.mrw)
 * Olympus Raw Format picture (.orf)
 * Portable Document Format (.pdf)
 * Perl script (.pl)
 * Portable Network Graphics (.png)
 * Raw Fujifilm picture (.raf)
 * Contax picture (.raw)
 * Rollei picture (.rdc)
 * Rich Text Format (.rtf)
 * Shell script (.sh)
 * Tar archive (.tar )
 * Tag Image File Format (.tiff)
 * Microsoft ASF (.wma)
 * Sigma/Foveon X3 raw picture (.x3f)
 * zip archive (.zip)

---

### Post by mal_conductor on 2009-03-29
testdisk and/or photorec can help you.

Here are my note to do this.  The steps are simple.

[http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871](http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871)

---

