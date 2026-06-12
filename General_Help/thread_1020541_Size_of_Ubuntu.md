---
title: "Size of Ubuntu"
date: 2008-12-24
forum: General Help
---

### Post by cholmes on 2008-12-24
I just installed ubuntu on a partition that was about 35GB. The drive now appears to be almost full, about 5GB left. I thought ubuntu was much smaller than that so what happened? Is there allot more on there than needs to be? It says it is 4GB so I should have 30GB left over after the install right?

---

### Post by redilyn on 2008-12-24
Yep you are correct, Ubuntu should not have used that much space.

Try checking with the Disk Usage Analyzer to see whats taking all the space. 

You can find it under Applications -> Accessories -> Disk Usage Analyzer

Open Disk Usage Analyzer and click the button "Scan Filesystem"

Have a look threw the tree to see whats using the space.

---

### Post by cholmes on 2008-12-24
If I go to the disk in windows there is a file folder named "disks" and the size of it is 27.9GB any idea what that is about?

---

### Post by redilyn on 2008-12-24
Do you mean the folder is /media/disk??

If so that is your windows file system and the space it shows as used is the space windows is using.

Maybe check to make sure your ubuntu disk is actually full.

Check this:

System -> Administration -> System Monitor

Click on the File system tab.

Does it show any device as almost full?? If so which directory?

---

### Post by crazyfuturamanoob on 2008-12-24
Well, ubuntu can fit into a 700Mb CD-ROM, but some files may be compressed, and also the files/programs you have installed eat disk space.

---

