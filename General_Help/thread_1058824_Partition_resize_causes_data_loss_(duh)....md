---
title: "Partition resize causes data loss (duh)..."
date: 2009-02-03
forum: General Help
---

### Post by pmooney78 on 2009-02-03
I never thought it would happen to me ...

I enlarged a partition (NTFS) using gparted. It's on an external USB drive, and I enlarged it from 120 to 130 GB. Now, Thunar shows an empty disk, and using "ls -a" in a terminal also shows no files. But Thunar reports only 11GB of free space, which is about right if there was still data on it. This makes me hopeful. The partition, of course, had all of my music on it.

Any suggestions for data recovery? I haven't touched the disk at all. Part of me wants to boot into Windows and run chkdsk, but I'd really hate to have a bunch of "fileXXXX.chk" songs. (Of course, this is better than nothing, but would still be an enormous pain to recover from ...)

Thanks in advance for any help.

---

### Post by timcredible on 2009-02-03
did you add to the partition from the beginning or the end.  if you add to the end of a partition, or remove from the end, you're ok.  if you add or remove from the beginning, you lose the info on where the files are.

---

### Post by pmooney78 on 2009-02-03
Added to the beginning. Problem solved by rebooting into XP ... which made all of the files visible again. 

Thank you.

---

