---
title: "Ubuntu 7.10 and Fedora Core 8 Dual Boot"
date: 2007-12-10
forum: Desktop Environments
---

### Post by Royal_Pwner on 2007-12-10
I have no idea how to do a dual boot. However, I would like to try fedora.
Question 1: Is fedora good/bad and is it worth losing my system76 custom drivers on a full switch?
Question 2: If it is worth it to dual boot?
Question 3: If it is worth it to dual boot, how would I go about doing that. Is it built into the fedora graphical installer? Or do I need a special program?

---

### Post by Royal_Pwner on 2007-12-11
Bump

---

### Post by Dark_Stang on 2007-12-11
There's no harm in trying it. To dual boot you'll just have to partition your drive for fedora. You can use gparted or a similar program to do that.

Now to my personal opinion... I tried fedora back when FC5 was the latest version. I hated it, it was nothing but a headache for me. I was able to have Ubuntu up and running in an hour tops, I fought Fedora for two weeks before I got all the bugs worked out. And then I ended up staying with Ubuntu.

Edit: Oh, and after you install fedora it will automatically search for other operating systems and see that Ubuntu is there. It uses (or at least used to use) grub by default, so the dual boot will be setup for you. But if you ever choose to get rid of fedora you'll have to point the grub that's on your MBR back to your Ubuntu partition.

---

### Post by Royal_Pwner on 2007-12-11
how do you choose which to boot at startup though? Is it hard?
is it possible to take off the partition if I want to?

---

### Post by Royal_Pwner on 2007-12-11
bump

---

### Post by Royal_Pwner on 2007-12-11
bump

---

### Post by Royal_Pwner on 2007-12-12
bump

Please, somebody hellp.

---

### Post by Dark_Stang on 2007-12-13
Sorry, I forgot to subscribe to this thread.

> how do you choose which to boot at startup though? Is it hard?
Grub will load up and you'll have 8 seconds (or whatever you set it to) to choose what you want to boot. After that it goes with default.
> is it possible to take off the partition if I want to?
To delete partitions? Sure. Just use gparted.

---

