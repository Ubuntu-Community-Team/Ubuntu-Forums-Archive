---
title: "multple X servers ctrl + alt + f1-f7"
date: 2006-01-09
forum: General Help
---

### Post by oly on 2006-01-09
hi just curious is it possible to launch different desktops from the terminals, 
in other words have gnome running on ctrl + alt + f7, but run kde at the same time on ctrl + alt + f6, and then attache xfce to ctrl + alt + f5.

i know this woudl use resources but have always been curious if you can and how, i get the feeling you can but have to setup different numbered screens or something.

any info on doing this ????

---

### Post by netkid91 on 2006-01-09
I know in KDE you can use the 'start new session' option in the K menu to open a new X session, lemme boot into Ubuntu so I can check on GNOME.

---

### Post by Dr. Nick on 2006-01-09
Gnome has the option aswell somewher in its menus to, Its called "New Login" I believe. This only last until a restart though, after that your back to one xorg display

---

### Post by akudewan on 2006-01-10
You can use *gdmflexiserver* This is the program invoked by gnome.

Edit: you can also login in a nested window. Use *gdmflexiserver -n* for it

---

### Post by lamego on 2006-01-10
You can start a second X session without a GUI tool, from a text console:
startx -- :1
This will start a new WM on display :1 .

---

