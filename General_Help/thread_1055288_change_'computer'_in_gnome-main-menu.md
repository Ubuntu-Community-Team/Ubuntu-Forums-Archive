---
title: "change 'computer' in gnome-main-menu"
date: 2009-01-30
forum: General Help
---

### Post by adie273 on 2009-01-30
Hey all, is it possible to change the word "computer" in gnome-main-menu (slab).

I use to use this couple years back now i think it was. And it use to say menu. 

Its just a personal preference. I'd rather have just an icon, but if it must have text beside it then can i change it?

And if so, how?

Thanks in advance

---

### Post by dmizer on 2009-01-31
Moved to General help.

You can right click on the menu and select "remove from panel". Then right click on the panel, select "Add to panel" and use "Main Menu".

"Main menu" is the GNOME menu with icon only. the "Menu bar" is the Ubuntu custom menu.

---

### Post by fitzydog on 2009-06-26
I don't know either, but there must be reason he's using the g-m-m instead of the default. It doesn't even ship with Ubuntu does it? If anyone has an answer to changing the text, that'd be great.

---

### Post by CatKiller on 2009-06-27
The .desktop file that calls it Computer in other places is /usr/share/applications/nautilus-computer.desktop. I don't know if whatever it is you're using uses that, but it's worth a look.

---

### Post by birddog165 on 2009-11-01
You ever figure this out? Because I would be interested in changing it myself.

---

### Post by dgtester on 2009-12-14
```
sudo gedit /usr/share/gnome-main-menu/slab-window.glade
```

Change instances of "Computer" to whatever you want.

---

### Post by marranzano on 2010-01-26
> **dgtester said:**
> ```
sudo gedit /usr/share/gnome-main-menu/slab-window.glade
```

Change instances of "Computer" to whatever you want.

thanx!!...

---

