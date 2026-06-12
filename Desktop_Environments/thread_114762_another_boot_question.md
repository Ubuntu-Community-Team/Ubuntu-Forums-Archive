---
title: "another boot question"
date: 2006-01-09
forum: Desktop Environments
---

### Post by Jaakdedraak on 2006-01-09
I looked in the hundred's of boottopics but didn't found this one:

I have 1 hard disk, with 2 partitions (and swap) , 1 has linux and 1 has windows.

I first installed Linux, and afterwards I installed Windows. No my pc only boots in Windows, how do i change the bootflag or how do i solve this problem?

I can only enter in linux with the live cd

---

### Post by frodon on 2006-01-09
All you have to do is to re-install GRUB because the windows install process destroyed it : [http://www.ubuntuforums.org/showthread.php?t=76652](http://www.ubuntuforums.org/showthread.php?t=76652)

---

### Post by Thirsteh on 2006-01-09
That's not all. Since it's on the same harddrive, you MUST and I mean MUST defragment your drive in Windows before you install Grub, or you will not be able to boot Windows after the installation.

---

### Post by lamego on 2006-01-09
What ?
Installing a boot loader has nothing to do with fragmentation.
You don't need to defrag anything, you only would need to defrag if you want to do a partition resizing, on that case the disk area which you want to free for a new partition needs to be free, thats why you defrag on such case.

Just reinstall grub...

---

### Post by Thirsteh on 2006-01-09
lamego, try it out for yourself. We'll see who's laughing in the end :) A somewhat used and fragmented Windows partition of course, then install any Linux distribution. Good luck, rofl.

Jaak, just defragment before you install, it'll spare you hell.

---

