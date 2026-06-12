---
title: "Debian menu will not show after restarting X"
date: 2006-07-13
forum: Desktop Environments
---

### Post by Calitar on 2006-07-13
I am using Xubuntu and I recently tried to install the Debian menu via apt-get. After logging out and restarting X, the Debian menu still will not show. Because the graphical menu editor in this release likes to eat menus, I may have to manually edit my menu.xml file. However, I do not know what changes I need to make to get it to show.

---

### Post by Calitar on 2006-07-14
Sorry for the bump, but it has been 17 hours and I don't think anyone is going to see it at this point.

---

### Post by theturtlemoves on 2006-07-14
Are you sure that the graphical menu editor eats menus? I used it to enable the Debian menu, and I had no problems.

---

### Post by Calitar on 2006-07-14
Are you using Xubuntu? It's even stated as a known issue and it has happened to me every time I try to use it (I made a backup of the menu file after the first time. Could you look in your /home/calitar/.config/xfce4/desktop/menu.xml file and post the relevent parts of it?

---

### Post by Calitar on 2006-07-14
Well, I'm making some headway. By adding ```
<include type="file" src="/var/lib/menu-xdg/menus/debian-menu.menu"/>
``` to my menu.xml file I managed to get it to show an "other" catagory. It seems to show all the stuff the debian menu would show, but it is all in one big list instead of in their own sub-catagories.

---

