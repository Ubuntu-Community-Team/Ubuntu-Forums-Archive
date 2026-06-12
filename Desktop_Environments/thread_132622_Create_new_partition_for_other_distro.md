---
title: "Create new partition for other distro"
date: 2006-02-18
forum: Desktop Environments
---

### Post by plexi50 on 2006-02-18
I can't seem to find a clear explaination of how to do this. I have Ubuntu installed /dev/hd1 and my swap is /dev/hd5. Qtparted also shows /dev/hd2 extended, but used space on that is N/A. I guess I need to create a new partition or resize my hd1. Can it be done or should I have planned for this in the beginning? Plenty of HD room and I would only need about 4gig for what I want to do.

---

### Post by cilynx on 2006-02-18
hda2 is extended...that means that it has other partitions inside it.  Your swap on hda5 is actually inside of hda2.  

To answer the question:

Check out 'gparted'.  It's like Partition Magic if you've ever used that...other than the fact that gparted actually works...

---

