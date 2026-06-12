---
title: "Beryl problems"
date: 2007-01-31
forum: Desktop Environments
---

### Post by vineetphillips on 2007-01-31
Hey, 
i m facing the same problem .. i have an internal graphics card (82845G/GL[Brookdale-G]/GE Chipset) . i followed [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_AIGLX)
to install beryl on my Ubuntu LTS 6.06 .. the problem is that everyhting is installed except the linux-dri-modules-2.6.15-27-386.. the site says that this package is broken and needs to fixed  and so when i try to install this package it gives me an error saying 

sudo apt-get install xserver-xorg-air-core linux-dri-modules-common linux-dri-modules-2.6.15-27-386
Reading package lists... Done
Building dependency tree... Done
xserver-xorg-air-core is already the newest version.
E: Couldn't find package linux-dri-modules-2.6.15-27-386

I also tried installing the linux-dri-modules-2.6.15-26-386 but then it gives me an error saying 
Reading package lists... Done
Building dependency tree... Done
xserver-xorg-air-core is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-dri-modules-2.6.15-26-386: Depends: linux-image-2.6.15-26-386 but it is not installable
E: Broken packages
 i guess it is because i had cancelled while it was installing before (because i wa not sure)

has anyone got a way around it!!

---

### Post by Brunellus on 2007-02-01
thread moved.  [Beryl is off-topic in Absolute Beginners](http://www.ubuntuforums.org/showthread.php?t=349732)

---

### Post by glabouni on 2007-02-01
[http://ubuntuforums.org/showthread.php?t=351319](http://ubuntuforums.org/showthread.php?t=351319)

---

