---
title: "Help with a dead hard drive"
date: 2009-02-22
forum: General Help
---

### Post by Ometoch on 2009-02-22
Alas, my old 4 gb hard drive has finally given up the ghost.  I was only using it for a swap partition, and my question is... how to I go about replacing the hard drive without causing my poor machine to have a conniption?  Basically, I wanna remove the dead drive, and put in a new one, again using it for my swap.  I would prefer to do this without changing the drive order, etc...  any help is greatly appreciated.

---

### Post by khelben1979 on 2009-02-22
I think the easiest way is to backup all your important data that you have on your Linux system to another drive and then you make a new installation of Ubuntu where you decide to add your new harddrive as a swap drive.

*I'm sure someone else might have a better advice for you, but this is the thing I can think of.*

---

### Post by kahlil88 on 2009-02-22
Since you're only using it for swap, there should be no harm in removing it. You just won't have swap until you create a new swap partition, either on a new hard drive or the current one. If you can afford to lose 4 GB of space from your main partition, I suggest booting from the Ubuntu Live CD and resizing the main partition, then create a new swap partition.

---

