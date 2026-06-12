---
title: "Truble with MBR"
date: 2006-04-06
forum: Desktop Environments
---

### Post by joplass on 2006-04-06
I added Elive on my hard drive but because I could not get the wireless going, I removed it by deleting the partition with Elive using gparted.  Now the box can't boot into Ubuntu either.  What options do I have here to fix grub and/or MBR ](*,) .

---

### Post by stoeptegel on 2006-04-06
Looks to me like either a corrupted partition table in the MBR or a perhaps Elive(dunno what this is though) have taken over the grub where the MBR now points to a dead end.

Either you probably have to restore the MBR with grub in it, or, you have to restore grub(when installed on a partition) or the MBR.

Since i am not too experienced with this stuff i'll better stop talking now.

---

### Post by ssalman on 2006-04-06
[quote=joplass]I added Elive on my hard drive but because I could not get the wireless going, I removed it by deleting the partition with Elive using gparted.  Now the box can't boot into Ubuntu either.  What options do I have here to fix grub and/or MBR ](*,) .[/quote]

I think I understand what you have done... 

you installed another linux distro on your harddrive, which probably installed it's own Grub, and now that you have removed the partition, the new grub is gone. Hoping that you still have the old grub setup, and that your machine is booting to grub, you can do the following:

- press c in the grub menu
- type: "configfile (hd0,0)/boot/grub/menu.lst"

replacing the (hd0,0) with your ubuntu partition. this should boot the ubuntu partition.

now to fix grub check [this]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub") following wiki page.

Good luck :D

---

