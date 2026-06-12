---
title: "Setting up another Hard Disk"
date: 2006-07-28
forum: Desktop Environments
---

### Post by Zingomoos135 on 2006-07-28
K. sooo.... i have 2 hard disks in this computer. i have one 10 gb Maxtor drive (master) which has everything installed in it. I also have a 20 gb western digital (slave) drive in it.  

so here's my problem.

although i've figured out how to set up the WD drive, it's just another folder in my file system called Disk2 (/Disk2)

when i install stuff on here (esp using automatix which is now the love of my life) it takes up too much room.

how can i install stuff on this computer without totally having to do everything by hand (which would defeat the purpose of automatix in the first place....)

---

### Post by Zingomoos135 on 2006-07-28
sorry, let me clarify. automatix and synaptic alike both install apps on the Maxtor drive which is gettin' pretty full. the WD drive is basically empty. that's why i want to get some of it on the WD drive.

---

### Post by ajgreeny on 2006-07-28
I don't think it's possible to do what you want, I'm afraid.  Everything you install either using synaptic or automatix will be put in the appropriate folders, all of which, (or at least, the biggest majority of them) are in /usr, and subfolders of that eg /usr/bin and others.

In order to use the WD disk the easiest way would be to set up a separate home partition and use all of the WD Disk for that.  You should be able to do it by using gparted to format the disk as ext3, then setting a mount point and adding the appropriate line to the /etc/fstab file so it is mounted at bootup.  Copy all your current home folder to that disk and you should have solved part of your problem, at least.

I'm sure there must be more detailed instructions on this forum somewhere so do a search and see if that helps.

---

### Post by Zingomoos135 on 2006-07-28
it worked! thanks!

---

