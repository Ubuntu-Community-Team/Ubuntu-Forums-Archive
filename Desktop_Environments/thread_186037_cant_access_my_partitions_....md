---
title: "cant access my partitions ..."
date: 2006-06-01
forum: Desktop Environments
---

### Post by sherlock-holmes on 2006-06-01
I installed 6.06 just now and then addedd certain applications that I use...
used automatix to get some multimedia stuff...

things are fine except that i cannot access my other ext3 (/home) partitions and fat32 partitions.. here is my /etc/fstab file

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

I had seen the drives listed explicitely from places>computer but now after reboot, there are only 2 of them listed...viz, cdrom1 and file system.

any clue?

---

### Post by sherlock-holmes on 2006-06-01
[QUOTE=sherlock-holmes]I installed 6.06 just now and then addedd certain applications that I use...
used automatix to get some multimedia stuff...

things are fine except that i cannot access my other ext3 (/home) partitions and fat32 partitions.. here is my /etc/fstab file



I had seen the drives listed explicitely from places>computer but now after reboot, there are only 2 of them listed...viz, cdrom1 and file system.

any clue?[/QUOTE]


any help would be appreciated... !!!](*,)

---

### Post by sherlock-holmes on 2006-06-01
[QUOTE=sherlock-holmes]any help would be appreciated... !!!](*,)[/QUOTE]


anyway...it came back after rebooting 2 times... in 'places'...dont know what happend... strange...now it lists all the volumes..:confused:

---

