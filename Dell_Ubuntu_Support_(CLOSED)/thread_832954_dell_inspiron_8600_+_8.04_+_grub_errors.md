---
title: "dell inspiron 8600 + 8.04 + grub errors"
date: 2008-06-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by leemajors on 2008-06-18
hi there,
I bought a new 250g drive and thought I'd give hardy heron a try... However when I go through the install everything works well until I reboot, when I get a grub error. 

I have tried partitioning in a few different ways. First I tried putting / at the beginning with a sep. /home partition and a small swap, but I got error 17. Then I just tried doing a guided 250g / install and got the error 18 this time. 

One possible fix I've read about is going into the bios and configuring the hard drive detection but my old dell 8600 inspiron just won't give me that option. Does anyone know how to get to this seting in a 8600? I think imusing the most recent 8600 bios, a14. 

Any ideas?

---

### Post by fonephixer on 2009-07-06
I too am having the same problem on the Inspiron 8600, but I am trying to install Ubuntu 9.04 with a dual boot and XP.  

any help would be appreciated.

---

### Post by leemajors on 2009-07-10
the problem i was having was trying to do a dual boot starting with a fresh install of ubuntu and then adding windows.

i ended up fixing it by creating two partitions, installing windows first and then installing ubuntu 2nd. 

dunno if that will help you but it certainly helped me! good luck :)

---

### Post by fonephixer on 2009-07-10
no, I did that too.  I made a fresh install of windows on one partition, and then installed ubuntu.  I am getting the grub error that is talking about the hard drive size.  I went into my bios, but there is no way to change my hard drive settings.  I upgraded my bios, to the latest a14 from the dell site, but there is still no way to change the hard drive info.

---

