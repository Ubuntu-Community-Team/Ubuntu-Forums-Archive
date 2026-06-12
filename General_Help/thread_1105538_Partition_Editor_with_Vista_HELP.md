---
title: "Partition Editor with Vista HELP"
date: 2009-03-24
forum: General Help
---

### Post by utnr6 on 2009-03-24
my vista and ubuntu both work fine
I need help resizing them both
250 gb harddrive w/ following settings

unallocated  -  1mb
/dev/sda1    -  1.46gb (this is my toshiba system volume-i think grub is on it?)
/dev/sda2    -  223.35gb (vista - 28gb used)
unallocated  -  3.71mb  (no idea what this is)
/dev/sda3(extended - 8.07gb) - where i thought i installed ubuntu
  /dev/sda5  ext3  8.07gb - 4.53 used

it says my sda2 c: is my boot flag
and mountpoint / for my /sda5

other than that, i just want to fix this crap and any help on resizing this stuff properly would be phenomenal

---

### Post by zvacet on 2009-03-25
How do you want to resize it?Do you want to give Ubuntu more space or what?if you want to do that (or anything else) download [Gparted live CD.]("http://gparted.sourceforge.net/")Before you use it defragment your Vista partition few times just in case.After that boot Gparted and shrink your Vista partition.You will get unallocated space whitch will merge with your existing unallocated space.Unallocated space means that is free (unformated) space.After that resize your sda3 to the unallocated space.

---

