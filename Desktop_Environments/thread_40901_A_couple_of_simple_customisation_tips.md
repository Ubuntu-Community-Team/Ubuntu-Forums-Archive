---
title: "A couple of simple customisation tips?"
date: 2005-06-10
forum: Desktop Environments
---

### Post by [censored] on 2005-06-10
1) How can I fix it so numlock is on when I boot up? It was on by default when I used mandrake, ubuntu seems to have it off by default.

2) How can I tell gnome to load certain apps/utilities on start up? For e.g, I use Klipper, a little clipboard manager that lives in the system tray. Would be nice if I didn't have to manually boot it every time I entered gnome.

---

### Post by bored2k on 2005-06-10
1) sudo apt-get install numlockx (from a terminal)

2) System > sessions > startup programs > add

---

### Post by vassalle on 2005-06-10
[QUOTE='[censored]']1) How can I fix it so numlock is on when I boot up? It was on by default when I used mandrake, ubuntu seems to have it off by default.

2) How can I tell gnome to load certain apps/utilities on start up? For e.g, I use Klipper, a little clipboard manager that lives in the system tray. Would be nice if I didn't have to manually boot it every time I entered gnome.[/QUOTE]
 hi there.. heres some simple solutions..

1) [http://ubuntuguide.org/#numlockx](http://ubuntuguide.org/#numlockx)

2)go to System>Preferences>Sessions>Startup Programs Tab -> Add/Edit/Delete
   eg. for gdesklets 
   startup command: gdesklets start
   order: 50

hope it helps.. :D

darn u beat me to it!  ;-)

---

### Post by bored2k on 2005-06-10
[QUOTE=vassalle]darn u beat me to it!  ;-)[/QUOTE]
It's like the wild wild west in here ;). "Be fast, be steady, be vigilant!" (Kiwinz sig)

---

