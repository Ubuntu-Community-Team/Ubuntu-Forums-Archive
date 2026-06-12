---
title: "root?"
date: 2005-12-22
forum: Desktop Environments
---

### Post by ESPOiG on 2005-12-22
i cant login into root

i activated it to be able to login via gdm or sumtin in the logon setup thingo :D... and i have had my root password activated for a long time

and then wen i go to log in to root it says <wrong plz try makin sure the caps arnt on well sumtin like case sensative or sumtin>

then i cant get into it

does anyone know y or wat i may have done to do this :D

---

### Post by Juippisi on 2005-12-22
Try "sudo passwd".

---

### Post by Juippisi on 2005-12-22
Btw, why do you want to login in to Gnome as root? That's just insane!

Just log in as a normal user and believe to the power of the sudo.

---

### Post by ESPOiG on 2005-12-22
yeh but i dont know how to set the settings of nautilis by just command lime sudo :D

---

### Post by Juippisi on 2005-12-22
So... you need to setup Nautilus? Why you can't set it up as a normal user? If you want to use Nautilus as a root, I think "sudo nautilus" works - I'm not sure about it.

You can also have some menus to Nautilus, something like "Open this file as root". If you need to open some config file for example and you're too lazy to type "sudo gedit /where/is/that/file" :-).

---

### Post by fordfan753 on 2005-12-22
[QUOTE=ESPOiG]yeh but i dont know how to set the settings of nautilis by just command lime sudo :D[/QUOTE]

You could just go into nautilus as root using the "sudo nautilus" command in a terminal. You can get to nautilus settings through nautilus.

---

### Post by 23meg on 2005-12-22
You can also hit alt+f2 and type ```
gksudo nautilus
``` to have a superuser Nautilus. You can use gksudo to launch any GUI app as root.

---

### Post by Sutekh on 2005-12-22
Here is a link to some good Nautilus scripts, including how to open a root nautilus browser in the current folder, using a right-click. 
[Helpful Nautilus Scripts]("http://ubuntuforums.org/showthread.php?t=63361")
Check post #4.

---

### Post by 23meg on 2005-12-22
Also check out this trick:

[http://www.ubuntuforums.org/showthread.php?t=24008](http://www.ubuntuforums.org/showthread.php?t=24008)

---

