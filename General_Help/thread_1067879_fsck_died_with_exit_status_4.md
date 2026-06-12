---
title: "fsck died with exit status 4"
date: 2009-02-12
forum: General Help
---

### Post by mvalenti on 2009-02-12
I looked thru the threads and found some answers but I am such a beginner I am having a hard time fixing this...

lost power and upon reboot got this...

fsck died with exit status 4
 * file system check failed
a log file is being saved in /var/log/fsck/checkfiles
please repair the system file manually
 *a maintenance shell will now be started
control-d will terminate this shell and resume system boot
bash: no job control in this shell
root@mark-desktop:~#


when i try running fsck nothing happens.. so i "ctrl-d" and get into ubuntu, try to open mail and it wants me to set up a new account....

help please...

---

### Post by mvalenti on 2009-02-12
contents of log file...

Log of fsck -C3 -R -A -a 
Thu Feb 12 10:22:19 2009

fsck 1.41.3 (12-Oct-2008)
/dev/sda3 contains a file system with errors, check forced.
/dev/sda3: Duplicate or bad block in use!
/dev/sda3: Multiply-claimed block(s) in inode 292830: 598110 598134 598135 598136 598137 598138 598139 598140 598141 598142 598143 598144
/dev/sda3: Multiply-claimed block(s) in inode 292985: 610542
/dev/sda3: Multiply-claimed block(s) in inode 293096: 610542
/dev/sda3: Multiply-claimed block(s) in inode 293104: 598110 598134 598135 598136 598137 598138 598139 598140 598141 598142 598143 598144
/dev/sda3: (There are 4 inodes containing multiply-claimed blocks.)

/dev/sda3: File /mark/.evolution/mail/config/folder-tree-expand-state.xml (inode #292830, mod time Wed Feb 11 16:23:18 2009) 
  has 12 multiply-claimed block(s), shared with 1 file(s):
/dev/sda3: 	/mark/.recently-used.xbel (inode #293104, mod time Wed Feb 11 16:35:00 2009)
/dev/sda3: 

/dev/sda3: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
fsck died with exit status 4

Thu Feb 12 10:22:30 2009

---

### Post by mc4100 on 2009-02-12
> **mvalenti said:**
> 
/dev/sda3: UNEXPECTED INCONSISTENCY; **RUN fsck MANUALLY.**
	(i.e., without -a or -p options)
fsck died with exit status 4

Thu Feb 12 10:22:30 2009
exit status 4 means, "File system errors left uncorrected".
Have you tried running it manually?
```
fsck /dev/sda3
```

Edit: Yes, you did try. What errors is it throwing up when you do that? Might need to force it, if necessary.

---

### Post by mvalenti on 2009-02-12
mark@mark-desktop:~$ fsck /dev/sda3
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda3 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? cancelled!

check aborted.
mark@mark-desktop:~$ 

Do I really want to continue?

---

### Post by jerome1232 on 2009-02-12
no, you want to unmount it then fsck it.

```
umount /dev/sda3
fsck /dev/sda3
```

---

### Post by mvalenti on 2009-02-12
mark@mark-desktop:/$ sudo umount /dev/sda3
umount: /home: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
mark@mark-desktop:/$ fsck /dev/sda3
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda3 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)?

---

### Post by jerome1232 on 2009-02-12
Okay it said the device was busy so it couldn't unmount it, you need to unmount the partition to run a fsck on it, I would either boot to recovery mode and unmount and fsck the partition there or Boot from a live cd then run fsck on /dev/sda3 from there.

To get recovery mode just select the recovery kernel in grub's boot list.

---

### Post by mvalenti on 2009-02-12
Thanks Jerome,

Seemed to fix a lot of files. and now system boots normally. However, when I start Evolution its acting like it has never been setup before... where did all my mail files go? Should i back them up before reconfiguring?

---

### Post by mvalenti on 2009-02-12
I just reconfigured it. thanks for all your help!

---

