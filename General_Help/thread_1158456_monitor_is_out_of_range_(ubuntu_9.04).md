---
title: "monitor is out of range? (ubuntu 9.04)"
date: 2009-05-13
forum: General Help
---

### Post by josepaul on 2009-05-13
hey guys, this is my first post, :p, and also my first installation of ubuntu :), OK, lemme get to the point, I have to install my graphics card to use compiz and stuff like that, so I tried to install both EnvyNG and the normal ubuntu driver 180 or something similar, so I install it and then when I reboot, I can see the boot screen but then my monitor says out of range, 

I have spent atleast 3 hours during 4 days trying to find out why this happens and this is apparently because the refresh rate default is too high or the resolution is too high, so I go into command (first time as well :p using the ctrl-alt-F2 thing) and I try all these things;

"sudo dpkg-reconfigure xserver-xorg" which is where I find out I can only change settings for the keyboard because they removed the monitor settings bit (or so I have been told)

"gksu displayconfig-gtk" which comes up with some warning and does nothing

"dpkg-reconfigure -phigh xserver-xorg" which does somewhat the same


I installed Ubuntu using wubi on my vista computer (dual boot)

Thanks for anyone who can help me (I know it's probably something really stupid, like I kept thinking what this root user thing was and then found out you had to be like an admin to use some commands :D)

---

### Post by josepaul on 2009-05-13
By the way, my graphics card is a 256mb Nvidia GeForce 8400 GS

---

### Post by Tipped OuT on 2009-05-13
You should have just used the "Hardware Drivers" option in 
System< Administration< Hardware Drivers.
Have you tried using the default settings of Xorg?

---

### Post by josepaul on 2009-05-13
Yea, that's what I tried and what I meant by "the normal ubuntu driver", sorry, I am new to this :D

---

### Post by josepaul on 2009-05-13
how do you use the default settings of xorg?

---

### Post by josepaul on 2009-05-13
anyone?

---

### Post by Kareeser on 2009-05-13
To restore default settings, you either delete xorg.conf or run the command:
sudo dpkg-reconfigure -phigh xserver-xorg

... which you've already done.

Try a different monitor.

---

### Post by josepaul on 2009-05-14
I'm sorry but this is the only monitor I have got :( and I don't know anyone who has a spare monitor, 

by the way, is it to do with installing ubuntu through WUBI?

---

### Post by josepaul on 2009-05-14
Anyone!?

---

### Post by josepaul on 2009-05-14
C'mon guys, I really need this to really use my computer :confused:

---

