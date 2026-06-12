---
title: "can't mount /dev/hdb ??"
date: 2005-03-13
forum: Desktop Environments
---

### Post by bazder on 2005-03-13
I can't mount /dev/hdb because it says ....

"/dev/hdb already mounted" or the mountpoint is "busy"

========================

but /dev/hdb isn't mounted according to fstab (see below)

any idea what's going on with this?  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0

---

### Post by sas on 2005-03-13
wild stab in the dark but do you need to mount /dev/hdb1 or something?

---

### Post by bazder on 2005-03-13
[QUOTE=sas]wild stab in the dark but do you need to mount /dev/hdb1 or something?[/QUOTE]


woohoo!!!  WE HAVE A WINNER  :!:  :!: 

I should have thought of that...  :???: 

thanks mate!

---

### Post by alastair on 2005-03-14
The fstab file does not tell you what is mounted - but what TO mount at boot.

To see what is mounted, type : mount

Or look at the contents of the file : /etc/mtab

---

