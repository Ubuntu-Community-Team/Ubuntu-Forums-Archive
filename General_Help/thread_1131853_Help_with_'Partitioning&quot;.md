---
title: "Help with 'Partitioning&quot;"
date: 2009-04-21
forum: General Help
---

### Post by DougieFresh4U on 2009-04-21
I would like for some one to explain the screen shot to me and which parts I can delete.
I have Windows 7 on sda1 and Ubuntu on sda6
I was trying to put fedora on it yesterday and some thing was addd and I have deleted 'sda7' but some thing looks like it's still there

---

### Post by unutbu on 2009-04-21
If a hard drive is a house, partitions are like rooms in that house. 
You have deleted sda7, and so that space has become unallocated.
sda6 and sda5 are on either side of that unallocated space.
sda6 and sda5, like rooms, have their own set of walls.
Unlike real houses and rooms, when you knock down the walls to a room (delete sda7), the rooms on either side (sda6 and sda5) still maintain their walls.

You can create a new partition in sda7's place, or you can use 
GParted to resize sda6 (Ubuntu).

---

### Post by bumanie on 2009-04-21
You have a logical partition (sda3) containing 3 other partitions, being , sda6, unallocated and swap. You can extend sda6 by grabbing the end of the box and dragging it to the end of the unallocated area. There is no harm leaving it as it is if you have enough storage space. If you want to repartition anything, use a live cd (either ubuntu live cd or gparted live cd). To alter a partition, one needs to have the partition unmounted. You can't alter sda6 if you are using it as it is then mounted, thus the need for a live cd.

---

### Post by coffeecat on 2009-04-21
> **DougieFresh4U said:**
> I have Windows 7 on sda1

There's something odd there. Gparted is telling you that sda1 is only 200MiB. I know Microsoft has managed to slim Windows 7 down, but.... :? Then there's the ~139GiB NTFS sda2 partition. I've no experience of Windows 7 - does it spread itself over two partitions? Or is sda2 your D: (or F, G, H: ) drive? In which case how can C: be only 200MiB?

Also - Gparted is trying to tell you something about sda1 and sda2. See those red exclamation marks. Unfortunately, I can't find what they mean in Gparted help, but they don't look reassuring to me.

---

