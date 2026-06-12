---
title: "How do I add these....."
date: 2009-01-19
forum: General Help
---

### Post by Dobbie03 on 2009-01-19
I am new to Ubuntu and I really like the way it looks but I want to add these widgets like the ones on this desktop in the picture:

[IMG]http://img528.imageshack.us/img528/392/20oct08et8.gif

if the hotlink doesnt work:
[http://img528.imageshack.us/img528/392/20oct08et8.gif](http://img528.imageshack.us/img528/392/20oct08et8.gif)


how do I get them on my desktop????

---

### Post by metallicamike on 2009-01-19
first do ```
sudo apt-get install screenlets
``` and then download whichever ones you want from any website that has them,e.g.[www.gnome-look.org](www.gnome-look.org) and install them.

---

### Post by spupy on 2009-01-19
Looks like Conky to me.
[http://ubuntuforums.org/showthread.php?t=281865&highlight=post+conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=post+conky)

Conky is a highly configurable program that can display all sorts of information on your desktop. The configuration is stored in a file called ".conkyrc" inside your home directory. The link I posted leads to a thread where people post their conkyrc files along with screenshots. You can browse that thread a little, and when you like a setup from a screenshot, save the posted text as ".conkyrc" inside your /home. (Don't forget the dot at the start of the file name).
Then install conky:
```
sudo apt-get install conky
```
Now you can press Alt+F2 to open the run dialog, type in "conky" and hit enter to start the program. (If you like it, you can add the program conky to your startup (but I forgot how to do that in ubuntu)).

---

### Post by Dobbie03 on 2009-01-20
Thanks Guys

---

