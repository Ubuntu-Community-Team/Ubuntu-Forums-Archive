---
title: "Swap space not mounting at startup"
date: 2006-06-19
forum: Desktop Environments
---

### Post by nousplacidus on 2006-06-19
I used parted and moved somethings around BUT the swap is still the same hda5 it was before. 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /media/hdb1     ext3     defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       


Disk /dev/hda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       14342   115202083+  83  Linux
/dev/hda2           14354       14596     1951897+   5  Extended
/dev/hda5           14354       14596     1951866   82  Linux swap / Solaris



How can I make sure that its not mounted (I'm going by the output of my gdesklet :) which worked fine before) and how do I get it working again. 

Thanks :-)

---

### Post by linuchsan on 2006-06-19
What does swapon -s say

---

### Post by nousplacidus on 2006-06-19
nothing, its blank out put, not even a new line. 

nousplacidus@resnet25-079:~$ swapon -s
nousplacidus@resnet25-079:~$

---

### Post by nousplacidus on 2006-06-19
Im a huge tool, I just needed to format it. Sorry for being a retard.

---

### Post by linuchsan on 2006-06-19
mkswap /dev/XXXX
swapon /dev/XXXX
edit your fstab

---

