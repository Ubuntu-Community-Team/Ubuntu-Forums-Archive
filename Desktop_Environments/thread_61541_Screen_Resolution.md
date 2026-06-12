---
title: "Screen Resolution"
date: 2005-09-01
forum: Desktop Environments
---

### Post by Nixforce on 2005-09-01
Hi,

I am totally new at ubuntu... I installed Ubuntu for my cousin last night on his laptop (quiet an old one), and the resolution is stuck at 640x480- - he cant change it any higher, how can i get this fixed?

---

### Post by Razvan on 2005-09-01
Hi there, 

firstof try these: 

press ctrl-alt-f1 to get to a text console,
login with your usual password and username,
type ´sudo killall gdm´
supply your password
type ´sudo dpkg-reconfigure xserver-xorg´
type ´sudo gdm´

now your graphical environment restarts...see if you can chang the resolution with the tool in your main menu on the upper left on your screen...dunno how thats namen because im in school now

hope that helps, cheers, Martin

---

### Post by SpooD on 2005-09-01
[QUOTE=Razvan]Hi there, 

firstof try these: 

press ctrl-alt-f1 to get to a text console,
login with your usual password and username,
type ´sudo killall gdm´
supply your password
type ´sudo dpkg-reconfigure xserver-xorg´
type ´sudo gdm´

now your graphical environment restarts...see if you can chang the resolution with the tool in your main menu on the upper left on your screen...dunno how thats namen because im in school now

hope that helps, cheers, Martin[/QUOTE]
 If you're totally new to Linux it might be easier doing it this way:

Run xorgcfg :
1. Applications -> Run Application...
2. Type xorgcfg 
(A program window pops up, hopefully)
3. Click and hold on the monitor image -> choose Configure monitor(s)
4. Choose whatever fits your monitor/graphics card.
5. Click Quit
6. Click Quit (Answer yes to the qestions about saving your settings)
7. Reboot your computer, or do the kill-thing Martin described.

---

