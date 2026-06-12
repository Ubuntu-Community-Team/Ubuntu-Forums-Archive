---
title: "Eagle Cad Simulation in Linux"
date: 2010-04-17
forum: Education &amp; Science
---

### Post by owenlinx on 2010-04-17
Does anyone know of a ulp that would allow Eagle schematics to be edited and simulated in ltspice or gspiceui. Currently I am booting a virtual machine and running b2spice. Two issues with that; first I would love to be all Linux, Second b2 spice crashes alot. Any help would be much appreciated.

---

### Post by tunasky on 2010-04-20
Hey, owenlinx

I'm not sure if that is possible at all
Although wish you good luck with solving the problem!




____________________
[freelance writers]("http://www.freelancercareers.com") are great guys!

---

### Post by owenlinx on 2010-09-02
[ftp://ftp.cadsoft.de/eagle/userfiles/misc/eaglesp3-0.99e.tgz](ftp://ftp.cadsoft.de/eagle/userfiles/misc/eaglesp3-0.99e.tgz)

install ngspice and xspice

[http://sourceforge.net/projects/ngspice/files/](http://sourceforge.net/projects/ngspice/files/)

I installed from the binaries. Listed under "17"

they are dependent on each other so 

```
sudo dpkg -i *.deb
```

The addon sp3 has pretty good documention to start with spice enable do 
```
./starteagle
```
from the dir you extracted sp3

---

