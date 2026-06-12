---
title: "Problems mounting NTFS read/write"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-06-02
I followed the guide found [HERE]("http://ubuntuforums.org/showthread.php?t=142481"). 

"sudo mount -a" gives no errors, but when I attempt to acces the drive I get this error:

Unable to mount the selected volume.
mount: according to mtab, /dev/hda1 is already mounted on /media/hda1
mount failed


I get the feeling I have made a stupid error somewhere, but I am not sure where.

My /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs-fuse       auto,gid=1002,umask=1001    0
 0
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

My /etc/mtab
```
/dev/hda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-23-386/volatile tmpfs rw 0 0
/dev/hda1 /media/hda1 fuse rw,nosuid,nodev,default_permissions,allow_other 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/hdc /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=ed 0 0

```

---

### Post by Lunar_Lamp on 2006-06-02
I forgot to say that if I travel to /media/hda1 I can view the folders in c:/, but they are all "unrecognised file types" - i.e. they are not folders and I cannot browse their contents.  They show a gnome foot icon instead of the folder icon.

Attempting to create a folder there tells me I do not have permission.

---

