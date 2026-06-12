---
title: "[Script for Xfce] Edit and autoupdate the menu"
date: 2007-11-22
forum: Desktop Environments
---

### Post by Coolaman on 2007-11-22
Sorry for my language, i'm french. 

I made a script for edit the xfce menu ( deploy all the name and remove the one line "inclusion" and "system" ) and auto update this menu when you install or remove programs.

- Work with synaptic, apt-get , aptitude
- The new entry are every time in top of them own category.
- Work for english and french .
- Original menu is in /home/yourlogin/.config/xfce4/desktop with menu.orig.xml name
- If application don't have category then add a "Other" menu
- Edit the script to see how to translate in other language and remove the automatization of the script.

The script : [AutoMenu](http://coolaman.free.fr/Divers/AutoMenu.tar.bz2) 

Add it to autostarted applications folder. You must first edit your menu one time to create the file 'menu.xml' ( script need this to work )

[I]Edit : this script work with /usr/share/applications but not in the directory inside it.

[/I]

---

### Post by Telecaster72 on 2007-11-22
Great i was missing this in xfce.
Thanks a lot!

---

### Post by Telecaster72 on 2007-11-23
After installing some apps (Avidemux, DeVeDE, Blender, DidiWiki, RipperX) through Synaptic, they do not show up in the menu.
However creating a launcher with your script is a breeze since it automatically opens in usr/bin and finding the icon is really easy since just pressing the icon button opens a really nice "icon browser"
...but for me, they do not come up in the menu automatically...
This thing is really nice though, it should come as default in the next Xfce version.

---

### Post by Coolaman on 2007-11-24
Sorry but i have made a mistake with translation. Now it work for me, prehaps for you. I update the file.

With space in the name, there 's still a little bug when you remove the program . I work on it.

---

### Post by Telecaster72 on 2007-11-24
It works fine for me now.

Merci Beaucoup:)

---

### Post by Coolaman on 2007-11-27
Update of the script :

- fixed small bug

- Add a how to to translate this script and how to delete automatization ( in the script itself)

---

### Post by Coolaman on 2007-12-02
Update of the script :

- fixed small bug
- Add menu "other" if application don't have category

---

### Post by Coolaman on 2008-05-11
Update of the script to remove some bugs

---

### Post by Coolaman on 2008-06-18
Update to remove few bugs.

---

