---
title: "Mounting Question"
date: 2005-07-22
forum: Desktop Environments
---

### Post by Phixion on 2005-07-22
Hi, I've searched and searched for this answer, I've read many pages all with different answers.

Basically I would like to know what command I need in my /etc/fstab to correctly mount  my 2 EXT3 Hard Drives.

At the moment I'm using

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hde1       /media/d        ext3    defaults,errors=remount-ro
/dev/hdc1       /media/e        ext3    defaults,errors=remount-ro

```

As I've seen so many variations I would like some advice, I also want the Drives to appear in my 'Computer' window.

Many thanks.

---

### Post by haaglin on 2005-07-22
try adding 0       1 at the end

> 
/dev/hde1       /media/d        ext3    defaults,errors=remount-ro 0       1
/dev/hdc1       /media/e        ext3    defaults,errors=remount-ro 0       1


---

### Post by haaglin on 2005-07-22
they should appear in Computer window if you mount them in media like you have done.

---

### Post by Phixion on 2005-07-22
Thanks guys :) I sorted it

---

### Post by GTvulse on 2005-07-22
[QUOTE=Phixion]
As I've seen so many variations I would like some advice, I also want the Drives to appear in my 'Computer' window.

Many thanks.[/QUOTE]

Add "users" to the option list in your fstab file. Gnome's volume manager will add the directories to the Computer window if they can be mounted and unmonted by normal users, with "FileSystem" being an exception.

---

