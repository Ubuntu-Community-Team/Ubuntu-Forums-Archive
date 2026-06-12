---
title: "can't find Version.h  (Noobie here)"
date: 2009-04-08
forum: General Help
---

### Post by ronaldo07 on 2009-04-08
Hi guys


I have default installation of Ubuntu 8.10

When I am trying to install driver for my CAN-USB adapter, I am getting following error.
> Makefile:64: *** "Can't find /usr/src/linux/include/linux/version.h !".  Stop.


I am very new to Ubuntu. Can anyone help me out here ?

---

### Post by ronaldo07 on 2009-04-08
I think I found the reason but I am not sure how to solve it.

I have this file under another directory
linux-headers-2.6.27-11

I read that I need to link it to /usr/src/linux or something like that.
I don't know how to do it ?

Any expert want to help me out here ?

Thanks

---

### Post by ronaldo07 on 2009-04-08
LOL

No one is replying to simple question. 
BTW I found solution myself after googling and searching for 3 hrs.

I had to link /usr/src/linux to the folder where I had version.h using 
ln -s

Thanks for help everyone :lolflag:

---

