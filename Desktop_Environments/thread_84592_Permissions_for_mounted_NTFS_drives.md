---
title: "Permissions for mounted NTFS drives"
date: 2005-10-31
forum: Desktop Environments
---

### Post by garethc on 2005-10-31
Hi all,

I'm completely new to linux, so this is probably pretty easily solved.
I run a dual boot system (WinXP), with 4 partitions - two being NTFS for use with WinXP. In Ubuntu 5.1, the two NTFS volumes are indeed mounted and are on the desktop. However, if I try to explore them I'm told I don't have the permissions necessary. I then logged on as root and that at least allowed me to explore the volumes, although I still can't change the permissions for the volumes, even as root, as the volumes are "read only"

All I want to do is have access to these volumes when I'm logged in normally - how do I do this?

Thanks a bunch!
Gareth

---

### Post by frenkel on 2005-10-31
There is no NTFS write support by default, so everything is read-only. You'd better use FAT32.

---

### Post by Hairy_Palms on 2005-10-31
you can read as normal user, by changing the fstab
open a terminal type 
sudo cp /etc/fstab /etc/fstab.backup
sudo gedit /etc/fstab
then look for the line that has ntfs in it and replace it with the line assuming it is hda1
/dev/hda1       /media/windows  ntfs    iocharset=utf8,umask=000   0       0

---

### Post by installer on 2005-10-31
Hrere is my fstab file with all my NTFS partitions mounted and readable when logged in as a normal user,


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdh3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0


/dev/hde5       /media/hde5  ntfs    nls=utf8,umask=0222 0       0

/dev/hdf5       /media/hdf5  ntfs    nls=utf8,umask=0222 0       0

/dev/hdg1       /media/hdg1  ntfs    nls=utf8,umask=0222 0       0

/dev/hdg5       /media/hdg5  ntfs    nls=utf8,umask=0222 0       0


/dev/hdh1       /media/hdh1  ntfs    nls=utf8,umask=0222 0       0


/dev/hdh2       /media/hdh2  ntfs    nls=utf8,umask=0222 0       0

/dev/hda5       /media/hda5  ntfs    nls=utf8,umask=0222 0       0

/dev/hdb5      /media/hdb5  ntfs    nls=utf8,umask=0222 0       0

---

### Post by garethc on 2005-10-31
Thanks guys,

I'm sure your tips will work, I'll confirm this when I have time to make the changes.

Cheers,
G

---

### Post by suRoot on 2005-10-31
[QUOTE=garethc]Thanks guys,

I'm sure your tips will work, I'll confirm this when I have time to make the changes.

Cheers,
G[/QUOTE]


**BE WARNED!!!!!**

Mounting & using NTFS volumes is NOT something you should be doing if you value your data.  NTFS read is pretty well supported, and has been for a while.  NTFS write is do-able, but is dangerous, and not something I'd be doing unless it were an emergency.  If you're going to be dual-booting, share data on a FAT32 drive like someone else said.

---

### Post by installer on 2005-11-01
[QUOTE=suRoot]**BE WARNED!!!!!**

Mounting & using NTFS volumes is NOT something you should be doing if you value your data.  NTFS read is pretty well supported, and has been for a while.  NTFS write is do-able, but is dangerous, and not something I'd be doing unless it were an emergency.  If you're going to be dual-booting, share data on a FAT32 drive like someone else said.[/QUOTE]

The advice regarding the fstab file will not give write access to NTFS partitions, and whilst suRoot is correct his advice can be safely ignored when reading only.

---

