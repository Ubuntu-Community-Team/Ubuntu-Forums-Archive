---
title: "How do I get a correct count of blocks in file"
date: 2009-05-28
forum: General Help
---

### Post by dstempfley on 2009-05-28
I need to get the number of 512 byte blocks in a file.  I'm confused because I get two different results from 4 different methods.  Is this the blocks of data and the number of blocks allocated on disk? 

$ ls -s --block-size=512 Pictures.sqsh
[COLOR="Blue"]59264[/COLOR] Pictures.sqsh
$ stat '--format=%n %b %B' Pictures.sqsh
Pictures.sqsh [COLOR="Blue"]59264[/COLOR] 512

$ ls -l --block-size=512 Pictures.sqsh
-rwx------ 1 dion dion [COLOR="Blue"]59192[/COLOR] 2009-05-28 09:14 Pictures.sqsh
$ dd if=Pictures.sqsh of=/dev/null bs=512 status=noxfer | tail -1
[COLOR="Blue"]59192[/COLOR]+0 records out

---

### Post by Brandon Williams on 2009-05-28
Both ls -l and dd are telling you how many 512-byte blocks worth of data are actually in the file. On the other hand, ls -s and stat are both telling you how many 512-byte blocks worth of space are allocated for the file. There will typically be more blocks allocated for the file than the amount of data in the file requires, especially if you use 512-bytes as the block size, since your actual I/O block size is more likely to be 4096 (but almost always bigger than 512).

---

