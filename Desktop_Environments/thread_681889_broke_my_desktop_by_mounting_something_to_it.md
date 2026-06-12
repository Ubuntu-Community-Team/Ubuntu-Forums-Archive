---
title: "broke my desktop by mounting something to it"
date: 2008-01-29
forum: Desktop Environments
---

### Post by sternkanz on 2008-01-29
Hi, I've managed to somehow mount a portable usb hdd of mine as /home/<username>/Desktop

and now my desktop is broke.

I've read some other posts and I see what I've done wrong, however, how do I fix it? I looked at /etc/fstab and I can't find a mount related to my HDD. When I plug my hdd back in it mounts to:

/media/<hdd name>

A note to the desktop. I can still right-click on it and change the background, however if I try and create a folder it says: 

          Error creating new folder.
          Error "I/O error" creating new folder.

Any help muchly appreciated!

Stern

---

### Post by kd2323 on 2008-01-29
Have you tried to delete the mount point in fstab and the re-write it? I unfortunatly am not using ubuntu right now so I can be of much help. Give me a few hours and I should be able to help

---

### Post by prshah on 2008-01-29
First, find the related uuid in /etc/fstab and comment out the line. Then find the relevant device in /etc/mtab and comment it out. Then, in a terminal (or just press alt+f2), type gksu users-admin and "modify" your username. On the second or third tab, you can set your home directory manually.

HTH
Cheers,
PRShah

---

### Post by sternkanz on 2008-01-29
Thanks for the replies! However:

The drive does not appear in fstab, does this mean I can continue directly to the mtab step?

In /etc/mtab there is a line:

/dev/sdb1 /home/<username>/Desktop fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0

I assume that is the line I need to comment out, right?

Finally... I have quite a lot of stuff in my home directory that is important, so what does that third step do? Will I lose my home directory and create a new user? Or will all the stuff in my home directory be copied to a new home directory (with the new name) and a new, fresh desktop be created?

Thanks,

Stern

---

### Post by prshah on 2008-01-29
Maybe you should post your fstab and mtab files here. as to wether it will wipe out your old home directory and create a new one... dont really know, but where actually is your /home mounted? Not /home/<user>, but /home ? 

Anyway your fstab and mtab will give us a clue...

Cheers,
PRShah

---

### Post by sternkanz on 2008-01-29
/etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3832d2f0-aeb0-4874-871b-49292e9fac73 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=28e5d212-6d63-44df-a3eb-149860fbd957 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

/etc/mtab

/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
/dev/sdb1 /home/<username>/Desktop fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0

Hope this helps, thanks for taking the time :)

---

### Post by RavanH on 2008-01-29
I would try commenting out (put a # in front of if) that last line in your mtab file: > **sternkanz said:**
> 
/dev/sdb1 /home/<username>/Desktop fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0

Then reboot and see if your Desktop folder is normal again....

---

### Post by sternkanz on 2008-01-29
Thanks very much guys that seems to have done it! (the comment in front of the last mtab line that is).

I have my desktop back now :)

Thanks! :KS

Stern

---

