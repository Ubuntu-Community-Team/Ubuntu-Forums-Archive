---
title: "Recover data from unknown file types?"
date: 2005-11-27
forum: Desktop Environments
---

### Post by awtomlinson on 2005-11-27
I had several problems with xorg, which lead to a blank screen of death, & an eventual fresh reinstall of breezy.  see the following thread if you have plenty of time:

[http://ubuntuforums.org/showthread.php?t=86972&highlight=blank+screen+death](http://ubuntuforums.org/showthread.php?t=86972&highlight=blank+screen+death)

anyway, on my original install, i have a separate /home partition.  this /home partition now has something wrong with it.  some of my directories/folders now display as an unkwown file type and the file size is displayed as unknown.  they have the gnome foot icon on them.  i cannot open these folders at all.  even though the size is displayed as unknown, they must still be their original size, as the free space available on the partition is unchanged since this issue began.  i deleted all files on the partition other than my documents to ensure that the xorg issue did not reoccur.  when i mount this partition on my fresh install, it is very slow to read.  it takes forever to open a good folder and the system frequently freezes temporarily when trying to access the partition.  how can i recover data from these unknown file types?  has this partition gone bad & need to be reinstalled?

---

### Post by teaker1s on 2005-11-27
I'd suggest data recovery software as this can often extract folders on damaged drives by starting back to front read of affected drive
next time don't reinstall just sudo dpkg-reconfigure xserver-xorg

---

### Post by awtomlinson on 2005-11-27
thanks, can you suggest any particular data recovery software for linux?

---

