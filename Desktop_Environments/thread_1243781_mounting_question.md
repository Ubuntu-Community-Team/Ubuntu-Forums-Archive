---
title: "mounting question"
date: 2009-08-18
forum: Desktop Environments
---

### Post by thundaraptor on 2009-08-18
I have a 1 tb hdd with 25 gb partitioned with main ubuntu install and 975 gb partition had old ubuntu install on it.  I reformatted the 975 partition.  Now, in jaunty 64 the partition shows up as 961 gb which is correct but if I check the properties of the drive it shows total capacity of 881 gb of which 45 gb is used.  I am curious what this means.  I reformatted the 975 so there shouldn't be anything on it right but there is a folder called 'lost+found' that doesn't have anything in it on it but can't be deleted or browsed via the gui.  what is going on?

---

### Post by DaithiF on 2009-08-18
Hi,
possibly the 5% reserved space feature of ext filesystems
have a read through this thread for how to confirm whether this is the case, and how reduce the 5% if you wish.
[http://ubuntuforums.org/showthread.php?t=1239907](http://ubuntuforums.org/showthread.php?t=1239907)

---

