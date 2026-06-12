---
title: "adding 'programing' submenu to the main menu"
date: 2005-05-23
forum: Desktop Environments
---

### Post by rjs on 2005-05-23
Gah,

I give up. How do i (re)add the programing submenu to the main (apps) menu? I must have got rid of it at some point, but i cant for the life of me remember how, and now i would like it back again, and cant see anything in the help about it, nor did any of my exploring and right-clicking on things get me anywhere.

thanks in advance,
-rjs

---

### Post by netrattler on 2005-05-23
Do you have menu editor for gnome installed you can simply add it back with that.

Install instructions:
wget -c [http://frankandjacq.com/ubuntuguide/smeg_0.5-0ubuntu1_all.deb](http://frankandjacq.com/ubuntuguide/smeg_0.5-0ubuntu1_all.deb)
sudo dpkg -i smeg_0.5-0ubuntu1_all.deb

Hope this helps
Joe

---

### Post by cutOff on 2005-05-23
[QUOTE=rjs]Gah,

I give up. How do i (re)add the programing submenu to the main (apps) menu? I must have got rid of it at some point, but i cant for the life of me remember how, and now i would like it back again, and cant see anything in the help about it, nor did any of my exploring and right-clicking on things get me anywhere.

thanks in advance,
-rjs[/QUOTE]
You could try to add this menu item by using Smeg

[http://ubuntuforums.org/showthread.php?t=34978&highlight=smeg](http://ubuntuforums.org/showthread.php?t=34978&highlight=smeg)

---

### Post by Sam on 2005-05-23
The submenus are displayed only if items are within them.

Change in any launcher in /usr/share/applications:```
Categories=GNOME;Application;Development;
```and it'll appear in the Programming submenu.

---

### Post by cutOff on 2005-05-23
[QUOTE=Sam]The submenus are displayed only if items are within them.

Change in any launcher in /usr/share/applications:```
Categories=GNOME;Application;Development;
```and it'll appear in the Programming submenu.[/QUOTE]
Oops i didn't know. Thanks for the tip.

---

