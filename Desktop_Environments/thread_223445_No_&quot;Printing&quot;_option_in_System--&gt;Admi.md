---
title: "No &quot;Printing&quot; option in System--&gt;Administration"
date: 2006-07-26
forum: Desktop Environments
---

### Post by djaya2 on 2006-07-26
I switched from KDE to Gnome this morning and have encountered more than a few hiccups.  The most recent:  I need to set up my printer.  The Ubuntu Guide says to go to System-->Administration-->Printing.  But "Printing" isn't on my System-->Administration menu.  Any help?

---

### Post by shawnrgr on 2006-07-26
Accessories>Alacarte Menu Editor>System>Administrator> [x] Printing

---

### Post by djaya2 on 2006-07-26
It's not there.  I think something didn't install properly (even though I've reinstalled gnome-desktop).  Lots of things, actually.  For example, synaptic---I had to 'sudo apt-get install synaptic'.  My guess is that I have to install Gnome's default printer service or something like that, but I don't know what it is.

---

### Post by shawnrgr on 2006-07-26
run in terminal: sudo gnome-cups-manager

if you don't have it: sudo apt-get gnome-cups-manager
then crt-alt-backspace, login, check the menu for the icon, still not their look in the menu editor, and if its not in their, just add it to the menu: the command to launch it is gnome-cups-manager

---

### Post by djaya2 on 2006-07-26
Thanks, that was it.  I had installed a bunch of printing-related stuff, including some cups stuff, but not gnome-cups-manager.

---

