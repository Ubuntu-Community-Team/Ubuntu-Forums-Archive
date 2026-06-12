---
title: "turning compiz off"
date: 2007-12-21
forum: Desktop Effects &amp; Customization
---

### Post by Intuvati on 2007-12-21
ok, so i have two little icons on my "ubuntu bar" at the top of my desktop, one is for turning compiz on, the other is for turning compiz off. but, when i turn compiz off, my entire system is extremely laggy and i cant play my games ( the reason i turned compiz off in the first place), and i cant pay them with compiz turned on just simply because it takes too much computing power. is there a way to turn compiz off without having my comp so laggy? it so bad that even typing text takes a few seconds for the text to appear...

---

### Post by tgilber1 on 2007-12-21
Remove compiz packages.  You can find out what compiz packages you have by typing the following:

dpkg -l *compiz*

Then, type "sudo apt-get remove <installed compiz files listed by dpkg -l"

ex.  "sudo apt-get remove compiz"

Next, make sure that metacity is installed and your current and default window manager

dpkg -l metacity

if not installed, type "sudo apt-get metacity"

Next, change the default and current window manager by using gconftool-2

gconftool-2 --set --type string /desktop/gnome/applications/window_manager/current metacity

gconftool-2 --set --type string /desktop/gnome/applications/window_manager/default metacity

You can verify that the settings took by the following command:

gconftool-2 --get /desktop/gnome/applications/window_manager/default 
gconftool-2 --get /desktop/gnome/applications/window_manager/current

Finally, log out system and log back in; window manager should now be metacity.

---

### Post by tgilber1 on 2007-12-21
Made a minor error on the previous post with the sudo apt-get command to install metacity.  It should have read like the following:

if not installed, type "sudo apt-get install metacity"

---

### Post by Intuvati on 2007-12-21
oh yeah, forgot to mention that i only want to disable it temporarilly, and only when i'm playing my game. that way, if i click the "compiz on" button, i can go back to having a nice desktop

---

### Post by santaslittlehelper on 2007-12-21
Hi, not sure, but can't you just use System > Appearance > Visual Effects, then choose None: ?
Otherwise how about "metacity --replace" from terminal.

---

### Post by Intuvati on 2007-12-21
nope, sorry, but same laggyness as efore -  and metacity --replace was how i was turning it off in the first place. i think i'm just going to get rid of compiz completely and just have a normal desktop, because i tried even logging out and using a different session (fluxbox, etc) and it was still laggy. i guess i'll just wait until i get a new comp, one that can have both compiz AND games. thanks for your help, though. really appreciate it. :D

---

