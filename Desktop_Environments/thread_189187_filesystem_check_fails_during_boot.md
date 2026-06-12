---
title: "filesystem check fails during boot"
date: 2006-06-04
forum: Desktop Environments
---

### Post by lofty00 on 2006-06-04
Hello,

I've just installed dapper drake, and I have a persistent problem where it fails the filesystem check during bootup, and I get dropped into a root shell. Ignoring the problem lets me boot up, and if I check the filesystem from the live CD it comes up clean. For some reason it seems to be checking the root filesystem (/dev/hda5) even though that's already been checked earlier on, and should be mounted at this stage. The other filesystems check clean. I looked at the script (/etc/rcS.d/S30checkfs.sh), and the fsck command includes the '-R' flag which should tell it not to check the root filesystem, so I don't understand why this is happening. As far as I can guess, the problem is that:
a) for some reason fsck is not picking up the fact that /dev/hda5 is mounted as root.
b) because of this, it's checking the filesystem while still mouonted, and finding an error because of that.

If anyone has any clue why this is happening or how to fix it, it would be good to know.

Thanks,

andy.

---

### Post by Chickenmonger on 2006-06-04
You might check your /etc/fstab. I recall that the last option on each partition line determines when and if the filesystems are checked on boot.

---

### Post by lofty00 on 2006-06-05
[QUOTE=Chickenmonger]You might check your /etc/fstab. I recall that the last option on each partition line determines when and if the filesystems are checked on boot.[/QUOTE]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /local          ext3    defaults        0       2
/dev/hda1       /media/hda1     ext3    defaults        0       2
/dev/hda4       /media/hda4     ext3    defaults        0       2
/dev/hda7       /var            ext3    defaults        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/local/home     /home           auto    defaults,bind   0       0
/local/usr-local /usr/local     auto    defaults,bind   0       0

I think this is correct.

---

