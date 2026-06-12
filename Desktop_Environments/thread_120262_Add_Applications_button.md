---
title: "Add Applications button"
date: 2006-01-21
forum: Desktop Environments
---

### Post by naruto11111 on 2006-01-21
Hi, I'm new to linux.  I seem to have somehow gotten rid of the Add Applications button in the Applications menu.  Can someone tell me how to get it back?  And also how to uninstall programs without that?  Thanks in advance

-Michael

---

### Post by matthewv on 2006-01-21
Right click on the Applications button in the top left of your screen (or wherever you put it) Select edit menus. Make sure there is an entry called Add Applications and that the check box next to it is selected. If that entry does not exist, create a new entry. Call it Add Applications, give it a description of Install and remove applications, and make the command ```
/usr/bin/gksudo /usr/bin/gnome-app-install
```. Click on the icon part and chose the correct icon and you should be all set.

---

### Post by naruto11111 on 2006-01-26
thanks for the reply, but when I try to run that new entry it says:

Failed to run /usr/bin/gnome-app-install as user root:
 Child terminated with 1 status


thoughts?

---

### Post by ncappel1 on 2006-02-24
try searching for "gnome-app-install" in synaptic. it may have happened that you accidentally uninstalled it.

---

### Post by nanotube on 2006-02-24
in general, using the synaptic package manager is really a better way to install/remove applications, anyway. :)
(in System>Administration>Synaptic Package Manager).

---

### Post by naruto11111 on 2006-02-24
I got it working, I guess I somehow uninstalled it.  Thanks!

---

