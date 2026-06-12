---
title: "Xubuntu 14.04 - Whisker menu remove &quot;Favorites&quot; and &quot;Recently Used&quot; categories"
date: 2014-05-04
forum: Desktop Environments
---

### Post by fpD7n6W on 2014-05-04
Hi!

Is there any way to remove the "Favorites" and "Recently Used" categories in the Whisker menu (Xubuntu 14.04)? Neither the Whisker menu nor Menulibre allow me to do that. I did a bit of research, but I couldn't find the right configuration file. 

Is there anyone out there who could help me out?

---

### Post by macachuto on 2014-05-04
I want to joint to this question, but I also need something different.
I would like to be able to choose category that will be open then "whisker menu" pops up. 
For instance I would like to see my own category, because I want to add a separator in there.

---

### Post by Dennis N on 2014-05-04
> **fpD7n6W said:**
> Hi!

Is there any way to remove the "Favorites" and "Recently Used" categories in the Whisker menu (Xubuntu 14.04)? Neither the Whisker menu nor Menulibre allow me to do that. I did a bit of research, but I couldn't find the right configuration file. 

Is there anyone out there who could help me out?

You can test this out (I haven't):

Edit the file **[FONT=Courier New]~/.config/xfce4/panel/whiskermenu-29.rc[/FONT]** and comment out the lines beginning **favorites=** and **recent=** and see what effect that has. You may have to log out and back in.

---

### Post by macachuto on 2014-05-04
It doesn't work - "favorites" button and empty list.

---

### Post by brainwash on 2014-05-05
Removing these two categories is not possible as of now. Please file an upstream report and request this feature.

[https://github.com/gottcode/xfce4-whiskermenu-plugin/issues](https://github.com/gottcode/xfce4-whiskermenu-plugin/issues)

---

