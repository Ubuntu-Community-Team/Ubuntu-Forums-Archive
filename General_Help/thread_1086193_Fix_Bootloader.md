---
title: "Fix Bootloader"
date: 2009-03-03
forum: General Help
---

### Post by solarwind on 2009-03-03
I recently repartitioned my hard drive and removed Linux. Now GRUB wont boot because I removed it's boot partition as well. (Don't worry I'm going to reinstall Linux later :P )

Anyway, how do I fix the bootloader to boot into windows xp again? I don't have a windows install CD so I can't do fixboot or whatever. I also don't want to reinstall grub/lilo.

---

### Post by oldos2er on 2009-03-03
You may be able to install grub4dos: [http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial)

 Or use Super Grub Disk to restore Windows' boot loader: [http://stmaarten.globat.com/~supergrubdisk.org/](http://stmaarten.globat.com/~supergrubdisk.org/)

---

### Post by hexanol on 2009-03-03
Normally, except if you erased/removed the bootloader from your windows partition, you should be able to boot it from a grub floopy for example, by doing something like

> root (hdX,Y)
makeactive
chainloader +1
boot

I think it's also possible to install grub so it all fit in the MBR (more precisely, in the first 63 sectors of your hard drive) so when you computer boot, you get the grub command line and you can boot operating system from there. No need for a separate partition.

Edit: I just tried it and it works on a USB stick. It takes unfortunately too much space to be installed in the 63 first sectors of a hard drive, so unless you have more more than 250 free sectors before your first partition, don't do it. Just follow the procedure [here]("http://www.gnu.org/software/grub/manual/grub.html#Creating-a-GRUB-boot-floppy") but instead of using /dev/fd0, use another device like a USB flash drive (warning, you will lost all the stuff on your stick)

---

