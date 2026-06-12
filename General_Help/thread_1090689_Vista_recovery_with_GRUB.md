---
title: "Vista recovery with GRUB?"
date: 2009-03-08
forum: General Help
---

### Post by williamwade on 2009-03-08
I have a laptop (Toshiba Equium L350D) which was originally running Windows Vista, I attempted to install Windows XP on via USB since the laptop couldn't boot the install disk (this has turned out to be a bad disk drive. This fell flat on its back and wouldn't even finish the install (although not before formating the Vista install in to oblivion). Although I was EXTREMELY careful to leave the Vista recovery intatct.

So I managed to get Ubuntu 8.10 (XFCE if that makes any difference) installed over USB. I was wondering, Could I use the GRUB louder to boot into the recovery drive?

---

### Post by meierfra. on 2009-03-14
> Could I use the GRUB louder to boot into the recovery drive? 

Maybe. Give this a try

Open "menu.lst" via

```
gksudo mousepad /boot/grub/menu.lst
```

Add the following to the  very end of the file:

title Vista Recovery
root (hdX,Y)
chainloader +1


Here X  is the hard drive and Y the partition. Grub starts counting at zero. So if the Vista Recovery partition is the third partition of the second hard drive,then "root (hdX,Y)" has to be "root (hd1,2)"

If the Vista Recovery is not in the boot drive (that is if X is not 0)  you also have to add "map lines"

title Vista Recovery
root (hdX,Y)
map (hd0) (hdX)
map (hdX) (hd0)
chainloader +1


Couple of examples:

If the Visa recovery is the  third partition on the first hard drive, use


title Vista Recovery
root (hd0,2)
chainloader +1


If the Visa recovery is the  third partition on the second hard drive, use


title Vista Recovery
root (hd1,2)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


If you need additional help, post the output of

```
sudo fdisk -lu
```

---

