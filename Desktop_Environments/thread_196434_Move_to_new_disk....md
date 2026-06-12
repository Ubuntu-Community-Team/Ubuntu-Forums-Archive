---
title: "Move to new disk..."
date: 2006-06-14
forum: Desktop Environments
---

### Post by Loffe_ on 2006-06-14
Hello!

When I first tried Ubuntu I installed it on an old 40GB hdd (hdc).
Now I want to move to my far better 200GB sata (sda).

GRUB is in mbr on hdc...

WinXP is installed on sda1 with the win loader on its mbr...

Whar is the best to do?

1. New install from cd on sda7. I have to customize my install with XGL again. ( Not a big problem)

2. Copy everything from hdc1 to sda7. What do I have to modify (GRUB etc.)?

//Loffe

---

### Post by frodon on 2006-06-14
I would just copy all to sda7 then all you have to do is to re-install GRUB (with the alternate cd), you can follow this guide to do that : [http://ubuntuforums.org/showthread.php?t=76652](http://ubuntuforums.org/showthread.php?t=76652)

---

### Post by Loffe_ on 2006-06-14
What is the best way to copy the disk?

I've read something about a command, **dd**... Is that correct? Someone wrote that the disk I copy to should have the same size as the one i copy from.

Or is nautilus ok to copy with? Or maybe cp?

I am copying to a smaller partition (10GB).

I also think of making a seperate partition for /home (but that is a later question)

---

### Post by frodon on 2006-06-14
The new partition must have enough space to put the image that's the only need but it can be bigger, no problem.

Don't use nautilus for that because you have to keep the symbolic links, so don't use nautilus and cp.

I advice you partitmage which have a GUI and is quite easy to use, to restore your partition on your new drive use a live cd with partimage on it like KNOPPIX (the ubuntu live CD don't have partimage on it) : 
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by Ramses de Norre on 2006-06-14
You certainly don't want to use cp or nautilus! All links will become broken.
I suggest you mount the partition you want to copy to as /media/new for example, make sure all data on the partition you're going to copy from fits on the partition your copying to and then run this command: ```
cd /
find . -depth -print0 | cpio --null --sparse -pvd /media/new/
```

---

