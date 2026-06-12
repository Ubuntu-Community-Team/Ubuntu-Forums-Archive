---
title: "Drive is read only"
date: 2006-09-12
forum: Desktop Environments
---

### Post by TokenBad on 2006-09-12
I had a crash where system locked up...I rebooted and now my slave drive is read only...I was told to umount it and run fsck...I did that...but when fsck got to the end of its scan and fix...it said drive left unchanged...even though it detected problems and I told it to fix it...and drive is still read only...anyone know how to fix this?

TokenBad

---

### Post by TokenBad on 2006-09-12
Please any help would be great....I have been trying to deal with this for over 24 hours...

TokenBad

---

### Post by TokenBad on 2006-09-12
No one knows how to fix this?  Please.....

TokenBad

---

### Post by WagnerVaz on 2006-09-12
Please, show us the output of:
cat /etc/fstab 
and
cat /etc/mtab

Thanks

---

### Post by TokenBad on 2006-09-12
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd1    /media/windows vfat  iocharset=utf8,umask=000,rw  0    0
/dev/hdd3 /media/iso ext3 defaults 0 0


here is mstab

/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-26-386/volatile tmpfs rw 0 0
/dev/hdd3 /media/iso ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/hdd1 /media/windows vfat rw,iocharset=utf8,umask=000 0 0

---

### Post by WagnerVaz on 2006-09-12
Sorry for can't help.
But I thought it is an error in fstab.
But all partitions seems to be set in RW.


Good look anyway

---

### Post by TokenBad on 2006-09-12
Anyone else help with this please?  I have been trying for like 2 days now...

TokenBad

---

### Post by TokenBad on 2006-09-12
Just to add to this...I can cut and paste files...I have used klibido to download files from newsgroups to that drive...but if I try to make dirs and stuff in command...it will not let me..says read only system


TokenBad

---

### Post by TokenBad on 2006-09-13
I give up....can't find anyone on here or IRC that knows how to fix this....I guess will just reinstall the OS and see if that fixes it...

TokenBad

---

