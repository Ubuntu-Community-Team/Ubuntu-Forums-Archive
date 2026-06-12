---
title: "Can't empty trash"
date: 2009-03-29
forum: General Help
---

### Post by hufferd on 2009-03-29
I somehow have gotten a folder (that I don't need) with files I copied off a CD in it. In the trash it is 3.2gig of stuff I no longer need it was a CD that came with a new GPS unit I bought & I can not get rid of it ... ie. empty the trash it acts like it is doing something but then when its done the folder is still there with all the contents :( 

Any ideas? 

D

---

### Post by drs305 on 2009-03-29
The trash probably contains items belonging to root. The easiest way to deal with it is to open nautilus with root privileges and use SHIFT-DELETE to remove it:
```
gksudo nautilus ~/.local/share/Trash/files
```
Root trash in its own bin is located at /root/.local/share/Trash/files

For more information, refer to the guide on finding and removing trash. The link is in my signature line.

---

### Post by UbuntuNerd on 2009-03-29
try this, in a terminal type:
```
gksu nautilus
```
browse to this location '/home/user/.local/share/Trash' and delete the folder
also check [here](http://my.opera.com/ubuntunerd1/blog/empty-the-trash-even-if-it-says-you-can)

---

### Post by hufferd on 2009-03-29
> **drs305 said:**
> The trash probably contains items belonging to root. The easiest way to deal with it is to open nautilus with root privileges and use SHIFT-DELETE to remove it:
```
gksudo nautilus ~/.local/share/Trash/files
```
Root trash in its own bin is located at /root/.local/share/Trash/files

For more information, refer to the guide on finding and removing trash. The link is in my signature line.


Hey thanks this worked :) and I will check that guid out some more

thanks for your help 
D

---

