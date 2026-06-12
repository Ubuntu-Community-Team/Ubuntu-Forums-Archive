---
title: "Seperate /home partition"
date: 2006-09-19
forum: Desktop Environments
---

### Post by alecjw on 2006-09-19
I've already installed Ubuntu. If I want a seperate /home partition, how do i do this? Do I need to reinstall? I know how to partition, just need to beable to tell Ubuntu that /home=hda2

---

### Post by tagra123 on 2006-09-19
> **alecjw said:**
> I've already installed Ubuntu. If I want a seperate /home partition, how do i do this? Do I need to reinstall? I know how to partition, just need to beable to tell Ubuntu that /home=hda2

Here's a pretty good how-to:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by aysiu on 2006-09-19
Follow these instructions:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by alecjw on 2006-09-19
Thanks for your quick replies, guys!
Can it be on a logical drive?

---

### Post by chavo on 2006-09-19
Yep, you can out your /home anywhere including a network share.

---

### Post by dracomordag on 2007-03-22
if i just created a 8 GB partition and a 42 GB partition, how do I install to use one as / and one as /home?

should i just install to the 8GB, then follow those guides to mount the other as my home?

---

### Post by orb9220 on 2007-03-22
> if i just created a 8 GB partition and a 42 GB partition, how do I install to use one as / and one as /home?

Well during the manual config you will come to the assign page where you point / from pulldown for the 8gb partion and the /home to the 42gb partition.

Just be sure that / is assign to the partition you want and /home points to the other partition you want.

And just like yours I have root / to a 10gb and my /home to my 55gb partition. 
It is a good idea to give /home the bigger partition.

---

