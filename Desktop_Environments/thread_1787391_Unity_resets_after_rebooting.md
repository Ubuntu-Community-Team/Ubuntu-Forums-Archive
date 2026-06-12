---
title: "Unity resets after rebooting"
date: 2011-06-21
forum: Desktop Environments
---

### Post by TheWizKid95 on 2011-06-21
Okay, first time Linux user here, I have Ubuntu 11.04 Natty Narwhal and after every reboot, my unity setup resets and its getting pretty annoying. it reverts back to the stock launcher setup: Home, Ubuntu Software Center, Mozilla Firefox, Libre apps, etc. I wanted to try out different things, so i tried the gnome3, but reverted with the help of this site since i didnt like it. idk if this is the cause, but i hope someone can help. i also installed kamal's 2.6.38-10 kernel for my Dell Inspiron 14R's backlight fix. any help?

---

### Post by TheWizKid95 on 2011-06-21
Shameless self bump :/

---

### Post by Krytarik on 2011-06-21
Check if the package "libdconf0" is installed:
```
dpkg -l |grep libdconf0
```
If it isn't, install it:
```
sudo apt-get install libdconf0
```
Greetings.

---

### Post by meconio on 2011-06-30
same here, but my problem was that I installed gnome-shell, didn't like it and revert back to unity, everything works fine, except for the fact that Launcher reset every time I boot up to the default icons, but does not do that for the size and other settings from the compiz-fusion manager.  

So to make myself clearer, I can change launcher icon size and looks, but the type of icons just restart to default after every boot up secuence.

tried the solution, but I did have installed that, nevertheless tried to install it again with no solution of the problem after rebooting.

---

### Post by ogregore on 2011-06-30
Had the same problem.  Went through reinstalling everything related to unity and finally when I reinstalled libdconf0 the problem cleared and everything was back to the setup I had prior to screwing things up with Gnome 3, all the quicklists and everything. Try that.

Cheers 
Ogre

---

### Post by meconio on 2011-06-30
> **ogregore said:**
> Went through reinstalling everything related to unity and finally when I reinstalled libdconf0 

Thanks man but could you be more specific like give me a link or something, cause I googled "reinstall Unity" and all that i could find was adding a ppa for some sort of beta versions of Unity.

Update:  Nevermind dude, I got it, I went to Synaptic and selected libdconf0 for reinstall and now I got back my old Launcher config it's been so far 4 restarts and no reset of the icons.

---

### Post by ogregore on 2011-07-03
Great - glad it worked, sorry my instructions were a little vague.

Cheers
Ogre

---

### Post by ren48185 on 2011-07-18
Thank you for that. I set to reinstall and it worked.

---

