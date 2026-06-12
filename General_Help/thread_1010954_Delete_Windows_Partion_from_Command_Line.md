---
title: "Delete Windows Partion from Command Line"
date: 2008-12-14
forum: General Help
---

### Post by BuddeJosh on 2008-12-14
I was wondering, is there a way to find out the Partion Windows is on and delete that from the Ubuntu Command Line; and how would I be able to give Ubuntu the whole machine from the Command Line, then switch to Graphical mode. Yes, I used Wubi to install Ubuntu.

---

### Post by logos34 on 2008-12-14
can't do it--wubi installs linux INSIDE windows on a loop-mounted fs.  

You have to first move ubuntu to a separate partition with LVPM:

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

---

### Post by logos34 on 2008-12-14
[delete--duplicate]

---

### Post by brandon88tube on 2008-12-14
Yes, [color=red]DO NOT DELETE THE WINDOWS PARTITION IF YOU ARE USING WUBI![/color] This will also delete your Ubuntu install as it is installed on your Windows partition.

---

### Post by logos34 on 2008-12-14
once you've got ubuntu on separate partition, use gparted to delete windows.  Or if you really want to use the cli, then fdisk:

[http://tldp.org/HOWTO/html_single/Partition/#fdisk](http://tldp.org/HOWTO/html_single/Partition/#fdisk)

---

