---
title: "can't boot, grub error 22, vista"
date: 2009-06-02
forum: General Help
---

### Post by jexdawg13 on 2009-06-02
i deleted my linux and linux swap partitions to make room for my full vista partition.

in the process i deleted grub and now when i boot i get this error:


GRUB Loading state1.5.

GRUB loading, please wait...
Error 22


i have read several other solutions, and here are my problems:

i don't have my ubuntu live cd. i installed ubuntu over a year ago, the cd is about 4 hours away, lost in my old house.

vista doesn't ship with recovery or install cd's - i have an HP recovery partition, but i can't get to it, because i have no GRUB to get me there. i can't fixmbr because i can't get to a command line.

i can't boot into anything. i'm typing this from my roommates computer and he is not happy with me. please help quickly!!! i need to fix this asap!!!

---

### Post by merlinus on 2009-06-02
This info may help:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by coffeecat on 2009-06-02
+1 for SuperGrubDisk. What isn't immediately obvious (unless you read a very long way down) in the link merlinus gave you, is that SuperGrubDisk can repair/restore the Windows bootloader.

If you can get SGD downloaded and burnt to CD (or USB stick), you can boot up from it and restore the Windows mbr in seconds. Scroll down about 2/5 into that page to the orange screenshot. The menu entry "WIN => MBR & !WIN!" is the one you want.

---

### Post by jexdawg13 on 2009-06-02
thanks for the replies but i still need help.

my roommate left so i don't have a computer anymore, but he did let me download the livecd of ubuntu 9.04, which is where i am posting this from.

so i did: sudo lilo -M  /dev/sda mbr (found on the forums)

now when i restart i get this error:

winload.exe

file is either missing or corrupt.


if i could get to a command prompt i could "fixboot" but i can't get to a prompt. i don't know what to do.

how can i fix windload.exe?

please help!!

---

### Post by coffeecat on 2009-06-03
You can't use the live CD to fix grub to be able to boot into Windows because by deleting your Ubuntu partition you deleted stage 2 of grub. Stage 1 of grub resides on the mbr. Stage 1 calls stage 1.5 which occupies a few hundred bytes just after the partition table, an otherwise unused part of the HD. Stage 1.5 calls stage 2 which **was** in the /boot/grub folder of your Ubuntu partition together with the menu.lst configuration file.

Look at this link:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

The ms-sys method may work for you. Unfortunately, the instruction to apt-get install the package from the live CD is bonkers because ms-sys is not in the repository. If, however, you follow the Freshmeat link, you eventually get to here:

[http://packages.debian.org/etch/i386/ms-sys/download](http://packages.debian.org/etch/i386/ms-sys/download)

... where you can download the ms-sys .deb in the live CD. Double-click on it to install and then follow the rest of the instructions in the first link.

Alternatively, now you've got a live CD, why not format what was the Ubuntu partition to something to use as temporary storage, and then download the SuperGrubDisk iso to that? Then burn the ISO to a CD (if you have a second optical drive) or USB stick and use SuperGrubDisk.

---

