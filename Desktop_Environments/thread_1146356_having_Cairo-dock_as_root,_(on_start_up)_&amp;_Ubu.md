---
title: "having Cairo-dock as root, (on start up) &amp; Ubuntulooks"
date: 2009-05-02
forum: Desktop Environments
---

### Post by ElevenWarrior on 2009-05-02
hey, I'm running 9.04, and I need to run Cario-dock as root, when the system starts up. right now I've added it to the startup app's, (command sudo cairo-dock) but all it does it start terminal. also, I have a different Icon theme for gnome than it shows in Cairo-dock. (meaning, I click on the gmenu icon, and the icons it shows are just the default. is there a way to change this?)
also, what is ubuntulooks? is it worth installing?

---

### Post by ElevenWarrior on 2009-05-02
also, I can't change any of my themes, when I try I get this error..
warning :  (cairo-dock-themes-manager.c:cairo_dock_get_theme_path:733)  
  couldn't retrieve distant theme Tux_n_Tosh : an error occured while executing ' wget "http://themes.cairo-dock.org//Tux_n_Tosh/Tux_n_Tosh.tar.gz" -O "/tmp/cairo-dock-net-file.z9NDNJ" -t 2 -T 3'
on_theme_apply: assertion `cNewThemePath != NULL' failed
on_click_normal_quit ()
on_delete_normal_gui ()

---

### Post by ElevenWarrior on 2009-05-02
I've fixed the start with  Ubuntu problem I just can't install any more themes
....

---

### Post by ElevenWarrior on 2009-05-03
sorry everyone....bump.
I still need,
1. Starting cairo-dock
2. how to change themes.

---

### Post by fabounet on 2009-05-04
install Cairo-Dock2
then, in the menu -> System, select the one that fits your machine.

right-click -> cairo-dock -> theme manager

---

### Post by ElevenWarrior on 2009-05-04
I did that. nothing happens. I ran it in the terminal and this is what I get..

warning : (cairo-dock-themes-manager.c:cairo_dock_get_theme_path:733)
couldn't retrieve distant theme Tux_n_Tosh : an error occured while executing ' wget "http://themes.cairo-dock.org//Tux_n_Tosh/Tux_n_Tosh.tar.gz" -O "/tmp/cairo-dock-net-file.z9NDNJ" -t 2 -T 3'
on_theme_apply: assertion `cNewThemePath != NULL' failed
on_click_normal_quit ()
on_delete_normal_gui ()

---

### Post by fabounet on 2009-05-05
what gives "cairo-dock --version" ?
with the RC5 it works.

---

