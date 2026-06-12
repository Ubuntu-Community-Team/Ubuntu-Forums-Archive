---
title: "Best FS?"
date: 2006-01-18
forum: General Help
---

### Post by Killgore on 2006-01-18
I was wondering what the best Ubuntu supported filesystem would be? Is ext2 fine for normal use? I would like to try something like ReiserFS if Ubuntu supported it natively.

---

### Post by 23meg on 2006-01-18
Every filesystem has its own strengths and weaknesses. EXT3 is a good default for Ubuntu that you should prefer over EXT2, and ReiserFS is supported, so you can try it.

---

### Post by Stereotypical Rage on 2006-01-18
Are you the Killgore I know? From Norwhich college, lives in the NH region, etc.

ReiserFS v3 is native, that I know, but not default.
ext3 is default.

---

### Post by earobinson on 2006-01-18
Right job for the right tool [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

The default install is perfect for any normal user.

EDIT: 23mebs posts before me 2X in a row now :(

---

### Post by magnusbb on 2006-01-18
For a stable, and safe file system for server and desktop usage,   I'll reccommend ext3. For a fast, but not so safe (in my opinion) ReiserFS would be the one.

The default is ext3, and if you're unsure, I'd stick to that. But don't use ext2, as it is not a journalizing FS.

---

### Post by Killgore on 2006-01-19
After reading that article you linked to earobinson im interested in running an XFS based Ubuntu installation. When i make the partitions in the installer what should i do? Id like to just have a boot partition, swap and storage space. How big should a boot partition be?

Stereotypical Rage no its not the Killgore you are thinking of.

---

### Post by yaztromo on 2006-01-19
I would recommend Reiserfs. It's fast and perfectly safe.

---

### Post by RikoW on 2006-01-19
You also want to consider whether you need to access data on the Ubuntu file system from you windows system (if you have a dual boot). There is a freeware programm called explorefs, which runs under all windows flavors and lets you read ext2 and ext3 filesystems:

 [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm]("http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm")

It does not support any of the other options mentioned here , like reiserfs, xfs.

I found that little very useful on my dual boot XP/Ubuntu (with ext3).

---

### Post by 23meg on 2006-01-19
There's also the [EXT2IFS]("http://www.fs-driver.org/") driver which mounts your  EXT2/EXT3 volume like a normal Windows partition and lets you access it with explorer.

---

### Post by JAwuku on 2006-01-19
If you have Reiserfs, you can still access these partitions in Windows via a program called Yareg.

It depends on the .NET framework in Windows, and allows you to drag and drop.

Its website is at [http://yareg.akucom.de/]("http://yareg.akucom.de/")

---

### Post by Davyp on 2006-02-02
You can also access reiserfs, ext2 and ext3 linux partitions from windows using Ltools:

[http://www.it.fht-esslingen.de/~zimmerma/software/ltools.html](http://www.it.fht-esslingen.de/~zimmerma/software/ltools.html)

I've used the program to access reiserfs but not ext2 or ext3, but no reason to think it wouldn't work.

---

### Post by el3ktro on 2006-02-02
My thoughts:

Ext3: Definitely the most tested & most stable, it's fast & doesn't consume much CPU. It's Ubuntus default and always a good choice.

ReiserFS: Also very stable (I never had problems, was running it for years). Faster than Ext3, but also consumes more CPU time. Mounting large Reiser partitions (>100GB) takes noticeable longer than mounting an Ext3 partition of the same type, my prev. 220 GB Reiser partition took something like 10 secs to mount.

XFS: Also very fast, but I can only tell from my experience that I _really_ had problems with it after my laptop just shut down suddenly because of an empty battery. The partition was not usable afterwards & I had to reformat. This never happened to me with Ext3 or ReiserFS

S, I'd go with Ext3, or if you have a fast CPU & want a little more speed, then ReiserFS.


Tom

---

### Post by ximok on 2006-02-03
[QUOTE=el3ktro]My thoughts:

XFS: Also very fast, but I can only tell from my experience that I _really_ had problems with it after my laptop just shut down suddenly because of an empty battery. The partition was not usable afterwards & I had to reformat. This never happened to me with Ext3 or ReiserFS
[/QUOTE]


Yeah, XFS, as cool as it can be, has a few drawbacks.  Even though it is Journalled like EXT3 and Reiser, it really doesn't like having to replay the journal sometimes.  In addition, it scales up nicely, but won't go back down.  XFS really should only be used if you plan to work with really big files (1gig+) on a regular basis or if you need a system that will nicely scale beyond 1TB.  (Some filesystems claim they work well past 1TB, but most don't compare to the performance that exists in XFS)

---

