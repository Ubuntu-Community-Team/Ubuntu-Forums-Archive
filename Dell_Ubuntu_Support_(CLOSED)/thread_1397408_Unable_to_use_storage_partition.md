---
title: "Unable to use storage partition"
date: 2010-02-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jl2035 on 2010-02-03
I want to have two partitions. A linux filesystem and one 'storage device'. This one was first FAT32 but I had some problems with it(I posted here: [http://ubuntuforums.org/showthread.php?t=1380109](http://ubuntuforums.org/showthread.php?t=1380109)) so I formated it to ext2. Now I can't even mount it:

[IMG]http://www.shrani.si/f/h/Xb/34vpYQZB/screenerror.jpg[/IMG]

If I open the Storage Device Manager I see that it didn't realize the changes... It still thinks that the partition is FAT32. I even reinstalled Storage Device Manager, but that didn't change anything. Did I do something wrong, or is this some kind of bug??

By the way: I have a Dell Studio 1555 laptop.

---

### Post by mikewhatever on 2010-02-03
Open /etc/fstab and change the file system for fat32 to ext2. Post the output of <cat /etc/fstab> if not sure what to do.

---

### Post by jl2035 on 2010-02-03
Thanks dude! This has been bothering me for a few weeks now!

---

