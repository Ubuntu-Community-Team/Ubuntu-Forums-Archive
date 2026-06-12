---
title: "How to run Obmenu in Ubuntu?"
date: 2011-03-09
forum: Desktop Environments
---

### Post by XsheepX on 2011-03-09
I recently installed the Openbox session on Ubuntu 10.10, but I want to just be able to run obmenu while running Gnome.
I can't seem to get it to replace the regular gnome right-click menu, no matter what I try.

Any ideas?

---

### Post by XsheepX on 2011-03-10
bump

---

### Post by Frogs Hair on 2011-03-10
The only possibly related package I see in synaptic is openbox-xdgmenu .

---

### Post by XsheepX on 2011-03-10
> **Frogs Hair said:**
> The only possibly related package I see in synaptic is openbox-xdgmenu .
Any idea how to run it during a Gnome Session?

---

### Post by Frogs Hair on 2011-03-10
Not really , I know how to use menu-xdg in Gnome , but this is the first time I have seen that package and the description doesn't  provide much information. I thought it may be worth researching.

---

### Post by mcduck on 2011-03-11
The  thing here is that OBMenu isn't the menu you get on Openbox, it's just a tool for *configuring* the menu.

The menu is a feature of Openbox itself, so you'd have to use Openbox as your window manager in Gnome to get access to that menu. 

Also another problem would be that Gnome uses Nautilus to draw the desktop, desktop icons, and to provide the right-click menu on desktop. So you'd have to stop Nautilus from managing the desktop before you could actually ever see the right-click menu provided by Openbox. And then add some other tool to handle wallpaper and desktop icons.

---

### Post by XsheepX on 2011-03-12
> **mcduck said:**
> The  thing here is that OBMenu isn't the menu you get on Openbox, it's just a tool for *configuring* the menu.

The menu is a feature of Openbox itself, so you'd have to use Openbox as your window manager in Gnome to get access to that menu. 

Also another problem would be that Gnome uses Nautilus to draw the desktop, desktop icons, and to provide the right-click menu on desktop. So you'd have to stop Nautilus from managing the desktop before you could actually ever see the right-click menu provided by Openbox. And then add some other tool to handle wallpaper and desktop icons.

Thank you, but I still have one more problem. Even if I run a Gnome/Openbox session, how do I replace nautilus?

---

