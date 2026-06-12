---
title: "Adding gkrellm to the Debian menu?"
date: 2005-07-31
forum: Desktop Environments
---

### Post by erik-the-red on 2005-07-31
I have installed gkrellm via synaptic.

How do I add it to the Debian menu?

---

### Post by kosmic on 2005-07-31
The best way to add/remove aplication from the Gnome menu is to use SMEG - just do apt-get install Smeg

---

### Post by erik-the-red on 2005-07-31
[QUOTE=kosmic]The best way to add/remove aplication from the Gnome menu is to use SMEG - just do apt-get install Smeg[/QUOTE]
 Does smeg also work for fluxbox, openbox, enlightenment, and so forth?

I don't actually use GNOME that often anymore since my 128mb-equipped system is poor for handling its monstrous needs.

---

### Post by Magneto on 2005-07-31
[QUOTE=erik-the-red]Does smeg also work for fluxbox, openbox, enlightenment, and so forth?

I don't actually use GNOME that often anymore since my 128mb-equipped system is poor for handling its monstrous needs.[/QUOTE]
 you can just edit the xml file that the debian menu uses

what wm are you using? the menu locations for different WMs vary, if you'd just like to add gkrellm to your general menu

check /var/lib/menu-xdg/menus/debian-menu.menu will show you how they use xml to create the menus
look in the other directories in /var/lib/menu-xdg for more answers

smeg will let you add it to debian-menu

i can provide alot of links to customizing openbox and other wm menus - there's a whole lot of things you can do with them

---

### Post by erik-the-red on 2005-07-31
[QUOTE=Magneto]you can just edit the xml file that the debian menu uses

what wm are you using? the menu locations for different WMs vary, if you'd just like to add gkrellm to your general menu

check /var/lib/menu-xdg/menus/debian-menu.menu will show you how they use xml to create the menus
look in the other directories in /var/lib/menu-xdg for more answers

smeg will let you add it to debian-menu

i can provide alot of links to customizing openbox and other wm menus - there's a whole lot of things you can do with them[/QUOTE]
 I use openbox because for some reason fluxbox has this lag when it starts up which openbox does not.

---

### Post by Magneto on 2005-07-31
[QUOTE=erik-the-red]I use openbox because for some reason fluxbox has this lag when it starts up which openbox does not.[/QUOTE]
 most of my links for openbox menu scripts are dead- they are a lil bit old

I use openbox too(but I mainly use gnome) so if you want to do something beyond the debian menu and smeg and you don't get the use of the file I mentioned let me know and I can provide some direct instructions

smeg will allow you to change it fast with no learning

---

### Post by erik-the-red on 2005-08-01
[QUOTE=Magneto]most of my links for openbox menu scripts are dead- they are a lil bit old

I use openbox too(but I mainly use gnome) so if you want to do something beyond the debian menu and smeg and you don't get the use of the file I mentioned let me know and I can provide some direct instructions

smeg will allow you to change it fast with no learning[/QUOTE]
 For some reason gkrellm showed up by itself. It took some time, but I didn't do anything; it's there now in the system submenu.

Thanks anyway!

---

