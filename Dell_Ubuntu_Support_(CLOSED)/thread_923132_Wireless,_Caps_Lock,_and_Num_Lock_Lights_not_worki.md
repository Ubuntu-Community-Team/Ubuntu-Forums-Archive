---
title: "Wireless, Caps Lock, and Num Lock Lights not working on M1330"
date: 2008-09-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by goeagles520 on 2008-09-18
Hello,

First off let me start with the system info. I am running Hardy on an m1330. When I first installed the system, the wireless light never worked but the caps lock and num lock lights (located on the black bar where the volume controls are) worked  fine. Now, none of my lights work? Any thoughts? Im pretty new to ubuntu so please let me know if you need more information.

Gratzi,
Go

---

### Post by goeagles520 on 2008-09-18
Heh heh heh...an advanced search of the forum revealed a solution...

sudo apt-get remove mouseemu

this solves the problem for caps lock and num lock.

Now, does anybody have any idea on how to get the wireless light to work...?

Thanks,
Go

---

### Post by superm1 on 2008-09-18
If it's an intel card; you have to install linux-backports-modules-hardy

---

