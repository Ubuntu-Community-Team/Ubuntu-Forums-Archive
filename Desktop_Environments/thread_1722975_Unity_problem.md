---
title: "Unity problem"
date: 2011-04-06
forum: Desktop Environments
---

### Post by Mosabama on 2011-04-06
hi,

I installed unity on ubuntu 10.10. when it first starts there is no problem ... but when I hover over any window the mouse gets stuck or at least REALLY slow that I cant control it. (I noticed also the keyboard does the same) 

some sites I searched suggested to remove unity application package and some other pack .. but it did not help.

I use ATI (propriety drivers) on a Toshiba Laptop
intel core i3, 3GB ram

please note that I downloaded gnome3-shell to try it but the exact same thing happened as unity.

---

### Post by Mosabama on 2011-04-13
Maybe this will help:

when I open any window.. and resize it to small size .. the CPU usage will be 10% but if I make it big the CPU will go 70 to 100 !!

and the process which uses the cpu is X sever.

when I close the window it will go back to normal.

maybe mutter is the reason ?
is it possible to replace mutter with compiz? although I tried that the screen goes empty !!!

---

### Post by Mosabama on 2011-04-13
one more thing when I uninstall fglrx it works fine .. but I want to use fglrx !!!

---

### Post by Mosabama on 2011-04-14
bump

---

### Post by Copper Bezel on 2011-04-14
Unity isn't doing anything wonky with the video driver or xserver, so the problem is most likely Mutter, yes. Do you have any problems running Compiz under a Desktop Edition session? If not, just wait on using Unity until the 11.04 upgrade. It's a completely separate package and built on Compiz, rather than Mutter. (Unity in 10.10 will not run under Compiz.) I just checked, and fglrx is still supported in 11.04.

Edit: Rather critical typo.

---

### Post by Mosabama on 2011-04-14
Thanks,

actually I have no problem with compiz on gnome2. so I will wait for 11.04.

do you have any idea if gnome3 can run using compiz too? cause I have the same problem with gnome3.

---

### Post by Copper Bezel on 2011-04-15
No, because Gnome 3 is also built on and heavily integrated with Mutter, unfortunately. It definitely sounds like Mutter is a no-go with your graphics card, but at least Unity shouldn't be a problem in 11.04.

---

### Post by Mosabama on 2011-04-16
well .. thanks for you reply .. I guess I am gonna keep using gnome2 until they find a solution with ATI and mutter hopefully.

---

