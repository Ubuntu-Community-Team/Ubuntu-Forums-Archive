---
title: "Corrupted files system"
date: 2006-06-15
forum: Desktop Environments
---

### Post by rcmiv on 2006-06-15
I occasionally (once every two weeks) get the following on boot:

```
...
*Checking root file system...
/ contains a file system with errors, check forced.
/:
Inodes that were part of a corrupted orphan linked list found.

/:UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
     (i.e., without -a or -p options)
                                                                                                                    [fail]
*fsck failed.  Please repair manually and reboot.  Please note
*that the root file system is currently mounted read-only.  To
*remount it read-write:

* # mount -n -o remount,rw /

*CONTROL -D will exit from this shell and REBOOT the system.
```
For which the solution seems to be:

boot up with a ubuntu live cd
open a terminal
```
sudo -i
fsck /dev/hdc*
```
replace * with the appropiate number for partition; /dev/hdc2 for my system
reboot

thanks to simbart for that...it works every time. But...

My questions are: why does 6.06 consistently corrupt the root filesystem causing this condition in the first place?  Has anyone else experienced this, and is there a permanent solution?

-rcmiv

---

