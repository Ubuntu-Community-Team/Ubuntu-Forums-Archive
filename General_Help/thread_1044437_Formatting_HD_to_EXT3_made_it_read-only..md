---
title: "Formatting HD to EXT3 made it read-only."
date: 2009-01-19
forum: General Help
---

### Post by AICollector on 2009-01-19
Hey all,

I recently had trouble with a malfunctioning install of Ubuntu, so I decided to backup and reinstall.


Sadly, after a load of problems getting my seemingly flaky external HD to even be recognized by Ubuntu before, now, with EXT3 installed, Ubuntu is declaring it read only, citing I do not have permission to do anything with it.

This is very annoying! Can someone tell me exactly how to unlock the external HD for general use?

---

### Post by logos34 on 2009-01-19
with it plugged in and mounted:

sudo chown -R username:username /media/wherever

sudo chmod -R 755 /media/wherever

---

### Post by AICollector on 2009-01-19
Ok, never dealt with the username:username.

username:aicollector is not recognized.

nor is 

aicollector:aicollector 


what am I doing wrong?

---

### Post by logos34 on 2009-01-19
> **AICollector said:**
> 
aicollector:aicollector 


yes


what's 

cat /etc/mtab

and

sudo fdisk -l

show?

You might try giving the drive a [label]("https://help.ubuntu.com/community/RenameUSBDrive") and letting it [automount ]("https://help.ubuntu.com/community/Mount/USB#Automounting")according to that, e.g.:

sudo tune2fs -L *label* /dev/sdb1

or 

sudo e2label /dev/sdb1 [I]label
[/I]

Perhaps then you will have full access to it

---

### Post by AICollector on 2009-01-20
My knowledge is limited with this, but here is the output of fdisk



Disk /dev/sdb: 360.0 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc5931f31

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       43777   351638721   83  Linux



and here is the output of cat  /etc/mtab

/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-9-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/dante/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=dante 0 0
/dev/sdb1 /media/disk ext3 rw,nosuid,nodev,uhelper=hal 0 0


(two HD's there as I couldnt tell which info belonged to what)

---

### Post by logos34 on 2009-01-20
hmm...fdisk isn't showing /dev/sda (?)

but the external drive sdb1 appears to be automounting ok.

Have you tried labeling it, as I suggested?  Worth a shot if chmod and chown didn't help

---

### Post by AICollector on 2009-01-21
Ahh yes, labeling it worked, thanks. :)

Just for future reference, why did EXT3 go read only?


(now, if I can only find how to put a 'resolved' tag here...)

---

### Post by logos34 on 2009-01-21
> **AICollector said:**
> Ahh yes, labeling it worked, thanks. :)

Glad it's ok now. 

> Just for future reference, why did EXT3 go read only?

All I know is, in linux, stuff happens.

> (now, if I can only find how to put a 'resolved' tag here...)

Yeah, everyone is asking what happened to the 'mark as solved' option (used to be in Thread Tools dropdown menu).  What happened to it?  Maybe it will come back soon--they've been working on the page for a while now (the servers as you probably know have been crashing a lot lately (or have been down for repairs)...

---

