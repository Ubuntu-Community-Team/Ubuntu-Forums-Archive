---
title: "Too late for LVM?"
date: 2006-01-26
forum: Desktop Environments
---

### Post by misterc on 2006-01-26
I just got breezy installed and running.
My PC has a 40GB disk which I let the install erase&partition for me.

During install I ignored my 2 other drives (160 & 200GB). 
They show up as /dev/hdc & /dev/hdd but have NO partitions on them.

Now I would like to setup breezy to treat them as ONE BIG drive (that I can use SAMBA to share with the rest of the PCs on my net)

Where do I go from here?

Thanks in advance.

---

### Post by misterc on 2006-01-27
Can I setup LVM while breezy is running?  
or do I need to re-boot from an install or Live CD ?

---

### Post by cwaldbieser on 2006-01-27
[QUOTE=misterc]Can I setup LVM while breezy is running?  
or do I need to re-boot from an install or Live CD ?[/QUOTE]
I believe you can turn your empty drives into storage for Logical Volume Management (LVM) while Breezy is running.  You then mount the logical volume at some mount point on your root filesystem.

---

### Post by misterc on 2006-01-30
I WAS able to get LVM added on after quite a bit of web searching and command line configuration. 

I'd think a tool like LVM would have a decent graphical front-end by now...
I sure couldn't find one.

---

### Post by mchatel on 2006-01-30
I will be looking at my current LVM setup again soon, as I just installed another hard-drive in the computer.  I love LVM, and will definitely keep an LVM setup in the future.  

I use mine in conjunction with a ReiserFS filesystem, and it's nice to resize my various mount points on the fly.  :-)

---

