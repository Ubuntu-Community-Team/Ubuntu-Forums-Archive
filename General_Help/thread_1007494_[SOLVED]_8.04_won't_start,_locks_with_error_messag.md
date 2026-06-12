---
title: "[SOLVED] 8.04 won't start, locks with error message. see attached image."
date: 2008-12-10
forum: General Help
---

### Post by brjoon1021 on 2008-12-10
Hi,

Sorry, there is no attached image, just the fstab below and my description. On the bootscreen, the job appears to be 

*Mounting local filesystems (and the jobs that it seems to be trying to accomplish are):
mount: mount point auto does not exist
mount: mount point <mount point> does not exist
mount: mount point auto does not exist

then it stops there forever with (fail) after these lines and just before *Activating swapfile.

I have to strike ctrl+alt+del to get it to complete startup. After I strike ctrl+alt+del I see a message that says:
init: rcs process ... something that suggests it has been canceled
init: rc6 process.... that it has been stopped or canceled as well.
 Please help. Even Recovery mode goes the same way. This happened after synaptic update a few days back.


Here is my fstab-

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# [COLOR=#ff0000]/dev/sdc1[/COLOR]
UUID=e1ce3fca-6f34-4653-9483-10a4d2c657e2 / jfs users,relatime,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda1
UUID=8d4f2d7e-d28c-43f5-9155-324a535cc19b none swap sw 0 0
# /dev/sdb1
UUID=fa2260c0-2012-4f10-b8e6-c78317c8496c none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,utf8,atime,noauto,rw,dev,exec,suid 0 0
[COLOR=#ff0000]/dev/sda2/UUE64 /mnt auto users,atime,noauto,rw,nodev,noexec,nosuid 0 0[/COLOR]
/dev/sda3/cowboy /mnt auto users,atime,noauto,rw,nodev,noexec,nosuid 0 0
[COLOR=#ff0000]/dev/sda2/UUE64 /mnt auto users,atime,noauto,rw,nodev,noexec,nosuid 0 0[/COLOR]
 /mnt auto users,noauto,atime,rw,nodev,noexec,nosuid 0 0
/dev/sda3 <mount\040point> auto nouser,atime,auto,rw,nodev,noexec,nosuid 0 0
/dev/sda7/160 <mount\040point> auto users,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/sdb2/MyDocs60 /mnt auto users,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/sda7/MyDocs160 /mnt auto users,atime,noauto,rw,nodev,noexec,nosuid 0 0
 /media auto users,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0
[COLOR=#ff0000]/dev/sda2/UUE64 /media auto users,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0[/COLOR]

I am confused by all of the lines that I have made red. The partition listed as sdc1 is Hardy 32 bit, the very next partition on the disk is Intrepid 64 but it shows up three times in the fstab and it is described as a different disk - sda, not sdc. Could that be the problem ?

Thanks,

B

---

