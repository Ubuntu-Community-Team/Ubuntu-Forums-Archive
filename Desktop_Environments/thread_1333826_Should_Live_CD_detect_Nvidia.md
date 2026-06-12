---
title: "Should Live CD detect Nvidia"
date: 2009-11-21
forum: Desktop Environments
---

### Post by ssulaco on 2009-11-21
I'm Running Hardy Heron live,is it possible to use visual effects while using the Live cd?
```
ubuntu@ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
ubuntu@ubuntu:~$ 
```
When i click on Hardware Drivers I get "No proprietary drivers are in use on this system"
Thanks in advance

---

### Post by Melcar on 2009-11-21
With an nvidia card no.  No open source drivers available on the LiveCD that can provide 3D acceleration for those chips.

---

### Post by mc4man on 2009-11-21
with karmic and probably the jaunty live cd you can install and load  restricted drivers ( load with a log out instead of a restart.

I don't remember hardy being able to do so.

(karmic may have them on the cd, in any event better to get from repo I'd think

---

### Post by ssulaco on 2009-11-21
> **Melcar said:**
> With an nvidia card no.  No open source drivers available on the LiveCD that can provide 3D acceleration for those chips.
Thanks Melcar

> **mc4man said:**
> with karmic and probably the jaunty live cd you can install and load  restricted drivers 
mc4man.....how would i go about loading restricted drivers if I was running Karmic "Live"?

---

### Post by ssulaco on 2009-11-21
Burnt Karmic,booted it up and within 15 sec after the desktop finished loading,a Hardware driver icon appeared at the top panel and a message stating "restricted drivers are available",I installed recommended driver and logged out...(yep,I couldnt log back in),tried guest,ubuntu,left everything blank.had to reboot.
If you log out of Karmic "Live" the Username is ubuntu,and leave password blank.also had to enable software sources to install ccsm.wobbly windows working good "Live"........Thanks

---

### Post by mc4man on 2009-11-21
generally if I want to fool around or test something from a live cd, after booting up and enabling Internet (wireless here) is to go to software sources, enable the ubuntu software sources and disable the cdrom sources.

Depending on how much memory you have you can do quite a bit. 

to free up some memory, after installing packages go to /var/cache/apt/archives and delete the .debs
( best to either shift+delete or in gksu nautilus -> edit -> preferences you can enable the 'delete' for root

see you figured out how to log back in...

---

### Post by ssulaco on 2009-11-22
Thanks mc4man,for advice,do appreciate it.

---

