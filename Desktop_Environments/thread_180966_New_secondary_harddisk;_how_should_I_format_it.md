---
title: "New secondary harddisk; how should I format it?"
date: 2006-05-23
forum: Desktop Environments
---

### Post by Rxke on 2006-05-23
Simple question, really:

I have an extra HD, but not sure in what filesystem to format it, ext2, ext3... What is the best, most suitable on an Ubuntu-only machine?
Will be mainly used for mediafiles, and absolutely no cross-compatibility requirements, so no need for FAT-32 schemes... Probably 2 useable partitions.
I guess gparted is probably the best/simplest tool to go?

---

### Post by Ramses de Norre on 2006-05-23
You'll probably want ext3 or reiserfs. They both have their own advantages but if your a normal user I'd just use the default ext3.
And gparted will work perfect on Linux native partitions.

---

### Post by Rxke on 2006-05-23
Thanks!
I did try it before getting advice, and seems like I hosed my partition table or something, will have to delve a bit deeper how to create a disk from scratch and have it consequently mounted etc. automatically...

---

### Post by Rxke on 2006-05-23
Got it working at last, thanks largely to this q&a: [http://www.ubuntuforums.org/showthread.php?t=179791](http://www.ubuntuforums.org/showthread.php?t=179791)

---

