---
title: "Ubuntu error 17"
date: 2009-02-02
forum: General Help
---

### Post by timoore on 2009-02-02
Hey this problem has been going on for days and i've tried to fix it with other posts but they didn't work. 

   Anyways, I've been using solely Ubuntu 8.04 for about 6 months on my HP laptop and everything was working fine, then one day it just froze and when i restarted it, it had the: 

GRUB loading stage 1.5

GRUB loading please wait.....
Error 17

   I tried reinstalling Ubuntu, but when i get to the prepare partitions step it's just blank, and the partition editor also doesn't show any partitions. Also in terminal: sudo fdisk -l returned nothing at all not even an error message. I'm beginning to think it my be a hardware problem opposed to a software problem. Any help would be appreciated thanks.

Cheers,
Tim

---

### Post by Crafty Kisses on 2009-02-02
If there's anyway you can get this output to us, it would be great:
```
sudo fdisk -l
```

---

### Post by caljohnsmith on 2009-02-02
From your Live CD, how about opening a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
sudo sfdisk -d
```
And make sure to include the "-lu" and not just "-l" with the fdisk command, because I will need to see the start/stop points of your partitions in sectors (not cylinders) in order to determine if there is something wrong with your partition table.

---

### Post by timoore on 2009-02-03
Hey guys thanks for the quick reply.

I tried both

sudo fdisk -lu
sudo sfdisk -d

and

sudo fdisk -l

From my live CD terminal and nothing gets outputted

---

### Post by caljohnsmith on 2009-02-03
If fdisk can't see your drive, then unfortunately you probably have either a hardware problem or maybe an issue with how the HDD is configured in your BIOS. Sorry I can't be of much more help.

---

