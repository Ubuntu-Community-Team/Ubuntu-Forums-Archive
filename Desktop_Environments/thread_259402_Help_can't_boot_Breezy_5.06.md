---
title: "Help can't boot Breezy 5.06"
date: 2006-09-17
forum: Desktop Environments
---

### Post by AllanP on 2006-09-17
I actually already posted on Breezy forum as that is what I use but, figured maybe not too many using that forum

Shut down normally last evening. This morning I get the following:

"Halts on "checking root file system"
Contains a file system with errors, check forced
Inode 804792has illegal block(s)
UNEXPECTD INCONSISTENCY; RUN fsck MANUALLY (i.e. without -a or -p options)
fsck failed. Please repair manually ~ Reboot.
Please note that the root file system is currently mounted read-only. To remount it read-write:
# mount -n -o remount,rw /
CONTROL - D will exit from this shell and reboot
bash: lesspipe: command not found
bash: dircolors: command not found
root@ (none): ~#"

I then tried fsck with warning and now have no GRUB either.
Any way to fix this without re installing?

---

### Post by cmost on 2006-09-17
This may be a harbinger of a hard drive problem.  What were you doing prior to shutting down the system?  Were you running any disk utilities, performing any major updates, or have you installed a new piece of hardware?  If the answer to all of the above is no, then it's possible your hard drive is in the early stages of melt down.  I recommend a full backup to a reliable source ASAP.  You can always use the Dapper live-CD for further trouble shooting, though, I highly recommend Knoppix for such rescue attempts (even though it's KDE based.)  Good luck!

---

### Post by AllanP on 2006-09-17
Thanks but, no I wasn't doing anything serious. No updating. On boot up no disk warnings either. All was normal up to the "checking out file system".

---

### Post by AllanP on 2006-09-17
Also I have opened up Disk Manager and the partition that Ubuntu is on (hdb1) shows as unformatted. Yikes!!!

---

