---
title: "non-contiguous files?"
date: 2005-12-27
forum: General Help
---

### Post by not_yet on 2005-12-27
boot up today was paused for a forced file check

a message indicated there are 2.1% non-contiguous files

how do I make them contiguous? 

thanks

---

### Post by amohanty on 2005-12-28
> man fsck
manual: [http://www.manlib.com/man/321](http://www.manlib.com/man/321)

---

### Post by lol on 2005-12-28
As far as I know, there is no way to defrag an ext3 filesystem, because there is no need to do so in the first place (well, it IS possible, but there is no easy way to do so).

There is a tool to defragment ext2 filesystems (but as for ext3, it's more or less useless, and always dangerous to use), which is called "defrag". You can try "defrag ext3" in Google, and you will soon understand that you shouldn't bother with this...

---

### Post by psusi on 2005-12-28
Yes, the short answer is don't bother, it isn't really a problem so don't sweat it.  

If you REALLY want to defrag though, you can try the defrag program ( installable via synaptic ).  To do this you will need to convert the partition back to ext2 with tune2fs, then back to ext3 after the defrag.  You also will need to do this from the livecd as you can't defrag a partition while it is mounted.  There is also a chance it can destroy your data, especially if the power fails in the middle, so make sure you have recent backups.

Regular defragmenting is required in windows because windows allocates blocks on the disk in about the most stupid manner possible, which quickly leads to files having hundreds of fragments.  It is typical for you to save a 100 MB file in windows and have it split into 500 or more fragments, which is VERY bad for performance.  Under Linux, it might break into  2 to 10 fragments, but you really can't notice the performance loss from that few fragments.

---

### Post by timseal on 2005-12-28
copy the file to a different partition, and back again

---

