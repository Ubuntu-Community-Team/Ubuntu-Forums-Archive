---
title: "Taskbar-System How to change entries"
date: 2005-11-02
forum: Desktop Environments
---

### Post by sherz on 2005-11-02
Hi 

how can I change the entries of the Special Button "System" ?
[IMG]http://sherz.net/screen/kde-system.png[/IMG]

Sherz

---

### Post by Freddy on 2005-11-03
you can find that icon in /usr/share/icons/crystalsvg, remove or rename that icon (for all sizes) and replace it with the choosen icon and rename that one exactly the same as the previous one. You will have to go root for this so use "kdesu konqueror" and browse to the right place.   /// Freddan

---

### Post by sherz on 2005-11-03
[QUOTE=Freddy]you can find that icon in /usr/share/icons/crystalsvg, remove or rename that icon (for all sizes) and replace it with the choosen icon and rename that one exactly the same as the previous one. You will have to go root for this so use "kdesu konqueror" and browse to the right place.   /// Freddan[/QUOTE]

No sorry I dont want change the icon I want change the entries e.g. instaed of Settings /home/sherz/download 

Stephan

---

### Post by Freddy on 2005-11-03
Sorry but I don't really understand what you want to do, entries for what? Do you want to make a entrie for example /media/flubdrive, or? If you explain exactly what you want to do, maybe I or someone else are able to help.   /// Freddan

---

### Post by sherz on 2005-11-03
[QUOTE=Freddy]Sorry but I don't really understand what you want to do, entries for what ? If you explain exactly what you want to do, maybe I or someone else are able to help.   /// Freddan[/QUOTE]

Ok I will change the entries to customize. For example it should looks like:

-Home Folder
-Pictures
-Work
-Sport
-Storage Media
-Trash ....

Do you know what I mean ?

Stephan

---

### Post by Freddy on 2005-11-03
Yes I understand what you want, tried to find some kind of config file to hack but found nothing. Hopefully someone else know or can figure out how to configurate the systembutton.   /// Freddan

---

### Post by Zyphrexi on 2005-11-04
SMEG anyone?


Of course a fun thing to do would just to create a new menu, then link those desired folders to created entries. That's what i usually do.

---

### Post by sherz on 2005-11-04
[QUOTE=Zyphrexi]SMEG anyone?


Of course a fun thing to do would just to create a new menu, then link those desired folders to created entries. That's what i usually do.[/QUOTE]

Oh thanks for the tip. It was so esay I had just to create a new own menu.

Thx

Stephan

---

### Post by jyhelle on 2005-11-04
Stefan,
You should use your preferred editor to have a look at the .desktop files that reside in /usr/share/apps/systemview ...

cheers,
JL

---

### Post by Zyphrexi on 2005-11-05
np, kde is pretty handy that way. You'll get used to it. :D

btw if you want to change the icon so it looks like it stands out (even change it to a system icon) right click the icon, configure, then in the general tab, just click the picture, and you can pick from a nice list of pretty icons. As a general rule, i try to stay away from modifying default thingamajiggers. Then later when you decided that wasn't the greatest idea in the world, or someone refers to a certain location, you aren't left totally clueless. (though it's really not TOO hard to restore the menus)

---

