---
title: "Strange File - Want to get rid"
date: 2006-06-11
forum: Desktop Environments
---

### Post by shinygerbil on 2006-06-11
Hi all,

I have a strange problem. On my second partition (which is mounted on the folder "files" inside my home folder), there is a file called console_log.txt which is 1431655765 bytes (yes that's 1.4GB!!) with the owner 1431655765 and group 1431655765. According to ls:
```
?r-x-wSr-x 21845 1431655765 1431655765 1431655765 2015-05-15 03:09 console_log.txt
```
(the console_log.txt is highlighted in brown)

So it appears to be an unknown file, possibly something corrupt. I have a feeling it was generated when I was trying to download a >2GB torrent file using utorrent through wine but cancelled halfway through. Perhaps this is the downloaded data that's been corrupted in some way, but whatever it is, the problem is simple.

How do I get rid of it? It won't even let me do it as super user. I've tried regular deleting and shredding, changing permissions, nothing works!

Any help would be much appreciated. (it feels weird to be asking questions again ;) )

Thanks in advance

Steve

---

### Post by tepidpond on 2006-06-11
It seems that your drive may be corrupted in some way.

The best way to fix it is to unmount that particular drive, then run fsck /dev/{whatever partition you have}. After that you should be able to remount it and rm that file.

---

### Post by shinygerbil on 2006-06-11
Running fsck, I'm getting a LOT of errors of the sort:

```
Inode <number>, i_blocks is <some enormous number>, should be 0.
```

I guess that's the problem :)

---

### Post by shinygerbil on 2006-06-11
Yep, it's fixed, works fine now :D The file didn't actually exist; after running fsck the file was just...gone.

Thanks very much!

Steve

---

### Post by shinygerbil on 2006-06-11
Well, it doesn't seem to have reclaimed the free space :(

---

