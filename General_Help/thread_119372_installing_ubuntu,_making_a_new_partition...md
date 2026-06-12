---
title: "installing ubuntu, making a new partition.."
date: 2006-01-19
forum: General Help
---

### Post by morning on 2006-01-19
helo,
im gonna install ubuntu today on a 3 or 4 gb partition, 
th computer now have 2 partitions ( 20 gb each one) ..i wanna make a 3 one to install ubuntu.   ..so i create a 3 partition with 3 (or 4 gb) form one of the current partitions before i start to install ubuntu? or i can just start the ubuntu installation ? the instalation gives me the possibility to make a new  partition from one of the 2 that i already have? but leting me "divide" that partition  (cus its 20 gb and i just want 3 gb..) install ubuntu and not lose the files i have in that partition?  (confusion..?)

anymore things that i should know before starting tio install?
thanks..

---

### Post by az on 2006-01-19
[QUOTE=morning]or i can just start the ubuntu installation ? the instalation gives me the possibility to make a new  partition from one of the 2 that i already have? but leting me "divide" that partition  (cus its 20 gb and i just want 3 gb..) install ubuntu and not lose the files i have in that partition?  (confusion..?)
[/QUOTE]
Yes.  You can just boot the installer and it will spot a partition and offer to split it for you.  You do not need to partition beforehand.

You can also use the installer to partition your drives yourself, just pick "manual partitioning" in the partitioning part.

---

### Post by Sef on 2006-01-19
A)Read this turtorial on installing:  [http://users.bigpond.net.au/hermanzone/index.htm]("http://users.bigpond.net.au/hermanzone/index.htm")

B) There is a partitioner on the install disk.  


C) To keep your data safe, you'll need to create a /home partition.

     1) Need to create a swap partition. Generally double your RAM.
     2) Need to have a Ubuntu partition.
     3) Should have a / partition.

D)  Total Partition size to do about should be at least 10 GB.

---

### Post by goatflyer on 2006-01-19
Its easy to lose your data if you mess with your partition table.

Are your existing partitions ntfs or fat?

(to find out, boot up a Ubuntu Live CD, open a terminal window, and type

fdisk -l

(that's a "dash-el")

This will show you your partitions, their sizes, and types.

If they are windows partitions, first you have to scandisk them and defrag them (in Windows) before resizing them.

---

### Post by morning on 2006-01-19
hi, thanks,
they are ntfs :(  , heard there where something about them and linux , some kind of an incompatibility :???: ..
im reading now that link .. hope to understant and be sure of what im gonna do ..

---

### Post by goatflyer on 2006-01-19
I used a program called ntfsresize to shrink my win2000 ntfs partition, then manually created new partitions, then checked to make sure windows was still happy, then ran the ubuntu install

Take it in small steps, you'll be okay.

---

