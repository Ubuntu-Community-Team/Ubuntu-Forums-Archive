---
title: "Fluxbox"
date: 2005-05-10
forum: Desktop Environments
---

### Post by stevenyu on 2005-05-10
I really want to get fluxbox working on my system.  I have succesfully installed the package via apt-get, however there is no menu editor when I right click on the desktop, is there a how to on getting fluxbox working in ubuntu?

---

### Post by kvidell on 2005-05-10
[QUOTE=stevenyu]I really want to get fluxbox working on my system.  I have succesfully installed the package via apt-get, however there is no menu editor when I right click on the desktop, is there a how to on getting fluxbox working in ubuntu?[/QUOTE]
 Menu editor?
```
vim ~/.fluxbox/menu
``` :)
- Kev

---

### Post by stevenyu on 2005-05-10
Any GUI method?

---

### Post by Brunellus on 2005-05-10
[QUOTE=stevenyu]Any GUI method?[/QUOTE]
 nope, sorry.  Fluxbox is lightweight because it doesn't go very many things from the GUI...

---

### Post by kosmic on 2005-05-10
I think fluxbox doesn't have a gui for editing, the only way is by command line

---

### Post by pietro_spina on 2005-05-10
try "fluxconf" it is in the universe repository I think.  I've used it in the past, it has an odd behaviour or two... (back when I was using a straight Debian install) I found it to be easier to maintain my own Menu file and by pointing the fluxbox configuration file at my custom menu and using "update-menus" to update the standard file. Makes it easy to maitain if you go wild installing various programs someday...

p

---

### Post by kvidell on 2005-05-10
[QUOTE=stevenyu]Any GUI method?[/QUOTE]
 ```
gedit ~/.fluxbox/menu
```Without using Fluxconf (a la peitro_spina's suggestion), the best you can get is a gui based text editor.
hehe ;P
- Kev

---

### Post by h2gofast on 2005-05-10
are you sure you're in fluxbox when you logged in?  You must select fluxbox from the session drop down.

---

### Post by thierry on 2005-05-11
Make sure you have this file on your system :

[http://svn.berlios.de/viewcvs/fluxbox/trunk/util/fluxbox-generate_menu.in]("http://svn.berlios.de/viewcvs/fluxbox/trunk/util/fluxbox-generate_menu.in")

To install type :

 ```
sudo install -m755 fluxbox-generate_menu.in /usr/local/bin/fluxbox-generate_menu
``` 

The command fluxbox-generate_menu will automatically generate a complete menu file in your ~/.fluxbox folder !

Good luck. Fluxbox is great, but you might have to google a bit to get it to work just the way you want it !

---

### Post by tread on 2005-05-11
That script is very useful, thanks a lot!

---

### Post by az on 2005-05-11
[QUOTE=stevenyu]I really want to get fluxbox working on my system.  I have succesfully installed the package via apt-get, however there is no menu editor when I right click on the desktop, is there a how to on getting fluxbox working in ubuntu?[/QUOTE]

Do you mean that you have no menu or that you cannot edit the menu?

Installing the menu package gives you a menu.

---

### Post by nicholaspaul on 2005-12-10
[QUOTE=thierry]Make sure you have this file on your system :

[http://svn.berlios.de/viewcvs/fluxbox/trunk/util/fluxbox-generate_menu.in]("http://svn.berlios.de/viewcvs/fluxbox/trunk/util/fluxbox-generate_menu.in")

To install type :

 ```
sudo install -m755 fluxbox-generate_menu.in /usr/local/bin/fluxbox-generate_menu
``` 

The command fluxbox-generate_menu will automatically generate a complete menu file in your ~/.fluxbox folder !

Good luck. Fluxbox is great, but you might have to google a bit to get it to work just the way you want it ![/QUOTE]


This answered my question. When I installed fluxbox (including all the other things that searching for 'flux' in synaptic showed) I had three things in the right-click menu. This script adds a whole menu. Very cool!

---

### Post by ardchoille on 2005-12-10
There is a gui menu editor for fluxbox that is written in python. The app is called fluxmenu but I can't seem to find the homepage for it.

---

### Post by nicholaspaul on 2005-12-11
Fluxmenu is in the repositories. That is the menu that, by default, only gives you three options: Terminal, restart and exit, if I rememeber correctly. The script mentioned above populates that menu with the stuff you have installed- or it my go by the Gnome menu, I'm not sure, but it also includes configuration options for the menu.

---

