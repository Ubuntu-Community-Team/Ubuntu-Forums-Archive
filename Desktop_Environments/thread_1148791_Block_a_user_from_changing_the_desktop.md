---
title: "Block a user from changing the desktop"
date: 2009-05-04
forum: Desktop Environments
---

### Post by cchshardware on 2009-05-04
I'm building an ubuntu 8.1 kiosk for work. We had Mandrake (2005?) previously and are users are complaining because they can't get to any of the email sites because Firefox is so outdated and we can't figure out to to get it updated. 
 
I'm not very familier with linux so take it easy on me. Here's my problems:
 
Main Problems is that users can still right click on desktop and change the desktop backround and the theme and font, etc. I would like to remove this option from them. 
 
I'm currently using pessulus to lock down alot of the stuff like the panel. I've also installed FireFox add on webconverger, which works pretty go at least this way they can't right click and set to desktop wallpaper. I still want my users to be able to play games. 
 
Another thing I would like to do is have it so the user can not shut down, restart etc. When mandrake was used you could log off and to shutdown you needed the root password, I would like that with ubuntu.
 
I've tried Sabayon but it keeps crashing.
Any idea's with what I need to do? the wallpaper / theme is the most important.

---

### Post by benerivo on 2009-05-04
I've just tried doing```
gksudo nautilus
```and navigating to /usr/bin/gnome-appearance-properties, and in the permissions tab of this file's properties, i've unticked the 'allow executing file as program' box. Now i can't change any appearance settings.

EDIT - Do this to the gnome-control-center file and you lock out all gnome desktop preferences

EDIT #2 - You might also want to look at this thread [http://ubuntuforums.org/showthread.php?t=1148654](http://ubuntuforums.org/showthread.php?t=1148654) specifically the post by bodhi.zazen

---

### Post by cchshardware on 2009-05-04
that worked Great! now I just need to figure out how to ghost this thing.

---

### Post by benerivo on 2009-05-04
I've lost you there. What do you mean by ghost?

---

### Post by cchshardware on 2009-05-05
Norton/Symantic Ghost, Creates images of the OS. We use ghost for everything and when I try to ghost it takes 1 second and creates a file that's only 6kb, so oviosly something is wrong but I don't know what. Anyone have any ideas?

---

