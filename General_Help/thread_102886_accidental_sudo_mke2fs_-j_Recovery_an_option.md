---
title: "accidental sudo mke2fs -j Recovery an option?"
date: 2005-12-13
forum: General Help
---

### Post by mbollenb on 2005-12-13
Following a tutorial for mounting a second hard dirve I came across a line sudo mke2fs -j /dev/hdb1 which I did not know what it was.  Being new to linux I typed it in and formated my entire storage drive with 3 years worth of work on it.  Anyway to recover these files?  The only files I am concerned about are in .rar format

---

### Post by kosmic on 2005-12-13
Try using this application -> [http://e2undel.sourceforge.net/]("http://e2undel.sourceforge.net/")
 
 
If your drive was formated with ext3 then i'm sorry but you can recover your data.
 
[I]"In order to ensure that ext3 can safely resume an unlink after a crash, it actually zeros out the block pointers in the inode, whereas
ext2 just marks these blocks as unused in the block bitmaps and marks the inode as "deleted" and leaves the block pointers alone. 
Your only hope is to "grep" for parts of your files that have been deleted and hope for the best."
[/I]

---

### Post by casperlingus on 2005-12-23
I read the post where you saw that formatting line and I feel terrible for you, I hope you can get back everything you lost.  

I do not know much about this topic, but I do know that it is possible, unless the data was *shredded* (man shred) that the data is still there and accessible *somehow*.  There are services to which you can take your harddrive and they will recover lost data for situations like this.

It might cost a pretty penny, but it might also be worth it if the 3 years of work is not recoverable otherwise.  I believe it's simply called a "data recovery service."   There's also software packages that are designed for situations like this.  I'm rooting for you.

Casper...

---

