---
title: "gnome start menu question"
date: 2007-04-09
forum: Desktop Environments
---

### Post by serialdae on 2007-04-09
Can gnome display the recently run programs like KDE on the start menu?

---

### Post by quux on 2007-04-09
Maybe "gnome-main-menu" suits your needs. It supports both favorite applications and recent documents. The package can be installed via apt-get/synaptic. After installation, just add the new "Main Menu" applet to the gnome panel.

---

### Post by serialdae on 2007-04-09
That is the menu I have been using but I do not see anywhere to add Favorite applications or recent documents

how do you do this?

---

### Post by quux on 2007-04-09
Try clicking on "More Applications...", then right-click on the application to be added to the favorites and choose "Add to favorites".

---

### Post by serialdae on 2007-04-09
All I get is 
     
      Add this launcher to panel
      Add this launcher to desktop
                Entire menu
                         Add this as drawer to panel
                         Add this as menu to panel

I am on Ubuntu 6.10 maybe my menu is older or something

I did see the recent documents buried under places.
I also notice that system, places and add remove are not listed when I try to edit the menus

---

### Post by quux on 2007-04-09
Ah... I see, you're using the standard gnome main menu. If you do a "sudo apt-get install gnome-main-menu", a new "Main Menu" applet will be available. This is the one I was referring to. It's part of the "universe" repository.

Strangely, both "Main Menu" applets have the same name. :/

---

### Post by serialdae on 2007-04-09
Broken packages  -  :confused: 


gnome-main-menu: Depends: libdbus-1-2 (>= 0.60) but it is not installable
E: Broken packages

---

