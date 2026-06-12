---
title: "Tools for defragin'"
date: 2005-10-12
forum: Desktop Environments
---

### Post by idn on 2005-10-12
Are there any tools with a gtk front end that can be used to defrag my HDD?

Cheers

---

### Post by PatrickMay16 on 2005-10-12
The filesystems used by Linux don't need defragmenting, so there're no tools to do that, I think.
In any case, I'm not an expert on this.

---

### Post by idn on 2005-10-12
Awesome! I love Linux! No more sitting in front of a creaking hard drive and defrag tool!

---

### Post by robins_web on 2005-10-13
[QUOTE=idn]Awesome! I love Linux! No more sitting in front of a creaking hard drive and defrag tool![/QUOTE]

Yeah--now you'll have to find something *productive* to do while you wait for the tea kettle to boil! :grin:

---

### Post by xmastree on 2005-10-13
```
sudo apt-get install cappuccino

cappuccino
```**That's** productive! :cool:

---

### Post by wylfing on 2005-10-13
[QUOTE=PatrickMay16]The filesystems used by Linux don't need defragmenting, so there're no tools to do that, I think.
In any case, I'm not an expert on this.[/QUOTE]

Just to be sure this is definitively answered: the file systems commonly used on Linux (e.g,. Reiser3, Reiser4, ext2, ext3, jfs, etc.) do not require defragmenting. Only crummy Windows file systems need to be defragged.

---

### Post by Wolki on 2005-10-13
Common linux file systems tend to fragment very little, and some fragmantation can actually be healthy. There can be fragmentation problems on very full partitionas however, since the file system is then forced to fill the gaps between files with parts of other files. Unfortunately, if someone encounters this problem, I do not know of a defragmentation program. You can, of course, copy the files to another hdd and then back, this should fix it.

It is always good to make sure that partitions (especially system partitions) don't become too full. Don't worry too much, this should happen only on very rare circumstances.

fsck will tell you how fragmented your drive is, if you're interested. Use it only on partitions that are not mounted.

(disclaimer: I'm no file system expert, so most of this is second-hand knowledge)

---

