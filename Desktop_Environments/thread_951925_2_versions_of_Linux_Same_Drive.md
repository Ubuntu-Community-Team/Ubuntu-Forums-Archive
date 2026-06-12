---
title: "2 versions of Linux Same Drive"
date: 2008-10-18
forum: Desktop Environments
---

### Post by Mr_Marc on 2008-10-18
Simple question but I need an answer so please bear with me.

First hardrive is a SATA with Win Vista.

Second HDD EIDE with Ubuntu 8.10 Hardy Heron No problems 

My question is can I install Mandriva on a different partition on the second HDD and how would I do this. By using gparted??

Thanks in advance Marc "Noob"

---

### Post by benerivo on 2008-10-18
I would use gparted. Just shrink ubuntu to make some free space, and then you'll be fine to just boot the Mandriva cd. You would have to consider that Mandriva will take over the boot/grub screen but that should be no problem unless you delete the Mandriva partition later on.

---

### Post by brianfreytag on 2008-10-18
I'm going to voice a fairly unheard opinion in the Ubuntu community, and I'll probably get some flak for it.

You're saying you have 2 hard drives... one with Windows Vista.

I would suggest you SKIP using gparted and use the built-in drive partitioner in Windows Vista.  It is quicker, more efficient, and less likely to screw with your stuff.

I have done several experiments with the two, testing speeds and likelihood of breaking your system.  In 3 out of 10 partitions I did with gparted, my boot sector was destroyed.  In 4 out of 10, several parts of my system were missing.  It took from 2 to 5 hours to take a partition from 20gb to 50gb, going from freshly defragged system to a highly fragged system.  I noticed also that the more fragged the system, the more likely you are to lose stuff.

In vista disk management, I experienced 0 lost boot sectors, and only 1 instance of losing system parts. And even on a highly fragged drive the maximum it took was 20 minutes.  On a freshly defragged system, it took 2 minutes.

Good luck, and happy partitioning :)

---

