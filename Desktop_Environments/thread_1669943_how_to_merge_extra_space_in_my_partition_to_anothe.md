---
title: "how to merge extra space in my partition to another partition?"
date: 2011-01-18
forum: Desktop Environments
---

### Post by ankur.trapasiya on 2011-01-18
Hello ... 
I have installed my ubuntu on 100GB partition and there is so much free space on it so that i want to merge that partition with my existing ntfs  windows partition...

Can anyone please tell me how to do that ??

Thanks in advance ...

---

### Post by ajgreeny on 2011-01-18
Boot to the live ubuntu CD/USB and use gparted to shrink the ubuntu partition by pulling the left hand end to the right as far as you want.  If it is the second or later partition on disk, it will take quite a long time and will go through a system check bith before and after doing the shrinking job.  Whatever you do, **DO NOT STOP THAT BEFORE IT FINISHES**, sorry about the shouting, but it is important.

When that is all finished, boot into ubuntu to check all is well with that.

Finally, if it is Vista or Win7, boot into windows again and using the disk management utility, enlarge the windows partition to fill the free space.  If it is XP you will need to do this using gparted, again from the live ubuntu CD/USB, as XP has no disk management system like Vista or Win7.

The alternative which will be much faster, would be to shrink the ubuntu partition with gparted from the right hand end, leaving free space at the end of the disk, and making the free space into an ntfs partition which can then be used in both OSs.

---

