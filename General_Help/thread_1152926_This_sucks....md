---
title: "This sucks..."
date: 2009-05-08
forum: General Help
---

### Post by joshaman on 2009-05-08
I have this issue - when I unRAR an archive with File Roller or even 7zip, the computer will freeze to the point of not being able to use other programs.  For instance I'll click programs that are already open in the panel and they've basically stopped responding.  

I've checked my resources and Ubuntu doesn't use even 20% of RAM during this time, so I don't think it's a RAM issue.  During this time it also hardly uses the CPU.  Plus, it hardly uses the swap partition.  I've tried changing file-roller's priority to 19, but that doesn't fix anything.  I think it has to do with using the HDD, because this problem gets worse as the stress on the HDD increases.

---

### Post by joshaman on 2009-05-08
When I extract to a NTFS partition in which I use to trade between XP and Ubuntu (which is about 7 GB total and 90% free space) the problem does NOT occur at all.  This leads me to believe that the problem is occurring on the ext3 partition because of low free disk space (about 20 GB total and 9% free space) and maybe fragmentation.

The more free space I free up on the ext3 partition, the better it's performing.

---

