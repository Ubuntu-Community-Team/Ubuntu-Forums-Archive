---
title: "ran out of partition space :("
date: 2008-12-26
forum: General Help
---

### Post by Howitzer777 on 2008-12-26
if i uninstall a lot of programs in windows will the partition space grow in ubuntu? 

if not how do i add the free space?

---

### Post by damis648 on 2008-12-26
Sorry, it will not. You have done a full installation, correct? (NON-Wubi)?
If so, you will need to boot from the LiveCD and go to System>Administration>Partition Manager to resize the partitions.

---

### Post by drs305 on 2008-12-26
How big is your ubuntu partition?
Please post:
```
df -Th
```

If you think you should have more space and don't know what may have happened to it, take a look at this tutorial:
[URL="http://ubuntuforums.org/showthread.php?t=898573"] How To: Disk Full? - Check Your Trash
[/URL]

It will show you how to find hidden trash bins and also discuss other methods of freeing up space on your ubuntu partition.

---

### Post by 1packer on 2008-12-26
As long as you still have space on your hard drive you can increase your Ubuntu partition without deleting or installing anything. However, it is useful to free up space by removing things that you aren't using.
As long as your Windows partition is healthy the live cd should be able to shrink it and expand Ubuntu.

---

