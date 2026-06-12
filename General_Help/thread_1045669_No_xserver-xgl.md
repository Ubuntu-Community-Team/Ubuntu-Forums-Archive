---
title: "No xserver-xgl"
date: 2009-01-20
forum: General Help
---

### Post by lazypeterson on 2009-01-20
There is no xserver-xgl in my Synaptic Package Manager and I've done everything that was suggested with the universe repository, but I've had no luck. 

tim@tim-laptop:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xgl


compiz:

tim@tim-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

Any help would be greatly appreciated.

---

### Post by Ub1476 on 2009-01-20
Are you running Ubuntu 8.10 or 8.04.1? Have you installed graphic drivers from System-Administration-Hardware Drivers?

---

### Post by lazypeterson on 2009-01-20
> **Ub1476 said:**
> Are you running Ubuntu 8.10 or 8.04.1? Have you installed graphic drivers from System-Administration-Hardware Drivers?

I'm running 8.10. I have the ATI/AMD proprietary FGLRX graphics driver installed.

---

