---
title: "hard drive question"
date: 2009-02-02
forum: General Help
---

### Post by tsmgroup2 on 2009-02-02
I've noticed on more than one system that the 164 gb drives that are installed on a couple of my systems that whether Ubuntu or MS Windows XP get installed that both systems have automatically a sum of around 15 gb of hard drive space placed in reserve and inaccessible by me.

First, Is this normal?

Second, how do I access this space and make use of it?

Third, If I can't use it, can someone please tell me what it is?  

Thanks in advance.

---

### Post by drhex on 2009-02-02
It could be that your "164GB" is 164 * 1000 * 1000 * 1000 bytes  (as harddrive manufacturers see it), while the operating system uses computer kilobytes and sees it as approximately 153 * 1024 * 1024 * 1024 bytes.

Also, the ext2/3 filsystems typically reserve 5% or so for use only by the superuser (so that if the filesystem gets full, it will be possible for the superuser to compress a file and temporarily store both the original and the compressed file).  That can be changed with the "tune2fs" command

---

