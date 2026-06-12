---
title: "How To Clean Up Disk Space??"
date: 2009-12-15
forum: Desktop Environments
---

### Post by acho on 2009-12-15
I had some problem Today... Please help me!!

My Disk Space is too low for root partition[/].. is there any idea to clean my disk space without to use add/remove application or uncheck synaptic....thx.

---

### Post by drs305 on 2009-12-15
Do you have a normal-sized partition (8GB or greater)?  (run "df -h" to check). If you recently did an install with the "side by side with Windows" option it may have created a partition of about 2.5GB that is too small to operate Ubuntu successfully. I wrote some guides about this problem if this is the case.

If you have been running it for a while and have now found you have run out of free space, this guide for troubleshooting the problem will probably be helpful. If you have questions, just ask.
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

The usual suspects are undeleted trash, large log files, or a backup which was written to the system partition instead of a backup partition.

Added: You can use the command line to empty the downloaded cache folder with this command:
```

sudo apt-get clean

```

---

### Post by Maheriano on 2009-12-15
There isn't really an update option in Linux because the EXT file system doesn't fragment files like NTFS does. So basically deleting things is really all you need to do. Remove applications you don't need or files you don't use. Or if you're really strapped, use GParted to increase the size of your partition, stealing space from somewhere else.

---

### Post by acho on 2009-12-15
Thx for your help everybody....;)

I'll try to remove some useless app...

---

