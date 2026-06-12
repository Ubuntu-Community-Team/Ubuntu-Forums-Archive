---
title: "hard drive size"
date: 2006-05-06
forum: Desktop Environments
---

### Post by azray on 2006-05-06
I installed ubuntu on a second hard drive that formerly housed Suse linux. The hard drive capacity is 140 GB. If I look at the device it says the current size is 12.67 GB and that there is 8.6 GB free. I assumed that the drive was reformatted during the ubuntu installation, perhaps not. How do I get the full use of the drive?

---

### Post by matthewstory on 2006-05-06
try opening up gparted and taking a look at the disk.  You should also be able to reformat the disk from here.  Its possible that you just installed ubuntu on a portion of the drive and so the rest is unusable as of now.

I believe that gparted is in the administration tab.  or you can open it from a terminal window by typing in:

gparted

---

### Post by azray on 2006-05-06
bash: gparted: command not found

---

### Post by aysiu on 2006-05-06
You need to install it before you can use it: ```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
``` If you want to resize partitions, they must be unmounted, though (not in use), so you probably want to do this while using a live CD.

---

### Post by azray on 2006-05-06
thanks to all....all better;)

---

