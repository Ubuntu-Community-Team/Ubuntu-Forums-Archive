---
title: "Extraction not performed  You don't have the right permissions to extract archives in"
date: 2009-06-15
forum: General Help
---

### Post by suffery on 2009-06-15
Extraction not performed

You don't have the right permissions to extract archives in the folder "file:///usr/share/gnome-screensaver"


i have done tryed gksudo nautilus
it opened root..

but didnt allow me to extract or even move anything to the folder
i do NOT want to enter as gui root :)
any terminal comands?

---

### Post by suffery on 2009-06-15
bump

---

### Post by ActiveFrost on 2009-06-15
```
cd /usr/share/gnome-screensaver && sudo unzip /home/user/yourarchive
```
** replace *yourarchive* with what you want to extract.

---

### Post by Legace on 2009-06-15
Why don't you extract the files to your desktop, then **gksudo nautilus** and copy-paste the files into /usr/share/gnome-screensaver :)

---

