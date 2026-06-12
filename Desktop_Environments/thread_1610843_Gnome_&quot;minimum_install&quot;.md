---
title: "Gnome &quot;minimum install&quot;?"
date: 2010-11-01
forum: Desktop Environments
---

### Post by camurgo on 2010-11-01
I'm about to install Gnome on my ubuntu server box (that means, a headless server which I'm gonna access through vnc)

I usually just run "apt-get install gnome"

But it installs a bunch of stuff I'm not going to use (email, office, games, etc..). All I need is the most basic environment to allow me running programs and their GUIs (browsers, custom software etc), and access it with vnc

How do I procced so I have the lightest gnome install possible?


ps: That's what I want to do, install gnome and access it through vnc. I'm aware of the number of other options I have. :)

---

### Post by stars on 2010-11-01
you can use: gnome-core --no-install-recommends 
you will probably want a login manager such as gdm too

---

### Post by camurgo on 2010-11-03
Thanks, but that didn't work quite well. A number of needed packages to run this and that seem to be missing.

I'll try a couple more things and then I'll give in and install gnome full..

---

