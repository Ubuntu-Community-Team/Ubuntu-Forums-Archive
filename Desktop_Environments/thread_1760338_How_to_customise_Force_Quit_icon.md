---
title: "How to customise Force Quit icon?"
date: 2011-05-16
forum: Desktop Environments
---

### Post by Sealbhach on 2011-05-16
I'm using the Faenza icon set but I do like to have the Force Quit button on my panel, however it looks really odd and out of scale compared to the rest of the icons. 

See pic: [http://edge.imgur.com/CiqOp.png](http://edge.imgur.com/CiqOp.png)

So does anyone know how I can change it, left-clicking doesn't bring up properties in the menu.

Does anyone know if there is a Faenza icon for it (couldn't find anything on Google) and if so, how could I change it?

.

---

### Post by Sealbhach on 2011-06-07
Nobody knows how to change the Force Quit icon? 

.

---

### Post by Arijan on 2011-06-17
Force quit is not included in Faenza icon set. You have to find one or to make it by yourself.
If you place the search "gnome-panel-force-quit" in Google images, you'll find plenty of them. 

When you do, name it "gnome-panel-force-quit" , and place it in  ~/.icons/Faenza/apps/24

Don't forget to execute "pkill gnome-panel" before you start expecting to see the changes.

---

### Post by Sealbhach on 2011-06-24
Hi, thanks for the reply, I tried your suggestion but it didn't work. I found a way to replace the icon it uses by going to 

/usr/share/icons/hicolor/24x24/apps

and replacing the gnome-panel-force-quit icon there with a different icon I prefer. It's the only method I found that worked. Of course, if I change my icon theme again I will have to go back there and change the icon in there too.

Again, thanks for your help. ;)

.

---

