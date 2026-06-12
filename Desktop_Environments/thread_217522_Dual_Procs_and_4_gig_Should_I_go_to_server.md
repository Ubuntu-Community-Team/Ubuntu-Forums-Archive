---
title: "Dual Procs and 4 gig Should I go to server?"
date: 2006-07-17
forum: Desktop Environments
---

### Post by systimax on 2006-07-17
Hello

I have a dual Proc Xeon machine with 4 gigs of ram. I may use it for vmware server or something else.

I have read a few conflicting points about the dual proc support in desktop.

Some have said that it supports it in 6.06 with out anything, some say that you need to install the 686 by doing a sudo aptitude install linux-image-686.

Does anyone know the correct point above? Or should i just go to server and it will be supported out of the box?

thanks

By the way I prefer desktop since im just learning ubuntu

---

### Post by brickbat on 2006-07-17
I have an AMD X2 and it works fine.

---

### Post by Dubbayoo on 2006-07-17
The default 386 kernel doesn't support SMP, but installing a new kernel is trivial.

---

