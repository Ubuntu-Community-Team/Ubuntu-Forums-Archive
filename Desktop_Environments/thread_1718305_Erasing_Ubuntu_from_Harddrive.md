---
title: "Erasing Ubuntu from Harddrive"
date: 2011-03-31
forum: Desktop Environments
---

### Post by redgrave3 on 2011-03-31
I installed ubuntu on a laptop hardrive that i put on an external case, and im running it on a desktop and it only has ubuntu installed, but i now need that harddrive for storage but i cant seem to be able to format it through windows, and thats the only ubuntu system i have right now, please if someone can help i would be gratefull

---

### Post by coffeecat on 2011-03-31
Hi and welcome to the forum.

You don't say whether you are trying to use Windows' own Disk Management utility or a 3rd-party partitioner to reformat the drive. Windows Disk Management can get very confused by the presence of Linux partitions, particularly if they are logical ones. This might be the cause of your problem.

How exactly do you want to format the drive? What sort of filesystem? NTFS or FAT32 perhaps?

The simplest way would be to do this from the Ubuntu live CD. Either keep the drive in your desktop or put it in a USB enclosure. Boot up with the live Ubuntu CD and choose "try Ubuntu". When you get to the desktop, go to System > Administration > Gparted. You will be able to delete the partitions it has already and create new ones and specify the filesystem you need. If you need more help, post back.

One hint. If there is a swap partition on the drive you want to reformat, you may need to right-click on it (in Gparted) and choose "swapoff" before you can do anything.

---

### Post by ~Plue on 2011-03-31
~edited out
//coffeecat finished it up before i did

---

