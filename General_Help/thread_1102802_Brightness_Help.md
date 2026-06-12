---
title: "Brightness Help"
date: 2009-03-22
forum: General Help
---

### Post by Jokenno14 on 2009-03-22
Hello all! I have wondered into the woods and have chosen to make Ubuntu my main OS.

I first installed it as a guest on my XP partition using VMWare and it worked fine sides that opengl is not supported so I decided to make it my main OS which I have done. 

My problem however is that the screen is very dim (almost unreadable) and I have googled to death a way to increase the brightness.

I am running Ubuntu 8.10 on a M50SV ASUS laptop (Gfx Nvidea 9500M GS - Latest 177 drivers installed). 

In BIOS and the Ubuntu boot manager (I have 4 OS's on this thing) the brightness is fine....also the first part of the Ubuntu loading the screen is fine as well until just at the end it goes dark and then the desktop loads so I assume its me doing something wrong! hopefully it is a easy fix.

What I have tried:
-At first startup I noticed the brightness changed automaticly so I assumed it was my laptops auto light detector thingy so I googled how to turn it off and found this:
[http://seethisnowreadthis.com/2008/05/19/how-to-install-ubuntu-804-hardy-heron-on-the-asus-m50sv-a1/](http://seethisnowreadthis.com/2008/05/19/how-to-install-ubuntu-804-hardy-heron-on-the-asus-m50sv-a1/)
I completed all the brightess tasks and I think it worked fine but the problem exisits. when I navigate to the brightness file and change the echo value and reset there is no change (like the problems below).

-I have tried the hot keys (Fn+F5) which does nothing

-Went to power option and changed it there which does nothing! I also tried taking the AC power out to see if the brightness changes but still nothing.

-When I go to the Nvidea settings (admin -> NVIDEA X Server Settings) and when I try to increase the brightness under X Server Color Correction all that happens is the amount of white colour increases (it does not make the screen brighter just whiter).


Hopefully there is a simple fix...because this is driving me nuts!

Thanks for your time!

---

### Post by CatKiller on 2009-03-22
You can set the gamma of X (the graphical part) with the **xgamma** command. Numbers greater than 1 will be brighter than the default, less than 1 is darker. So you might try ```
xgamma -gamma 1.5
``` as a starting point. Keep tweaking the value till you get the brightness that you want. When you've got the number that works for you, you'll want to make it so that it gets automatically set when X starts. You do this by editing X's configuration file with ```
sudo nano /etc/X11/xorg.conf
```The option goes in the "Monitor" Section as ```
Gamma          1.5
``` replacing 1.5 with whatever value you've chosen.

EDIT: If you find that the colours aren't quite right, you can adjust the red, green and blue gamma values independently. **man xgamma** will tell you more if you want to do this.

---

### Post by BelaC on 2009-03-22
> **CatKiller said:**
> You can set the gamma of X (the graphical part) with the **xgamma** command. Numbers greater than 1 will be brighter than the default, less than 1 is darker. So you might try ```
xgamma -gamma 1.5
``` as a starting point. Keep tweaking the value till you get the brightness that you want. When you've got the number that works for you, you'll want to make it so that it gets automatically set when X starts. You do this by editing X's configuration file with ```
sudo nano /etc/X11/xorg.conf
```The option goes in the "Monitor" Section as ```
Gamma          1.5
``` replacing 1.5 with whatever value you've chosen.

EDIT: If you find that the colours aren't quite right, you can adjust the red, green and blue gamma values independently. **man xgamma** will tell you more if you want to do this.


I don't think so setting away gamma is solving the original problem -like I have as well-

---

### Post by Jokenno14 on 2009-03-22
> **CatKiller said:**
> You can set the gamma of X (the graphical part) with the **xgamma** command. Numbers greater than 1 will be brighter than the default, less than 1 is darker. So you might try ```
xgamma -gamma 1.5
``` as a starting point. Keep tweaking the value till you get the brightness that you want. When you've got the number that works for you, you'll want to make it so that it gets automatically set when X starts. You do this by editing X's configuration file with ```
sudo nano /etc/X11/xorg.conf
```The option goes in the "Monitor" Section as ```
Gamma          1.5
``` replacing 1.5 with whatever value you've chosen.

EDIT: If you find that the colours aren't quite right, you can adjust the red, green and blue gamma values independently. **man xgamma** will tell you more if you want to do this.

hmmm I dont think gama is a issue but I will give it a go.

I think its the level of light from the screen is the problem...

Any other ideas?

---

### Post by Jokenno14 on 2009-03-22
Hazzah! I got it!

Apparently I didnt google enough:
[http://forum.notebookreview.com/showthread.php?t=332158](http://forum.notebookreview.com/showthread.php?t=332158)

Thanks all that tried to help tho.

---

### Post by CatKiller on 2009-03-22
Glad you got it sorted.

---

