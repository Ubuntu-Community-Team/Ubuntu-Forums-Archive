---
title: "Grub help again"
date: 2009-06-03
forum: General Help
---

### Post by elliotn on 2009-06-03
I have installed xp in the second partion. 
fdisk -l would be like hda1 linux and hda2 ntfs so ubuntu boot with hd0,0
Xp is suppose to boot with hd0,1
But when I set xp to that on menu.lst and boot I get NTDR error so when I check there it i set on hd1,0 even if I change in my menu.lst.

Is there a way to reinstall grub now erasing the current one?

---

### Post by lindsay7 on 2009-06-03
type "fdisk -l" the letter l not number 1, in hte terminal and lets take a look at it  first,

---

### Post by elliotn on 2009-06-03
Dude hd0,0 is linux
hd0,1 is xp
Now have set it that way but now when I go to xp it keep sayin 'starting up' foreva

---

### Post by =CelticRaven= on 2009-06-03
the most widely used (and easiest) installation method is to install windows first, and then Ubuntu, have a look here it may be of some help:

[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by jbruced on 2009-06-03
> **elliotn said:**
> Dude hd0,0 is linux
hd0,1 is xp
Now have set it that way but now when I go to xp it keep sayin 'starting up' foreva

Give supergrub a look, does pretty much any type of boot situation, excellent information on the site to explain it all.

---

### Post by trench.me on 2009-06-03
If you don't enjoy the above option you could always delete the partition, expand your Ubuntu partition and just run [VirtualBox]("https://help.ubuntu.com/community/VirtualBox").

---

### Post by Entropy_Sam on 2009-06-03
> **elliotn said:**
> Dude hd0,0 is linux
hd0,1 is xp
Now have set it that way but now when I go to xp it keep sayin 'starting up' foreva
 
not fully sure this will work (can you remap partitions?), but try adding the following two lines to your /boot/grub/menu.lst after calling rootnoverify(0,1) for XP:
 
```
map (hd0,1) (hd0,0)
map (hd0,0) (hd0,1)
```
 
Hopefully, you'll then have fooled XP into thinking it's on (hd0,0) and it should boot happily.

---

