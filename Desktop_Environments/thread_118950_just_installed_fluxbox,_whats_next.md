---
title: "just installed fluxbox, whats next?"
date: 2006-01-18
forum: Desktop Environments
---

### Post by D1G1T4L on 2006-01-18
i just installed it, and it seems its just an empty screen (no taskbar even)
however when i right click, it shows applications menu etc

i installed a a few dockapps with apt-get install

how do i run them though? what program should i use to execute the dockapps + modify them?

---

### Post by encompass on 2006-01-18
have you installed ubuntu with gnome... sounds like your are pretty new, if so... stick with gnome.  or read up on your environment that you are in by going to their homepage.

---

### Post by D1G1T4L on 2006-01-18
[QUOTE=encompass]have you installed ubuntu with gnome... sounds like your are pretty new, if so... stick with gnome.  or read up on your environment that you are in by going to their homepage.[/QUOTE]


yea i did

i just got the toolbar by making it visible in config menu

now i wanna learn how to install + display dockapps

also is there a way to show icons on the desktop etc

---

### Post by [Rui] on 2006-01-18
[QUOTE=D1G1T4L]also is there a way to show icons on the desktop etc[/QUOTE]

Type "nautilus&" on an xterm or another terminal emulator.

---

### Post by ardchoille on 2006-01-18
you can have the dockapps appear by running them from a terminal. For instance the wmbinclock dockapp can be run with 
```

wmbinclock &

```

The "&" allows the app to run while allowing you to close the terminal. wmbinclock should appear wherever your dock is.

---

### Post by D1G1T4L on 2006-01-18
thank you guys

is there a way i can get a list of docks i already have installed on my system?

also how do i edit settings of dockapps

for example dockapp for weather, i wanna edit it to display my city's weather, etc

---

### Post by D1G1T4L on 2006-01-19
[QUOTE=D1G1T4L]thank you guys

is there a way i can get a list of docks i already have installed on my system?

also how do i edit settings of dockapps

for example dockapp for weather, i wanna edit it to display my city's weather, etc[/QUOTE]


anyone?

---

### Post by newuser111 on 2006-01-19
use fbdesk to create desktop icons in fluxbox, its available from synaptic if its not already installed

[http://fluxbox.sourceforge.net/fbdesk/](http://fluxbox.sourceforge.net/fbdesk/)

to get a list of dockapps you can install try apt-cache search dock app | grep wm

---

### Post by D1G1T4L on 2006-01-19
[QUOTE=newuser111]use fbdesk to create desktop icons in fluxbox, its available from synaptic if its not already installed

[http://fluxbox.sourceforge.net/fbdesk/](http://fluxbox.sourceforge.net/fbdesk/)

to get a list of dockapps you can install try apt-cache search dock app | grep wm[/QUOTE]

i have installed fbdesk but i dont understand how do i make it so when i double click on the icon, it opens lets say a ~/home/desktop folder

---

