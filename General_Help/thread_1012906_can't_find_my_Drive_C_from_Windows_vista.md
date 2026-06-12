---
title: "can't find my Drive C: from Windows vista"
date: 2008-12-16
forum: General Help
---

### Post by amir.giryes on 2008-12-16
Hi, i'm a new ubuntu user and i installed the 8.10 version of ubunto. i have windows Vista, and it work together (every time i restart my laptop i need to choose which program- vista or ubunuto start)

unfortunately ubuntu didnt mount my Drive C, and do it only to the Vista installation partition and now i can't see the all Music pituces etc..  that i have on my laptop

i know that i need to write a few commands in the shell but i dont know which one, please help me

Thanks :)

---

### Post by any.linux12 on 2008-12-16
show me your fstab

gedit /etc/fstab

---

### Post by taurus on 2008-12-16
Install ntfs-config and use it to mount your windows partition.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by amir.giryes on 2008-12-16
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

---

### Post by any.linux12 on 2008-12-16
the taurus solution should solve the problem

---

