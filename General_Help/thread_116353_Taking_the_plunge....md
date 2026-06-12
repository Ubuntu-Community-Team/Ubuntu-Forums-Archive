---
title: "Taking the plunge..."
date: 2006-01-12
forum: General Help
---

### Post by richcoleuk on 2006-01-12
Hello all,

After trying the Ubuntu Live CD I was so impressed that I would like to try and dual boot on my machine.  Firstly a bit about my computer.  I currently have windows XP installed on my C: drive.  I also have a much larger D: drive that i use to store photos music etc.  Now what i want to know is how I go about dual booting.  More importantly would it be possible to have windows on the c: drive and then ubuntu on the d: drive and still be able to boot from both with out loosing my photos on the d: drive?

Thanks in advanced

Richard

---

### Post by icarius on 2006-01-12
It is quite possible to boot ubuntu from one drive and xp from another. However, if you have a lot of files on your d drive then it makes sense to repartition your c drive to boot both xp and ubuntu from in so you dont have to backup all of your files on your d drive. I personally only know how to partition using partition magic, which partitions without destroyind data. If you have this, then reduce the size of your c partition in partition magic, then insert a disk with the 5.10 ubuntu iso image written on it, install to the unallocated space, ubuntu will create a swap and ext 3 partition (follow the onscreen directions) and then, after the install is complete, it will ask you if you want to install grub, say yes, and walla, you have both. I have personally reduced the size of my windows and ubuntu partitions to just the size that I need to run the os, and then made another partition, say z: to store all data, incase the os blows up, then I will not loose any data, I will only have to reinstall my os. Good luck.

---

### Post by aysiu on 2006-01-12
The fifth link of my signature explains all... and with screenshots. It's the best dual boot guide for Ubuntu I know of.

---

