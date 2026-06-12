---
title: "help with backup files"
date: 2009-05-17
forum: General Help
---

### Post by linuxted on 2009-05-17
For backups I have a linux drive formatted as ext3

How do I get a Mac to recognize it?

Should I reformat this drive as FAT32?   Sorry, I'm pretty clueless here.

If I need to rewrite the data in a different format please give me some pointers (ie. what type and which package would make it easy).


Thanks, 
linuxted

P.S. I posted a similar topic in the Apple area.   I'm desperate as my linux machine has a 30% rate of booting correctly and I may lose all my data if I don't switch soon.    I don't know what the cause of the issue.   My attempts to fix it have failed.   It is some sort of hardware problem.

---

### Post by mb_webguy on 2009-05-18
Mac OS X doesn't read or write to ext2 or ext3 natively (which is a bit odd if you ask me, since OS X is a Unix-based OS just like Linux).  You'll have to install the [ext2fsx]("http://sourceforge.net/projects/ext2fsx/") driver on the Mac in order to access files on an ext2 or ext3 partition.

---

