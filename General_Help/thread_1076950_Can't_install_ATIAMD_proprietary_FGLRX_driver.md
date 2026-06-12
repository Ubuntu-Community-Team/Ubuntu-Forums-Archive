---
title: "Can't install ATI/AMD proprietary FGLRX driver"
date: 2009-02-21
forum: General Help
---

### Post by magicmanfk on 2009-02-21
Suddenly after updating my computer, compiz fails to load all of the effects, and so I check out the hardware drivers section, and it shows that the ATI driver is not activated. If I hit "activate" it flashes the downloading driver screen but when it goes back it shows it still isn't activated. 

I'm thinking this might be something weird with updates, but it looks like I'm competely updated. It's an ATI X1300 mobility graphics card on a dell inspirion e1505 running intrepid. Thanks!

EDIT: I also tried reinstalling all the FGLRX drivers.

---

### Post by magicmanfk on 2009-02-26
fixed the problem; for some reason when I upgraded my kernel stuff it didn't completely register. It showed I was using 2.6.27-9 while I had most of the things installed for 2.6.27-11, including the restricted drivers. I uninstalled all the kernel/header stuff before 11 and made sure all the 11 stuff was installed and booted with that kernel instead, which fixed it.

---

### Post by mylord on 2010-01-10
Hi, I am new with ubuntu and I have the same problem, but can't fix it and I don't understand what you did to fix it. If you can tell me how to do this in details I' ll be very appreciated :)




P.S. the problem occured when i upgrated my ubuntu to v9.10

---

