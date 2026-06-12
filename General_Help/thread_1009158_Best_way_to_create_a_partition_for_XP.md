---
title: "Best way to create a partition for XP?"
date: 2008-12-12
forum: General Help
---

### Post by Joeyc on 2008-12-12
I did a clean install of Ubuntu 8.10, but now realize I would still like to have access to XP on occassion. How can I go about installing XP at this stage? Am I better off installing XP first and the ubuntu after?

---

### Post by poydence on 2008-12-12
Right now I am duel booting with Ubuntu and Vista. I partitioned my disk before I installed either.  If you're not too far along with Ubuntu that still may be the easiest way with XP. However, I've heard of something called 'Partition Magic' which allows you to partition your disk after you have already installed an OS. Good luck!

---

### Post by sPiN1 on 2008-12-12
the way i partitioned my hd is i put in my ubuntu live disc, went to terminal and typed sudo gparted and split my HD the way i wanted it and installed xp to the other partition

---

### Post by tuxxy on 2008-12-12
Its recommended to install WIndows first then Ubuntu, however if you still want to install it this way run the Ubuntu Live CD and open the app gparted.

Here you could shrink the current partition size of the current Ubuntu installation.  TYhen create your new Windows partition with the free space you created and of course NTFS.

By installating XP second you may have to reinstall GRUB which shouldnt take long if you do.

---

### Post by perspectoff on 2008-12-12
It is best to let Windows be installed first.

See Ubuntuguide at [http://ubuntuguide.org](http://ubuntuguide.org)

or

Kubuntuguide at [http://kubuntuguide.org](http://kubuntuguide.org)

---

### Post by Metallion on 2008-12-12
Partition magic is a windows app and quite expensive to boot. I suggest using gparted live CD to do the partitioning, then install win xp and afterwards use super grub disk to install grub.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

If you don't mind losing your ubuntu it might be easier to indeed install win xp first and then ubuntu. The ubuntu installer comes with a strong partitioner and grub will be installed automatically for you.

---

### Post by Joeyc on 2008-12-12
Lots of great info. Thank you everyone. Being a novice with Linux, I'd like to make this as easy as possible for me. It seems that installing XP first, then Ubuntu is probably the right thing for me to do. I know there are work arounds, but I don't want complicate things quite yet. I am actually a OS X user, but after a few days in Ubuntu, I am hooked. I only want XP for a few things - network printers mainly (Lexmark).

I will be sure to look at the guide linked above. 

The Ubuntu community has impressed me quite a bit so far and it seems I can accomplished everything (or very close to everything) that I did in OS X, in Ubuntu. Still some bugs to work around, but I expected that.

Thanks again,

Joe

---

