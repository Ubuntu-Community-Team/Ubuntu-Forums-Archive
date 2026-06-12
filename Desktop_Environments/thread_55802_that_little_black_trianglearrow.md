---
title: "that little black triangle/arrow"
date: 2005-08-10
forum: Desktop Environments
---

### Post by hunteramor on 2005-08-10
i've replaced the gnome foot with the ubuntu logo for the main menu/menu bar, and it looks great.  however, when i tried to save panel space by replacing the menu bar with the main menu, an incredibly irritating little black triangle/arrow is superimposed on the logo.  does anyone know how to get rid of this?

(example attached, with panel blown up to make it easy to see - lower left corner)

---

### Post by Mateo on 2007-02-14
curious about this too.

---

### Post by Mateo on 2007-02-14
never mind, figured it out.  anyone who's curious, download the gnome-panel source code, and comment out the part about the arrow in the panel-button.c file, then ./configure, make, sudo make install.  You do have to download several dev packages to get it to configure, though.  Worth it, I think.

---

### Post by b0rka7a on 2007-12-28
First type:
```
cd ~/
apt-get source gnome-panel
```
Do not close the terminal.
Then extract the archive "gnome-panel_2.20.1.orig.tar.gz" which is in your home directory. After that go back to the terminal and type:
```
gedit gnome-panel-2.20.1/gnome-panel/panel-menu-button.c
```
Find the line:
```
...
"has-arrow", TRUE,
...
```
and change it to:
```
/* "has-arrow", TRUE, */
```
Save and exit...

Type:
```
cd gnome-panel-2.20.1
./configure && make
sudo make install
```
When the install finish type:
```
killall -9 gnome-panel
```
You're done! :)

---

### Post by alamarco on 2008-01-27
Thanks for providing the instructions. It worked perfectly once I had all the depenencies installed. I must say, there was a ton of dev files needed to be installed.

---

