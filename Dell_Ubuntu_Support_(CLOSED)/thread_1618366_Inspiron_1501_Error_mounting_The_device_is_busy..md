---
title: "Inspiron 1501 Error mounting: The device is busy."
date: 2010-11-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by djsven on 2010-11-10
Background:
A few days ago, Dell Inspiron 1501 running Ubuntu 10.04 stopped booting with the error "mounting /dev on /root/dev/ failed".
Tried booting with 10.04 LiveCD with no luck. Downloaded 10.10, successfully boots live session. Now trying to access files for backup before clean install, but the hard drive will not mount.

Various errors. In disk utility, clicking "Mount Volume" or "Check Filesystem" gives 

An error occurred while performing an operation on "77 GB Filesystem" (Partition 1 of ATA ST980811AS): The device is busy.

Opening "77GB Filesystem" under "Places" gives

Unable to mount 77GB Filesystem - A job is pending on /dev/sdb1

Any thoughts? Is the drive toast?

---

### Post by djsven on 2010-11-12
bump. any ideas whatsoever?

---

### Post by gibbylinks on 2010-11-12
Sorry but if it won't mount from the live CD and your getting errors, looks toasted.

Have you tried looking at it with gparted ?

---

### Post by djsven on 2010-11-17
It shows up in gparted. Do you suggest I make some small change in the partition table or something?

---

### Post by gibbylinks on 2010-11-17
Wonder if the drive has got corrupted. Try searching the forums for **fsck** which I think you will need to run from live CD.

I'm not a good enough linux guru to advise you further as my knowledge is virtually nil on repairing file systems.

Maybe some kind soul will read this thread and be able to advise you further

---

### Post by gfwright80 on 2011-09-30
I am having a very similar problem.  I am using UBUNTU 10.04, and have it on a separate partition of my HD.  There is an older version of UBUNTU on the other half of the disk, and it is still working perfectly.    The computer was freezing when i was attempting to shut it down, so I did some hard power-downs.  After about a day, when I attempted to hard-reboot my computer, it put me in something called a "busybox".  All attempts to access my drive via the live CD, and via the older version of UBUNTU, tell me that the device is busy, and that there is a pending job on that drive.  I have tried several suggestions that I have found searching online, and nothing seems to work.  Did you ever get the problem fixed?  If you did, please let me know how.  I don't want to scrap the partition because I have a whole bunch of pictures that I put on it the day before it crashed, and I haven't backed them up yet.  
Thanks

---

