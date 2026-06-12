---
title: "Can't get Comiz to work"
date: 2008-03-14
forum: Desktop Effects &amp; Customization
---

### Post by Extremeshannon on 2008-03-14
Hello all. I have been trying for a week to get Compiz to work. I really would like to have a cubed desktop. After all my tweaking and reading forum post all over the internet I reloaded Ubuntu 7.10. I have a fresh default install and I followed this guide.

[http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-52]("http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-52")

I have done all the steps in that order. Any help would be great. I am still kind of new to Linux :lolflag:

AMD Dual core
2Gigs Ram
7800GTX video card
Alienware Aura M7700
ATI chipset](*,)](*,)

---

### Post by Afkpuz on 2008-03-14
Well, I couldn't access the link you posted.  I think I would need to register with the site to see it.  But here are the basic steps you need to follow.


1.) Install Video driver 
Goto System>Administration>Restricted Drivers Manager
Check the box to install your video driver

2.) **If you have an ATI card**, You'll need xserver-xgl.  If you are using an NVIDIA graphics card, you won't need it.  To download it, paste this into a terminal.  Applications>Accessories>Terminal  (please note that you have to press ctrl+Shift+v in order to paste things into the terminal)
```
sudo apt-get install xserver-xgl
```

3.) Install compizconfig-settings-manager for ease of use

*REBOOT*

4.) Enable desktop effects by right clicking on desktop>Change Desktop Background>Visual Effects Tab

Have you done all these steps?

---

