---
title: "gnome application menu shows no applications"
date: 2008-12-09
forum: General Help
---

### Post by rekahsoft on 2008-12-09
Hi all...i recently converted a friend to linux and for some odd reason his "Applications" part of the gnome-panel (specifically both ubuntu menu applets) show no application..a small square box comes up and thats it...i have tried reinstalling gnome-panel, gnome-panel-data, gnome-applets, and gnome-applets-data. I don't know where the information for the application menus comes from..i would assume either a light end database, xml files (which is my first guess) or some text file....could they have been corrupted? has any other had any issue like this? Thanks :P

---

### Post by bapoumba on 2008-12-09
Deleted two identical threads.
Check the theme and the fonts used. I may just be a display problem.
Also try to run
```
sudo apt-get update
sudo apt-get dist-upgrade
```
I've seen similar problems due to an incomplete upgrade (dist-upgrade checks for deps more carefully than a regular upgrade).

---

### Post by mc4man on 2008-12-09
If you are referring to the Applications drop down on the upper left panel not working then go to home folder -> view -> "show hidden files" -> .config -> menus and delete applications.menu

Note: there is no harm deleting this file, will be rebuilt as soon as you click on Applications in your panel

---

### Post by rekahsoft on 2008-12-10
Already tried changing the theme...no go..but as for deleting /home/username/.config/menus/applications.menu all went well :D thanks

---

