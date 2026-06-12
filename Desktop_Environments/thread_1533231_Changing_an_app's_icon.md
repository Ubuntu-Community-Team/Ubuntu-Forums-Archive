---
title: "Changing an app's icon??"
date: 2010-07-17
forum: Desktop Environments
---

### Post by PepeLapiu on 2010-07-17
Okay, here's my take on this. When you install Firefox for example, it also installs it's icons on my machine. 

But let's say I want to change the Firefox icon from the default one to this one: [http://www.hungry-hackers.com/wp-content/uploads/2009/06/fasterfox.png](http://www.hungry-hackers.com/wp-content/uploads/2009/06/fasterfox.png)

I would assume that all I need to do is find where the default Firefox icon is stored, delete it (or move it elsewhere), and replace it by the new one.

But where does Ubuntu store the default icons for Firefox?

Thanx,
PepeLapiu :)

---

### Post by dv3500ea on 2010-07-17
Most application icons are stored in /usr/share/pixmaps. You will probably need to convert it from png to xpm (you can use gimp for this)

---

### Post by PepeLapiu on 2010-07-17
> **dv3500ea said:**
> Most application icons are stored in /usr/share/pixmaps. You will probably need to convert it from png to xpm (you can use gimp for this)

Okay, it's all very well. I found the folder where the Firefox default icon is. It's in /usr/lib/firefox-3.6.6/icons

But it seems I don't have permission to remove/delete/add/c&p/rename files in those folders. How do I move these files as sudo?

---

### Post by kerry_s on 2010-07-17
change it the same as you would on the desktop, use the main menu.

---

### Post by mister_p_1998 on 2010-07-19
Well I just have a folder in home called icons, I right button/properties on the old icon picture, then browse to /home/icons and choose the new icon. Make sure you've put the picture in there first, ( I have some nice OSX icons in my folder).

Steve

---

