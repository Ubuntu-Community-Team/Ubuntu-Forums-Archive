---
title: "PAE kernel"
date: 2009-02-13
forum: General Help
---

### Post by RedSingularity on 2009-02-13
I wanted to use all my available RAM without upgrading to a 64bit.  I herd about enabling PAE in the Linux kernel.  Anyone know how i can do this?

---

### Post by rbmorse on 2009-02-14
I was using 32-bit 8.10 and now run the 8.10 server kernel. 

If you use Synaptic to search on:

2.6.27-11-server

it should return five results. I loaded all but the linux-headers-lvm package and then rebooted the system.  You should see a new entry at the top of the GRUB menu to load the server kernel, that comes with the PAE extensions enabled by default, and it works for me. 

Question of my own....what does lvm do, and should I install those headers, too?

---

### Post by dcstar on 2009-02-14
> **rbmorse said:**
> I was using 32-bit 8.10 and now run the 8.10 server kernel. 

If you use Synaptic to search on:

2.6.27-11-server

it should return five results. I loaded all but the linux-headers-lvm package and then rebooted the system.  You should see a new entry at the top of the GRUB menu to load the server kernel, that comes with the PAE extensions enabled by default, and it works for me. 

Question of my own....what does lvm do, and should I install those headers, too?

Are you using LVM arrays?

Anyway, if you use 8.10 how come your profile says you use 8.04??

---

### Post by sdennie on 2009-02-14
This thread contains the various methods of accessing 4 or more GB of RAM with Ubuntu: [ Ubuntu with 4GB+ of memory]("http://ubuntuforums.org/showthread.php?t=855511")

---

### Post by 3rdalbum on 2009-02-14
You've got a 64-bit processor - why not just use 64-bit Ubuntu?

PAE is a hack that was designed to allow 32-bit processors to use more than 4 GiB of RAM - now that Ubuntu works just as easily in 64-bit as it does in 32-bit, and since you have a 64-bit processor, I really can't think of any reasons why you'd still need a 32-bit operating system.

---

### Post by rbmorse on 2009-02-14
> **dcstar said:**
> Anyway, if you use 8.10 how come your profile says you use 8.04??

Because I haven't update my profile??

---

### Post by Francewhoa on 2011-04-09
Official instructions at [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

