---
title: "Moving /home from a folder to a partition"
date: 2005-11-13
forum: Desktop Environments
---

### Post by veloct on 2005-11-13
I have GParted but I can't unmount my /root partition to create a /home partition and move /home to it.  How can I do this?

---

### Post by aysiu on 2005-11-13
With a live CD.

---

### Post by psusi on 2005-11-13
Or the old fashioned way.  Use fdisk from the command line to create a new partition from free space on the disk, save and reboot, then format the new partition ( eg. mke2fs ), mount it somewhere empty like /mnt, copy all the files over, then delete everything in /home, unmount from /mnt, and mount it in /home instead.  

You probably want to drop to single user mode to do this by running init 1.

---

### Post by slux on 2005-11-14
Why would you need to unmount your / partition in order to create one for /home? I don't see single-user being needed with home either,  the root user doesn't use home anyway..

---

### Post by veloct on 2005-11-14
[QUOTE=slux]Why would you need to unmount your / partition in order to create one for /home? I don't see single-user being needed with home either,  the root user doesn't use home anyway..[/QUOTE]

If I go through GParted then my linux partitions are locked so I can't resize the /  partition to add another partition to put /home in it.

---

### Post by veloct on 2005-11-14
I've completed the task and it's working nicely.  Thanks to all for the help.

---

