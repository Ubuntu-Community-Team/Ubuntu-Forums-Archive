---
title: "Emerald, Compiz-Fusion, Gnome, AVN"
date: 2009-07-22
forum: Desktop Environments
---

### Post by geudrik on 2009-07-22
I'd still consider my self a fairly novice uBuntu user.  
I've recently reinstalled ubunto on my laptop and have installed:

Avant Window Navigator
Emerald
Compiz-Fuzion
and have the GNOME environment

But, nothing seems to be working quite right... AVN is working as it should (soooo... I lied), Emerald works (sorta) if I run:
```
 emerald --restart
``` 
but I have no top to my windows (no title bar, or buttons on the right).  Compiz-Fusion sorta works, but is clearly not integrated all that well into GNOME and Emerald doesnt work at all unless I force it, but that bbreaks the other programs (minus AVN)

So, how do I get Emerald, Compiz-Fuzion and GNOME to all work like peas in pod happily together? :)

Sidenote: After I installed these four apps, System -> Preferences -> Sessions dissapeared from the list (hence, I can't add a session for Emerald...  How do I get Sessions back? :)

---

### Post by ajgreeny on 2009-07-22
First try a different theme as some work much better with compiz and emerald than others.  I use [**ddragon's blue**]("http://api.compiz-themes.org/usermanager/search.php?username=ddragon&action=contents&PHPSESSID=e6157d163a4276be6f0ed887bf693462"), big and small versions are available, and both work well on my old system with an ati 9200SE card

---

### Post by realzippy on 2009-07-22
Hi,
in CCSM go to Window Decoration,and type a command:

        emerald --replace

and restart the xserver...

---

### Post by VCoolio on 2009-07-22
Have a look at fusion-icon; it will run as an icon in your systray and right clicking will provide options for easily switching window manager and window decorator.

---

