---
title: "default settings while there is no xorg.conf"
date: 2005-06-27
forum: Desktop Environments
---

### Post by ^NoX on 2005-06-27
i was playing with the settings and accidently changed xorg.conf into xor**f**.conf
than i wrote "startx" and suddenly the options in the resolution that i wanted was enabled.
the problem is, linux is using some default settings when there is no xorg.conf file, so i don`t have a xorg.conf file - and i need this file.

is there a way to create a new xorg.conf file with these default settings?

thank you very much :-P

---

### Post by dialate on 2005-06-27
You probably saved your work as xorj.conf, but that doesn't make xorg.conf go away. If it was moved, X probably generated a new one for you. In any case, you can do "sudo pico /etc/X11/xorg.conf" and it should be there for you.

---

### Post by ^NoX on 2005-06-27
[QUOTE=dialate]You probably saved your work as xorj.conf, but that doesn't make xorg.conf go away. If it was moved, X probably generated a new one for you. In any case, you can do "sudo pico /etc/X11/xorg.conf" and it should be there for you.[/QUOTE]
 the file is not existent :\

---

### Post by dialate on 2005-06-27
Huh thats pretty wild. I think what you're looking for is /usr/share/xresprobe/xorg.conf. Try 

sudo cp /usr/share/xresprobe/xorg.conf /etc/X11/xorg.conf

then restart X and see what happens. If things dont change, then that would be it.

---

### Post by ^NoX on 2005-06-27
[QUOTE=dialate]Huh thats pretty wild. I think what you're looking for is /usr/share/xresprobe/xorg.conf. Try 

sudo cp /usr/share/xresprobe/xorg.conf /etc/X11/xorg.conf

then restart X and see what happens. If things dont change, then that would be it.[/QUOTE]
 no man it isn`t the file.. its a damaged file.. thanx anyway :)

---

### Post by az on 2005-06-27
I do not know about default setting in the case of a missing config file, but you can create a new xorg.conf by running 
sudo dpkg-reconfigure xserver-xorg


It is best to run this from a console, when X is stopped, as it cannot autodetect hardware while X is running.

sudo /etc/init.d/gdm stop

and

sudo /etc/init.d/gdm start

---

### Post by ^NoX on 2005-06-28
[QUOTE=azz]I do not know about default setting in the case of a missing config file, but you can create a new xorg.conf by running 
sudo dpkg-reconfigure xserver-xorg


It is best to run this from a console, when X is stopped, as it cannot autodetect hardware while X is running.

sudo /etc/init.d/gdm stop

and

sudo /etc/init.d/gdm start[/QUOTE]

thank you! it worked fine :)

---

