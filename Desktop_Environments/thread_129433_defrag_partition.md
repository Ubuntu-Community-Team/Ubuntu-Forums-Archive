---
title: "defrag partition"
date: 2006-02-13
forum: Desktop Environments
---

### Post by Digitu on 2006-02-13
how do i defrag ubuntu's partition??

---

### Post by alfotis on 2006-02-13
What filesystem?

---

### Post by GTvulse on 2006-02-13
[QUOTE=Digitu]how do i defrag ubuntu's partition??[/QUOTE]

You don't. Even with heavy usage the filesystems used with linux are much better handling file fragmentation than FAT or NTFS.

---

### Post by alfotis on 2006-02-13
hell yeah. But you can tune a reiserfs partition with certain programs

---

### Post by Digitu on 2006-02-13
[QUOTE=alfotis]What filesystem?[/QUOTE]
to tell u the truth i dunno wot filesystem im using, but it aint FAT/NTFS, it aint being recognised by windows. just that i no its linux or unix

---

### Post by GTvulse on 2006-02-13
[QUOTE=alfotis]hell yeah. But you can tune a reiserfs partition with certain programs[/QUOTE]

Yeah. It is correct that you can control small-file packing by using a mount option. But contrary to ext2/3, there are no parameters settable in the partition's superblock, that would affect performance. You can modify other settings though.

I also made a small fib. JFS does need defragmentation from time to time, but the utility has yet to be written, according to what I read in the jfs development mailing list at SourceForge (some post during the last 4 monnths, it is in the archives).

---

### Post by jerome bettis on 2006-02-13
[quote=Digitu]to tell u the truth i dunno wot filesystem im using, but it aint FAT/NTFS, it aint being recognised by windows. just that i no its linux or unix[/quote]

yep you don't need to worry about defragging it then.  fragmentation is a design issue in the way FAT works .. it came from QDOS, which stands for quick and dirty operating system.  most unix file systems work very differently and do not fragment, you're probably using ext2 or reiserfs.

---

