---
title: "Formatting some extra space"
date: 2006-01-21
forum: Desktop Environments
---

### Post by asq on 2006-01-21
Hey guys, im a fairly intermediate linux user now, but I have a sligth prob ;)

When I setup my ubuntu box I installed in into the wrong harddrive because the ubuntu must have read the partition table wrong.. (at least i consider that i couldnt make that mistake!)

Basically I have my ext3 and my swap, but i also have around 70gb of ntfs crap hanging around that i really dont need. The majority of this stuff is free. How do I go about customizing this partition into a new, or preferably, my existing ext3 FS?

Im guessing fdisk but i dont wanna screw around without consulting the experts 1st ^_^

---

### Post by cayamara on 2006-01-21
Try gparted. It lets you resize partitions and as far as I understand you, thats what you're trying to do. Plus, it comes with a nice frontend.
```
$ sudo apt-get install gparted
```
Be careful though, when you resize or move partitions, you can always loose data.

---

### Post by asq on 2006-01-21
Thanks.. doing a search of synaptic I had spotted this before but still wasnt sure. I might hold fire on this install and re-install my first love KDE. How I love her ^_^ :KS

---

