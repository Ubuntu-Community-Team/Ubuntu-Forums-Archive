---
title: "How to update system info (after installling an image on a new computer)"
date: 2011-03-08
forum: Desktop Environments
---

### Post by FredericF on 2011-03-08
Hello everyone,

I've just receive my new Dell desktop (yé!) and I used CloneZilla to move everything from my old computer to the new one. I made an image of the disk of the old computer and 'restored' this image on the new one. 

For most of it, it worked well: it was relatively quick, and I have all my old settings except everythings is going quicker. But the new system is not entirely recognized: the processors are correctly identified, but I can't see the new RAM memory: hardinfo, free or cat /proc/meminfo all seem to refer to the memory of the old system, not the one that is on the new computer. 

Is there a way to force the system to reinspect the hardware and 'discover' its new ressources?

Thanks for your help!

---

### Post by Kirboosy on 2011-03-08
Welcome to the Forums! :)

Is the old Image a 32 Bit system and does new computer have 4 Gb of RAM or more?


~Caboose

---

### Post by rcayea on 2011-03-08
Maybe try, the command, lshw

or to get info about the product and vendor and so on:
dmidecode

Here are some other commands to try:
dmesg
lsdev
lshal
lspci
lsusb
lsscsi

I found most of this information at this website which may be helpful:
[http://puschitz.com/pblog/?p=29](http://puschitz.com/pblog/?p=29)


> **FredericF said:**
> Hello everyone,

I've just receive my new Dell desktop (yé!) and I used CloneZilla to move everything from my old computer to the new one. I made an image of the disk of the old computer and 'restored' this image on the new one. 

For most of it, it worked well: it was relatively quick, and I have all my old settings except everythings is going quicker. But the new system is not entirely recognized: the processors are correctly identified, but I can't see the new RAM memory: hardinfo, free or cat /proc/meminfo all seem to refer to the memory of the old system, not the one that is on the new computer. 

Is there a way to force the system to reinspect the hardware and 'discover' its new ressources?

Thanks for your help!

---

### Post by FredericF on 2011-03-08
Hello Caboose,

You spotted the problem right away! I thought I had installed Ubuntu 10.04 x64 on the old computer, but I just checked and the system architecture is i686. 
The new computer does indeed have more than 4 Gb or RAM, (12 Gb! double-yé!), and I want to be able to use every byte of it. So I guess that I will have to do a clean install after all...

Thanks again for your sharp eye!

---

### Post by FredericF on 2011-03-08
Hello Rcayea,
Thanks for the link. I will check it out, commands that allow you to get detailed system info are always useful!

---

### Post by Kirboosy on 2011-03-08
Glad I could help. 


Once again welcome to the forums :)


~Caboose

(Please mark your thread as "Solved". Under Thread Tools you can mark it :) )

---

