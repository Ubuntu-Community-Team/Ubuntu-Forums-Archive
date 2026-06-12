---
title: "Desktop Effects"
date: 2009-07-27
forum: Desktop Environments
---

### Post by weef on 2009-07-27
Hi!!

    I'm a newbie to Ubuntu and Ubuntuforums.org but not to Linux. I used to use Fedora 10 and yes I understand the difference between Red Hat based Os and a Debian based Os like Ubuntu. So I have the latest kernel (2.6.28-13-generic) and updates (as of Sunday, July 26, 2009 9:00 ET time). So I installed the following driver for my Nvidia 8300 256 MB RAM video card: Nvidia accelerated graphics version 180 which was recommended by Ubuntu. I got the driver through: System --> Administration --> Hardware Drivers. So as I tried to enable Desktop Effects through: System --> Preferences --> Appearance and the Visual Effects Tab. When I try to enable it on any level (Normal or Extra), my screen then flickers and finally the following message showed up: (!) Desktop Effects can not be enabled. So can anyone provide any support? 

Thank you in advanced,
Weef

---

### Post by ~sHyLoCk~ on 2009-07-27
See if ```
modprobe nvidia
``` shows any error. Usually this happens when you don't have the driver installed, which you have.

---

### Post by weef on 2009-07-27
Nope, No error.

---

### Post by weef on 2009-07-27
Umm anyone?????????

---

### Post by chrisinspace on 2009-07-27
If you install the compiz-gnome package, it will install a more robust implementation than the default Ubuntu desktop effects.  You can then use the Compiz settings manager to enable/disable specific plugins.  It may just be that one of the plugins is not playing well with your system.

---

