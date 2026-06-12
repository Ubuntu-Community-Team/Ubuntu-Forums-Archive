---
title: "Colour of background while desktop loads"
date: 2005-05-09
forum: Desktop Environments
---

### Post by rum beverage on 2005-05-09
I was just wondering how I can go about changing the colour of the desktop while gnome is loading.  I know this isn't a huge deal, but those couple seconds of chocolate brown just annoy the hell out of me.

---

### Post by Xian on 2005-05-09
Read about midway down [THIS](http://www.ubuntuforums.org/showthread.php?t=26513) thread for assistance.

---

### Post by Sam on 2005-05-09
[QUOTE=rum beverage]I was just wondering how I can go about changing the colour of the desktop while gnome is loading.  I know this isn't a huge deal, but those couple seconds of chocolate brown just annoy the hell out of me.[/QUOTE]
Open /etc/gdm/gdm.conf and search for "Background":

Set BackgroundType=0 to disable the background
or change the value of BackgroundColor with your favorite color.

---

