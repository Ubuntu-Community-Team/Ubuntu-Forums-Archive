---
title: "Only root can write to NTFS problem"
date: 2006-07-29
forum: Desktop Environments
---

### Post by declaration on 2006-07-29
Hi,

I recently edited my fstab file to automount an NTFS partition at boot up.
I followed the following guide.
[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

However, now I can only write to the ntfs partition whilst root even though i think I followed all the steps properly.

my fstab-

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /mnt/c 	vfat  	iocharset=utf8,umask=000  0    0
/dev/hda5    	/mnt/e    	ntfs-fuse    auto,gid=1002,umask=0002    0  0

btw- the offending partition is hda5 (obviously : ))

---

### Post by fensirien on 2006-07-29
The reason you can't write is because of umask=0002

To give all access permissions to the group and allow other users read and execute permission: umask=0002

For all users to read and write the disk: umask=0000

Do you really need to set a group owner? Because it seems you are not a part of group 1002. If you don't want to change umask you could add yourself to group 1002

---

### Post by declaration on 2006-07-29
thanks fensirien- changed the umask to 0000 and i can write to the partition now.

Thanks again.

---

