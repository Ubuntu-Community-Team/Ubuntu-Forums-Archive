---
title: "Change icon of starter"
date: 2009-09-21
forum: Desktop Environments
---

### Post by Freekmans on 2009-09-21
Hi,

I have a couple of starters on my desktop and I would like to change the icon of it.
Not adding an extra icon to it (which you can do by right mouse click, properties) but a complete different icon. Now I have like 4 of those springs on my desktop.

Any help is well appriciated

Thanks !

---

### Post by jerrrys on 2009-09-21
click on the icon in properties and you can change it to whatever you want

---

### Post by Freekmans on 2009-09-21
> **jerrrys said:**
> click on the icon in properties and you can change it to whatever you want

Thanks for your reply, but no I can´t.
I can only add another ´emblem´ on top on the current spring icon. I want to replace the spring icon.

---

### Post by theZoid on 2009-09-21
> **Freekmans said:**
> Thanks for your reply, but no I can´t.
I can only add another ´emblem´ on top on the current spring icon. I want to replace the spring icon.

Click on the spring icon itself

---

### Post by jerrrys on 2009-09-21
sorry, that must only work in 8.04

---

### Post by theZoid on 2009-09-21
> **jerrrys said:**
> sorry, that must only work in 8.04

I just created a launcher with custom icon that way.  Been doing it since gutsy (my first ubuntu release)...I don't get it.

---

### Post by VCoolio on 2009-09-21
I don't get why the above solutions don't succeed, but here's a third: open the launcher in a text-editor (it's basically a .desktop file), find or add a line "Icon=" and add either a path to your icon or scroll through your current icon theme folder (/usr/share/icons/<theme> or ~/.icons/<theme>) and find the name of an icon you like and add that (in that case the whole path is not required). So make it "Icon=/path/to/icon.png" or "Icon=icon-name-from-theme"

---

### Post by gadolinio on 2009-09-22
Strange thing... if you right-click, then go to properties, and click the spring icon of the properties window, you should get a window where you can change the icon!

---

### Post by Freekmans on 2009-09-22
> **gadolinio said:**
> Strange thing... if you right-click, then go to properties, and click the spring icon of the properties window, you should get a window where you can change the icon!

Aaaaah, that did the job/trick ! I didn't know you could actually click the spring itself within being in the properties window !

Thanks guys !

---

### Post by gadolinio on 2009-09-23
> **Freekmans said:**
> Aaaaah, that did the job/trick ! I didn't know you could actually click the spring itself within being in the properties window !

Thanks guys !

Haha i liked that when i discovered it; in linux everything can be clicked or right-clicked, and then configured... Have fun!

---

