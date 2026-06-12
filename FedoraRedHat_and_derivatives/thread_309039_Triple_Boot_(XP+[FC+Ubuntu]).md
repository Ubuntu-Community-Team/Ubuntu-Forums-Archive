---
title: "Triple Boot? (XP+[FC+Ubuntu])"
date: 2006-11-29
forum: Fedora/RedHat and derivatives
---

### Post by navneeth on 2006-11-29
Hi again, 
       I have XP on one hard disk(Master) and Ubuntu  along with some free space on the other(Slave). Can I install FC on the second disk, and if I can, any "precautions" that I should take such that the new OS does not disturb Ubuntu?

---

### Post by angryfirelord on 2006-11-29
Unfortunately, Fedora's Anaconda installer does not let you resize drives. However, there is a way.

Download a Linux distribution called GParted (20MB, like a free Partition Magic with Linux support). Boot it up and go to your second disk and resize it (it's real easy to use).

Next, boot into your Ubuntu desktop and copy the /boot/grub/menu.lst file. Fedora, for some reason can only boot a Windows OS. If you try to add Ubuntu during setup, it won't work.

Anyway, install Fedora to your disk. When it's all done, copy the Ubuntu and Windows section and add it to the /boot/gurb.menu.lst in Fedora. Save it and you should be ok!

---

### Post by navneeth on 2006-11-30
Thanks. I have the Gparted LiveCD, but would I need to resize if there is enough space is the second drive(i.e. the one with Ubuntu) - about 17G,  to let FC install by itself(similar to the option in Ubuntu that lets you install in the largest free space available)?

---

