---
title: "Frequent filesystem errors"
date: 2010-03-10
forum: Desktop Environments
---

### Post by kunix on 2010-03-10
I'm running Ubuntu Hardy in a kiosk environment in a number of remote locations. 
The slightly modified Ubuntu LTS system is shutting itself down every evening and boots again in the morning. 

The problem is that one kiosk keeps getting file system errors like this one:

```
Setting kernel variables...done
Activating swap...done
Checking root file system... fsck 1.40.8 (13-Mar-2008)
/dev/sda1 contains a file system with errors, check forced
/dev/sda1: Inodes that were part of a corrupted orphan linked list found
/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
         (i.e., without -a or -p options)
fsck died with exit status 4
failed (code 4).

* An automatic file system chceck (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the
root filesystem mounted in read-only mode.


* The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D
to terminate the maintenance shell and restart the system.
Give root password for maintenance
(or type Control-D to continue):
```


Of course this issue cannot be solved via SSH, so it means someone has to locally run fsck, which isn't such a big deal to the point where I have to give someone the root password... Security bummer :(

I check the SMART status of hard drives every boot so I know that there are no defects on the drive itself.

Has anyone faced this kind of prob before? Please help me solve this.

---

### Post by heu on 2010-03-31
The situation is very much the same with me. It started about a month ago (probably after some "upgrade" it even started well before i switched to ext4, which just seems to have made it worse). SMART is not showing any disk errors and the other distros installed on this box (OpenSUSE, Sabayon and Solaris (along with XP)) never report filesystem errors, and I am using them just as frequently as I use kubuntu.

---

