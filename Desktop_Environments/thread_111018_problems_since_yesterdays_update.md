---
title: "problems since yesterdays update"
date: 2006-01-01
forum: Desktop Environments
---

### Post by rupert on 2006-01-01
Hi,
yesterday i had a 70MB update and since than many programms wont run, they all fail with a memory allocation error "Speicherzugriffsfehler" in german.
I also now have a kubuntu splash instead of the normal ubuntu splash.
I use Gnome but have KDE installed for testing(longer thatn yesterday).
I also played arround with different installations of wine, where i first got these errors.
And tried to install the latest NVIDIA on Christmass, but havent got it working, seems the yesterday kernel update havent brougth the right nvidia modules with it.
Please help me, i have exams next months and absolutily no time to hack with my system for hours, maybe i can post some logfiles where you can give me tips.


thx

---

### Post by anil_robo on 2006-01-01
As per my own experience as well as other references online, GNOME and KDE do not go well together. I had many problems when I installed KDE just to try it out, so I had to remove it after half an hour. Yours sounds a similar case.

If you want to remove kde, you can take the following steps:
1. ```
sudo apt-get remove kubuntu-desktop --purge
``` 2. ```
sudo apt-get remove kdm
``` 
THat should do it. If any problems, you might have to reconfigure gdm this way: ```
sudo dpkg reconfigure gdm
```

Let me know if it solves the problem. Or else we'll try something else! :)

---

### Post by rupert on 2006-01-01
this didnt work, it only removed the  kubuntu-desktop file but not kde, or any of it compontents

---

### Post by rupert on 2006-01-02
well it seems only one App wont work now, can live with that so far.
But the bigger problem is that i have to recompile the nvidia driver after every reboot. 
The module gets loaded at startup but the xserver crashes:
[http://az-lantech.de/ubuntu/Xorg.0.log.old](http://az-lantech.de/ubuntu/Xorg.0.log.old)

After recompiling with exactly the same xorg.conf it works fine.
I use the latest nvidia drivers.

I read that many people have problems with non ubuntu drivers, 
but im now have trouble with both :(

wait, why is it using /root/xorg.conf ???

Thats strange and says enough!

it seems it uses only the conf in roots folder when i start gdm with /etc/ini.d/gdm start

---

