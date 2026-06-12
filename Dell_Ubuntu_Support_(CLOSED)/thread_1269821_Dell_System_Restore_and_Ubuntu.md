---
title: "Dell System Restore and Ubuntu"
date: 2009-09-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Pen Spinner on 2009-09-18
Hello.  I have a Dell E510 with windows xp and ubuntu 8.10.  I have a partition for ubuntu, /home, and windows.  I want to reset windows to factory settings using the Dell System Restore Utility.  Will this affect/delete my linux partitions?  Thanks everyone.

---

### Post by gbrainin on 2009-09-18
Yes.  The system restore returns the hard drive to its factory configuration, including repartitioning if necessary.

You could, of course, recreate your Ubuntu partitions the way you did it the first time, but that would take some effort.  Definitely back up your /home partition first.

---

### Post by linux_tech on 2009-09-19
The system restore is faster than a fresh install because you do not need to reinstall drivers

---

### Post by Pen Spinner on 2009-09-20
So if I use the system restore, I need to backup my home partition.  Is there an easy way to backup the whole partition on a DVD?  Thanks everybody.

---

### Post by gbrainin on 2009-09-21
There's a program called partimage that allows you to back up entire partitions.  However, the partition you're backing up needs to be not mounted when you do it.

---

