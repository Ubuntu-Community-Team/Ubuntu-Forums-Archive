---
title: "Qk: Gtk?"
date: 2005-04-22
forum: Desktop Environments
---

### Post by coldturkey on 2005-04-22
I downloaded some themes and stuff from gnome-look.org but I didn't what to download so I downloaded one thing from every genre (?).
I downloaded GTK 1x and 2x themes, now;
Will these work with Gnome that comes with Ubuntu 5.04?
And if, how do I install these .bz2 packages?

Thanks in advance!

---

### Post by domesticatewhat on 2005-04-22
You need the Gtk2. Then go to system --- preferences ---themes then click on install theme and browse to where you downloaded it.

---

### Post by coldturkey on 2005-04-22
[QUOTE=domesticatewhat]You need the Gtk2. Then go to system --- preferences ---themes then click on install theme and browse to where you downloaded it.[/QUOTE]

Thanks! 
Btw, is GTK2 installed or do I have to get it from Synaptics?

Edit; Got it now.. Btw, how do I install splaschscreen and GDM? And icons?

---

### Post by domesticatewhat on 2005-04-22
Icons -

go the menu where you install themes. Click on theme details then click on the icons DONT install via this menu click on go to theme folder and extract the icon folder there.

splash screen -

To change the splash screen, put the downloaded image in an unobtrusive location (since it will need to remain there as long as you want it to be the splash screen). A logical location would be ~/.gnome/splash.png (or .jpeg if the image is a JPEG). Then, edit the GConf key /apps/gnome-session/options/splash_screen using the Configuration Editor (Panel menu->System Tools->Configuration Editor) or the commandline tool gconftool-2.

A useful site for faq on installing themes is - [http://art.gnome.org/faq.php](http://art.gnome.org/faq.php)

---

### Post by coldturkey on 2005-04-22
[QUOTE=domesticatewhat]Icons -

go the menu where you install themes. Click on theme details then click on the icons DONT install via this menu click on go to theme folder and extract the icon folder there.

splash screen -

To change the splash screen, put the downloaded image in an unobtrusive location (since it will need to remain there as long as you want it to be the splash screen). A logical location would be ~/.gnome/splash.png (or .jpeg if the image is a JPEG). Then, edit the GConf key /apps/gnome-session/options/splash_screen using the Configuration Editor (Panel menu->System Tools->Configuration Editor) or the commandline tool gconftool-2.

A useful site for faq on installing themes is - [http://art.gnome.org/faq.php](http://art.gnome.org/faq.php)[/QUOTE]


Wow, thanks alot for the help ;)

Edit; I tried it, everything works exccept the ikons :( I've tried several times... Still won't work :/

---

