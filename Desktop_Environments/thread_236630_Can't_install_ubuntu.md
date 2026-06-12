---
title: "Can't install ubuntu"
date: 2006-08-15
forum: Desktop Environments
---

### Post by bbtwin on 2006-08-15
Hi, I just changed computer and my ubuntu won't install.
I have a new Athlon 3500+ with a MSI NX7600GT graphics card, a Winfast 6100K8MA motherboard and a Samsung SATA 200Go Hard disk. I start the 6.06 LTS CD, installation begins and the xserver crashes. The log says something about 'no screens'. I think it doesn't recognize the graphics card. I tried the 64 bit version too, same problem.
I read the forums, and tried some options to start like 'noapic' or 'acpi=off' or 'vga=771'. Same problem.
I tried a dpkg-reconfigure xserver-xorg and tried the vesa driver and the nv driver. Same problem.
Has anyone an other idea ? I want my Ubuntu back !!!

---

### Post by nick122147 on 2006-08-15
Hi, I had the same problem with the Gentoo LiveCd disk. I found a solution: 

went to another terminal with cntr alt f1 or f2 or another... , killed x with kill "job Id number - you have to run top first to see what job number x has. 

I then edited the /etc/X11/xorg.conf file. I have a nVidia card and under "driver" it stood vesa or somthing, I changed this to "nv" saved and then type startx and it worked. 
Hope this might help.

Steinar

---

