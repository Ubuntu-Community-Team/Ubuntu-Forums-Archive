---
title: "Serious Crash: runlevel does not seem to be initialized"
date: 2006-07-27
forum: Desktop Environments
---

### Post by cptnapalm on 2006-07-27
Well, after a hard lock (Xgl), I hit the power button and the system is now in a *very* bad way.  Insofar as I can tell, there is nothing wrong with the filesystem as xfs_check gives no errors and there is nothing in lost+found.  But the system is seriously b0rked.

There is no splash boot, just text boot.  But instead of the normal stuff, it lists rc.S's list.  Then, when it comes time for runlevel 2, it dies.  Then I get a root prompt with no hostname, asking for the password for maintainence.  the /etc/hostname file is fine despite me being root@(none).

I would prefer to recover my existing installation rather than re-install everything.  I do have plenty of space for doing a backup, assuming I can get my external drive to work.

Any ideas on where I should begin the repair process?

EDIT: I've found that I was mistaken, there is indeed some stuff in the lost+found directory.  I ran xfs_check and xfs_repair.  Ack.

---

