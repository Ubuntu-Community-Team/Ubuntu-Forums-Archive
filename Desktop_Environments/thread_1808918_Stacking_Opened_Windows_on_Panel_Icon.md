---
title: "Stacking Opened Windows on Panel Icon"
date: 2011-07-20
forum: Desktop Environments
---

### Post by ASchlosser on 2011-07-20
Hey Everyone!

I was just wondering, is there a way to configure XFCE to stack open windows on the respective icon on my panel?  Like Windows 7 sort of, but I don't need all of the fancy effects.  I prefer not to use Cairo-Dock, I wasn't a fan when I tried it before.  Plus, I use XFCE to lighten the load on my system.  I figured out how to make it so the icon is the only thing that represents open windows and its currently acceptable, I was just wondering if there was a better way.

Thanks guys,
Andy

---

### Post by azertyh on 2011-07-21
hello,
right-click on the window button
properties
and untick "show button label"

---

### Post by ASchlosser on 2011-07-21
I got that, I meant so that they stack on the icon that I have on the panel.  I have the chrome icon on the panel for example, and I want it to stack windows on the shortcut instead of in a new window.  I'm thinking its probably impossible without a dock, but I just figured I'd ask.  Thanks anyways!

---

### Post by Pirate Zoro on 2011-07-22
You can make a dock-like panel using xfapplet (which lets you run gnome applets on an xfce panel) and Talika. To do this, bring up your terminal and enter:
```
sudo apt-get install xfce4-xfapplet-plugin && sudo apt-get install talika
```
Add xfapplet to the panel you wish to use. Right click on the xfapplet icon, select properties, and this brings up a menu to add a gnome applet to run. Select Talika. Then your open windows should now show up as launcher icons, and you can maximize or minimize icons into these launchers. You can pin launchers to the panel as well, making essentially a lightweight dock that works like docky or AWN using less resources

---

