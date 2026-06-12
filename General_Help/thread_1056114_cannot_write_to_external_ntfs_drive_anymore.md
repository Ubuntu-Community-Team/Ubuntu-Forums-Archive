---
title: "cannot write to external ntfs drive anymore"
date: 2009-01-31
forum: General Help
---

### Post by wanye on 2009-01-31
hi,

been running ubuntu happily for the last two years now with an external USB/NTFS drive, but all of a sudden (a couple of days ago) i started getting errors when trying to write a torrent file to it. ktorrent said it couldnt write file.

after some digging, i cant even create a new file to the drive, even as root.
> 
me@babydweezil:/media/700gb$ sudo touch FILE
[sudo] password for me: 
touch: cannot touch `FILE': Operation not supported

mount looks ok (i think)
> 
me@babydweezil:/media/700gb$ mount
/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/me/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=me)
**/dev/sdc1 on /media/700gb type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)**

and dmesg doesnt show anything obvious (to me)

> 
me@babydweezil:/media/700gb$ dmesg | grep sdc
[   10.418157] sd 5:0:0:0: [sdc] 1465149168 512-byte hardware sectors (750156 MB)
[   10.418882] sd 5:0:0:0: [sdc] Write Protect is off
[   10.418885] sd 5:0:0:0: [sdc] Mode Sense: 00 38 00 00
[   10.418888] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[   10.419506] sd 5:0:0:0: [sdc] 1465149168 512-byte hardware sectors (750156 MB)
[   10.420314] sd 5:0:0:0: [sdc] Write Protect is off
[   10.420316] sd 5:0:0:0: [sdc] Mode Sense: 00 38 00 00
[   10.420318] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[   10.420323]  sdc: sdc1
[   10.420989] sd 5:0:0:0: [sdc] Attached SCSI disk



also, its probably not related, but the last few weeks (i think since upgrading to 8.10) i can no longer reboot via the icon in the top right. i only get log out/switch user. i have to do it as root
> 
me@babydweezil:/media/700gb$ shutdown -r now
shutdown: Need to be root

any ideas?

cheers,

W.

---

