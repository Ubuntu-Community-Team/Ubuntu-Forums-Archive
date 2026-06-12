---
title: "Gnome Menu User  &quot;Template&quot;"
date: 2009-01-16
forum: Desktop Environments
---

### Post by Vince4Amy on 2009-01-16
I have a few users I need to setup on a system and although there are multiple users I have customised the gnome menu to respect what is required. 

However when I create a new account I have to edit the menu again, can I copy the menu structure from User 1 to User 2 for example so I don't have to keep modifying it.

---

### Post by FIONEX on 2009-01-16
Yes you can.  The menu is actually an XML file I believe.  If I can remember where the file is, I'll post it.  You should try looking for "Ubuntu Menu File" on google or something.

---

### Post by FIONEX on 2009-01-16
Hey man, I did a little research for you but it's upto you to figure out the rest.  So the modifications you make for each user go in the follow file:
/home/fionex/.config/menus/applications.menu

As you can see, this file also references the "default menu":
/etc/xdg/menus/applications.menu

Now what you want to do with this information is upto you.  For more information on the menu format, go here:
[http://library.gnome.org/admin/system-admin-guide/2.20/menustructure-13.html.en](http://library.gnome.org/admin/system-admin-guide/2.20/menustructure-13.html.en)

---

