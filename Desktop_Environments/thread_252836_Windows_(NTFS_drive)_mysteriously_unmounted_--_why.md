---
title: "Windows (NTFS drive) mysteriously unmounted -- why?"
date: 2006-09-07
forum: Desktop Environments
---

### Post by BoyBlunder on 2006-09-07
last night after i changed the wallpaper picture on my desktop, i noticed that my mounted windows drive was unmounted. i tried to remount it again, but all it said was that the device was busy. so i rebooted, and tried again, but got the same error.

i followed the directions here:

[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

---

### Post by electricshoes on 2006-09-07
What does yer fstab look like?

Do you get any errors if you do
```
sudo mount -a
```

---

### Post by BoyBlunder on 2006-09-07
no errors if i use that command.

this is fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda2    /media/windows    ntfs-fuse auto,gid=1001,umask=0002    0    0

```

the last line is what i added in myself.

---

### Post by Toxicity999 on 2006-09-07
You started using NTFS Fuse and forgot about it ;) It messes up the default mounting. Skim to /media/windows/ It's mounted there. That's just a desktop file anyway. the computer:/// setup is a tad... blah it would be nice if it handled mountings more inteligently but, for simplicities sake just create an icon to open up /media/windows in nautilus.

---

### Post by electricshoes on 2006-09-08
Make sure that fuse is in /etc/modules also.

---

### Post by wsun on 2006-09-09
I get this from sudo mount -a
Couldn't mount device '/dev/sda2': Operation not supported
Windows did not shut down properly.  Try to mount volume in windows, shut down and try again.

---

### Post by electricshoes on 2006-09-09
Boot into windows, then shutdown and boot back into Ubuntu.

That should fix it, if it does not.

Boot into windows, run a checkdisk then boot back into Ubuntu.

---

