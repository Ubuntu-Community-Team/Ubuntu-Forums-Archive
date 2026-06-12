---
title: "Help restoring fstab"
date: 2008-12-17
forum: General Help
---

### Post by michaelzorn on 2008-12-17
Hi All,
I am an ubuntu newbie and I need help. I did a **** up with my fstab file and now I am unable to restore it. I must say also that I didn't make a copy of the file, so now I am floating in the ****. I am in fact unable to browse a windows disk with my documents from linux. All the other disks are fine. The problem is also that I don't know which device is: sda,sdb,...
Is there a way to regenerate it?
Please help me.
Thanks in advance.

Bye.

---

### Post by any.linux12 on 2008-12-17
this is the default fstab
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4e75b16c-7f4f-4423-a121-bb4697e11699 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a63e1a93-d2a3-4d0b-88a5-c37a4b0defdd none            swap    sw              0       0


if you have more disks you have to had some extra lines, but first try this

---

