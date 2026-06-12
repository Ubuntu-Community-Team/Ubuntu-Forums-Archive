---
title: "Hibernate causing loss of HDD free space?"
date: 2007-12-19
forum: Dell  Ubuntu Support
---

### Post by Threlkeld on 2007-12-19
Inspiron 6400 (UK version of 1505n) standard configuration for Dell-installed Feisty.
I've lost about 33GB of my 60 GB HDD. 
Disk Usage Analyser only finds 12 GB of actual files, but indicates only 7.4GB of free space. The loss increases over time.
I notice that when I close the lid I occasionally can't resume. The laptop is locked on opening and I've had to turn it off at the power button. Is it possible that the hibernate file then remains present but 'lost' to the file system?
For the present I'm not hibernating at all to see if this holds the problem. I notice that when fsck is forced automatically (after 24 boots) it hangs for an age at 46.1% and takes something like 40 minutes to scan to 100%. It doesn't change anything, however. I'm worried at these symptoms. Any ideas?

---

### Post by m94mni on 2007-12-19
That could well be a HDD failing.

Hibernate uses the swap partition, so your normal partition should not be affected.

I would grab a LiveCD (Fiesty or gutsy) and check the partition from there.

---

