---
title: "Home Folder Icon Location"
date: 2007-04-03
forum: Desktop Effects &amp; Customization
---

### Post by shiznatix on 2007-04-03
Ok so I am trying to add a link to my home folder on a panel but I can not find where the home folder icon is located. Can someone help me out please.

---

### Post by reclusivemonkey on 2007-04-04
If you make a link to /home/*your username* it should automatically use the default icon for your theme.

---

### Post by shiznatix on 2007-04-04
Nope. I right click on the panel -> add to panel -> custom application launcher -> set type to "file" and location /home/shiznatix/ and click "OK". The icon that gets put on the panel is the yellow diamond with a question mark in the middle. It works just fine but I would much perfer a better looking icon

---

### Post by reclusivemonkey on 2007-04-04
> **shiznatix said:**
> Nope. I right click on the panel -> add to panel -> custom application launcher -> set type to "file" and location /home/shiznatix/ and click "OK". The icon that gets put on the panel is the yellow diamond with a question mark in the middle. It works just fine but I would much perfer a better looking icon

Try dragging and dropping the home icon to your panel. Alternatively you can choose an icon yourself by right clicking and choosing preferences. You can then choose your own icon. The default icons are stored in /usr/share/icons (I think, I am at work right now). Depending on which icon theme you are using, the home icon will be in the relevant folder in "Places".

---

### Post by maxamillion on 2007-04-04
/usr/share/icons/ is where the default icons are ... if you are running Xubuntu, the icons are in the Tango directory within the /etc/share/icons/ and if you are running Ubuntu the icons are in either Human or gnome directory in /etc/share/icons/ 

though if you added an icon theme ... it would depend on where you put it ... hope that helps

---

### Post by shiznatix on 2007-04-04
Ok I got it. It was in /usr/share/icons/Human/scalable/places/

I think its kinda silly that I can go to the menu and right click on anything and add it to the panel EXCEPT anything in the 'Places' section. Why can't I add a place to my panel? When I right click on any 'place' it just opens the place, no options or anything.

---

### Post by reclusivemonkey on 2007-04-04
> **shiznatix said:**
> Ok I got it. It was in /usr/share/icons/Human/scalable/places/

I think its kinda silly that I can go to the menu and right click on anything and add it to the panel EXCEPT anything in the 'Places' section. Why can't I add a place to my panel? When I right click on any 'place' it just opens the place, no options or anything.

As I mentioned in my earlier post, I can simply drag and drop my home icon from my desktop to a panel and this creates a link to my home folder. Pretty simple IMHO.

---

