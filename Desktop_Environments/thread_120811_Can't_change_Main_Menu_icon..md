---
title: "Can't change Main Menu icon."
date: 2006-01-23
forum: Desktop Environments
---

### Post by kenn_palmer on 2006-01-23
Create a .png file 48x48 pixels in size and save it in /usr/share/icons/hicolor/48x48 with the name distributor-logo.png. Thjis will replace the Ubuntu logo on the Application menu.

---

### Post by tebibyte on 2006-01-23
Hello all. I have a problem in which I can not figure out how to change the icon on the main menu toolbar. I tryed going into the menu editor thing. I clicked on "applications" and then on edit; properties. I changed the Icon thru the pop up. No luck. I find it weird that the icon displayed in the editor is not the icon that is on the toolbar.

Thank You very much for your help

PS attached are pictures that show what I attempted.

---

### Post by Pedricko on 2006-01-23
I have this problem too - I got a .png from gnomelook.

Puppy is awesome btw.

---

### Post by jackinloadup on 2006-01-24
same here. will go into the menu editor and it will not change.. i swear i found the actual image in /usr/share/hwdb-client/ but replacing it helped none just like the steps above... any help would be great

---

### Post by manicka on 2006-01-25
[QUOTE=jackinloadup]same here. will go into the menu editor and it will not change.. i swear i found the actual image in /usr/share/hwdb-client/ but replacing it helped none just like the steps above... any help would be great[/QUOTE]

kenn_palmer's method (pos t1) will change the logo to whatever you like. If you just want the gnome foot as the icon try this method - 

[http://doc.gwos.org/index.php/Gnome_Icon](http://doc.gwos.org/index.php/Gnome_Icon)

---

### Post by jackinloadup on 2006-01-25
this method didnt work for me.. im running beezy .10

---

### Post by Perfect Storm on 2006-01-25
Did you killall gnome-panel after you made the change?

```

sudo cp distributor-logo.png /usr/share/icons/hicolor/48x48/apps
killall gnome-panel
```

It should work also in 5.10 as I'm using this methode.

---

### Post by manicka on 2006-01-25
[QUOTE=jackinloadup]this method didnt work for me.. im running beezy .10[/QUOTE]
which method? there are a couple described here

---

### Post by speed on 2006-02-03
[QUOTE=kenn_palmer]Create a .png file 48x48 pixels in size and save it in /usr/share/icons/hicolor/48x48 with the name distributor-logo.png. Thjis will replace the Ubuntu logo on the Application menu.[/QUOTE]

this also works for me.

```
sudo mv /usr/share/icons/hicolor/48x48/apps/distributor-logo.png /home/user/backup/
sudo killall gnome-panel
```

btw: there's an original gnome-foot icon /usr/share/icons/hicolor/48x48/apps/gnome-main-menu.png
correct me if i am wrong ;)

---

### Post by harold4 on 2006-02-03
Applications > system tools > configuration editor:

apps > panel > objects > object_0:

check "use_custom_icon"
edit "custom_icon" to the path of your custom icon: 

The Foot = /usr/share/pixmaps/gnome-logo-icon-transparent.png

---

