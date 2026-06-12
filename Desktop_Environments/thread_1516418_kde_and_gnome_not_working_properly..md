---
title: "kde and gnome not working properly."
date: 2010-06-23
forum: Desktop Environments
---

### Post by intermediatech on 2010-06-23
i have an ubuntu 10.04 installation. i installed kde. i use screenlets in gnome. i place all the screenlets in place and lock them one by one in properties window. setted the screenlets to autostart. when logon to kde the screenlet is displayed at the top left corner. then when i log back to gnome they appear on top left corner. 
i want screenlets to start in gnome only.

installed compiz in gnome. it is working smoothly. but in kde no effects are working.

what should i do now ? pls help 

i don't know the correct version of kde. but i am using uptodate version. updated yesterday.

---

### Post by kornfan71 on 2010-06-23
I just found this one out today. For the screenlets problem, go to ~/.config/autostart, and edit the ".desktop" file for screenlets, most likely "screenlets.desktop." (You can use gedit or Kate, or any other text editor.)
Add this line:
```
OnlyShowIn=GNOME;
```AFAIK, that can go anywhere in the file.

I'm still working on getting Compiz and KDE playing nice, but if I figure that one out, I'll let you know. :D

---

