---
title: "Want Ubuntu with Vista"
date: 2007-09-04
forum: Dell  Ubuntu Support
---

### Post by VISTA_USER on 2007-09-04
Using the Vista OS, I would like to partition my hard drive so that I can use Ubuntu as well as Vista.

---

### Post by vinater on 2007-09-04
Actually pretty simple. use gparted (live cd) to move/create partitions install vista then install ubuntu. you're all set. grub should overwrite MBR and it's just that easy. if you already have one(vista/ubuntu) installed it's a little trickier but not much. it sounds like you have vista installed so just shrink the vista partition and create a partition for ubuntu and install.  Here is a link that might help you out.

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

---

### Post by nermalthecat on 2007-09-05
Or you can use vista to resize partitions, using the built-in tool it has.
This will tell you how to do it:
[http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/]("http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/")

---

### Post by Joeb454 on 2007-09-06
The link worked for me ( [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first) ).

When I was installing Ubuntu (using the guided install) it automatically recognised that Vista was installed and didn't overwrite the MBR, and it also created a GRUB entry for Vista.

This was using the Feisty CD btw, don't know if this would work with Edgy

---

### Post by Steve1961 on 2007-09-06
You can also use the Vista bootmanager to boot Ubuntu instead of Grub if you wish.  easiest way is to use [EasyBCD]("http://neosmart.net/dl.php?id=1")

---

