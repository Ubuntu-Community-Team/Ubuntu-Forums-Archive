---
title: "How i can reinstall my Ubuntu"
date: 2007-09-20
forum: Desktop Environments
---

### Post by hellolijo on 2007-09-20
hi 
     i want to reinstall my Ubuntu....
     I tried to do that by putiing the  installation Cd again , 
     But it is showing that the disk space is not available....

What i should do ..................

---

### Post by hellolijo on 2007-09-20
Hi,
    i tried to install the Opera Package for my ubuntu ....
    But it is showing this error..


root@lijo:/home/lijo/Desktop# apt-get install opera
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package opera

Would u able to help me...

---

### Post by tropcky on 2007-09-20
i really dont know what do u want  is it reinstall ubuntu  ? or install opera for ubuntu 

any way if u wanna reinstall ubuntu 
 boot from cd and do evry thing as normal but when u come to the partioner  mark on manual 
( so u can do it by ur self then press forward locate the partion   that u gonna install ubuntu in it 
and right click chose delete and delete it  and create it all over agen  ( of curse  make it ext3 ) 
 
and about opera 
E: Couldn't find package opera
means that u dont have it in ur sources  list  if u install Automatix2 its gonna help 2 install alot of good things  u will faind it ther 
[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_Automatix2_with_Apt](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_Automatix2_with_Apt)

---

### Post by ugm6hr on 2007-09-22
> **hellolijo said:**
> Hi,
    i tried to install the Opera Package for my ubuntu ....
    But it is showing this error..


root@lijo:/home/lijo/Desktop# apt-get install opera
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package opera

Would u able to help me...

Opera is not available from apt-get (I think).  Go to the [opera.com]("http://www.opera.com/download/") website, download the correct .deb file and just double-click on it.

To reinstall Ubuntu, you may have to erase the previous installation (i.e. delete the Ubuntu partition) prior to re-installing.

---

