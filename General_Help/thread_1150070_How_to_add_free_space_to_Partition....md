---
title: "How to add free space to Partition..."
date: 2009-05-05
forum: General Help
---

### Post by Reyes1986 on 2009-05-05
Hey guys, after a failed attempt to reinstall my Ubuntu (had previous problems that couldn't get solved) I would like to know how to add free space to my c:\ so I can do a clean install. Please note, I have wiped out completely all of Ubuntu + Grub features on my PC. My Ubuntu copy is on a DVD, so I don't have to worry about installing a new one.

[IMG]http://img412.imageshack.us/img412/4870/freespace.jpg[/IMG]

*Please keep in mind, I cannot install Ubuntu regardless because it is not recgnoizing the 78.90 GB of free space, also I tried to maunually choose a partition during installation. So, through trial and error, my only assumption is that I have to add the free space to C: so I can start the intsallation just as the first time I've installed Ubuntu

---

### Post by raymondh on 2009-05-05
c: drive means you have a windows program.  In that case, you can use windows' disk manager to extend the current windows partition....that is after deleting and unallocating the ubuntu partition.  Remember to defrag afterwards.

Best of luck with the OS of your choice.

---

### Post by raymondh on 2009-05-05
also, don't forget to restore MBR .... at a windows command prompt, type

bootrec.exe/FixMbr

---

### Post by Reyes1986 on 2009-05-05
> **raymondhenson said:**
> c: drive means you have a windows program.  In that case, you can use windows' disk manager to extend the current windows partition....that is after deleting and unallocating the ubuntu partition.  Remember to defrag afterwards.

Best of luck with the OS of your choice.


How to I do this? The free space was the deleted Ubuntu partition...

---

### Post by ebanlague on 2009-05-05
When you right click the partition you want to add to, Does it say 'Extend Partition'?

---

### Post by Reyes1986 on 2009-05-05
No that option is not available.

---

### Post by arsenix on 2009-05-05
I would get yourself a copy of gparted ([http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)) which will get you a bootable CD that you can boot into to resize the partition.  You can do the same thing with the ubuntu installer CD, but gparted is a dedicated bootable distro for doing just what you want to do.

  This assumes you are wanting to enlarge the partition without eraseing the data.  If you want to erase everything... just erase everything from the Windows installer or your computers system restore disks.

James

---

### Post by Reyes1986 on 2009-05-05
> **arsenix said:**
> I would get yourself a copy of gparted ([http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)) which will get you a bootable CD that you can boot into to resize the partition.  You can do the same thing with the ubuntu installer CD, but gparted is a dedicated bootable distro for doing just what you want to do.

  This assumes you are wanting to enlarge the partition without eraseing the data.  If you want to erase everything... just erase everything from the Windows installer or your computers system restore disks.

James


I'm sorry I'm getting confused. I already have the boot CD for Ubuntu, it won't let me choose the partition I want to in installation mode, that's why I am trying to combine the free space with my c:\ drive. :P

edit: how can i do it without buring another .iso drive? What's the other manual way.

---

### Post by Reyes1986 on 2009-05-05
anyone?

---

### Post by Reyes1986 on 2009-05-05
Nevermind, I just realized how to fix it, I reformatted the drive, and then when I went to go and install I had to put the "/" command to manual install it.

Thanks guys!

---

