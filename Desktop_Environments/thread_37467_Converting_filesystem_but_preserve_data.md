---
title: "Converting filesystem but preserve data?"
date: 2005-05-27
forum: Desktop Environments
---

### Post by Stealth on 2005-05-27
I've been reading about Reiser and apparently people like it more compared to ext3. So I was wondering if my Ubuntu install could easily convert to a Reiser partition without losing any data?

---

### Post by Xian on 2005-05-27
[QUOTE=Stealth]I've been reading about Reiser and apparently people like it more compared to ext3. So I was wondering if my Ubuntu install could easily convert to a Reiser partition without losing any data?[/QUOTE]
I don't think parted is capable of that. However, you should be able to move the data into another partition, re-format the original ext3 and then move it back without any issues. You'd just need to update the fstab entries to reflect the new file system.

---

### Post by ltmon on 2005-05-27
Better yet, back up your data externally.  I've lost count of how many times I've killed stuff while playing around with the partition table and filesystems ;) 

As far as Reiser being better, I'm not sure you'll notice the difference.  They're both journaled file systems, which means no defragging and low probability of corruption on a crash.

The only time you notice differences with things like that is if your running some kind of high use database or similar.  I've used both on the desktop and have noticed no difference.  Maybe you would notice if you had to copy several GB frequently.

L

---

### Post by haiku72 on 2005-06-21
Check my post at :

[http://ubuntuforums.org/showpost.php?p=222067&postcount=6](http://ubuntuforums.org/showpost.php?p=222067&postcount=6)

---

