---
title: "No Panels Running kde4 Under Ubuntu"
date: 2008-07-25
forum: Desktop Environments
---

### Post by Tim_Olaguna on 2008-07-25
[SOLVED] [With the help of the kind gentleman below.] I'm running Ubuntu Hardy 8.04.1.  I have installed three desktop options:

1.  Ubuntu (Gnome style)
2.  Kubuntu (kde 3 style)
3.  Kde 4.1 

Desktops 1 and 2 run well,  But when logging on trying to use #3 (Kde 4.1 ) I get no panels at all on the bottom or top.  Thus I have no access to any menus at all.  Which means I can do diddley.

I can right-click and get access to a small menu which does allow me to add a new panel.  But there are no items on that panel.

I've seen some very favorable comments about how well kde 4.1 runs under OpenSUSE.  But I want to get it to run under ubuntu/kubuntu.

Doe anyone have any suggestions?  Thank you in advance for your time and trouble.

---

### Post by benerivo on 2008-07-25
What happens when you right click on a panel that you have just created? It should give you an option that will allow you to add items to it.

---

### Post by Tim_Olaguna on 2008-07-25
> **benerivo said:**
> What happens when you right click on a panel that you have just created? It should give you an option that will allow you to add items to it.


Duh, what do you know?  Of course it does.  Thank you for opening a portal into a whole new world for me.

---

### Post by Tim_Olaguna on 2008-07-26
An even better simple solution turns out to be:

Code:
---------
cd ~
rm -r .kde4
---------
Then logout and log back into KDE 4.  This will set all desktop configs to their defaults.

Thanks go to Johnny Utah over at kubuntuway.net for this advice.

---

