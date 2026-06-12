---
title: "Desktop Launcher Gone!"
date: 2008-08-16
forum: Desktop Environments
---

### Post by kierpaul on 2008-08-16
Hi everyone,

I had a problem with Hardy where it locked up and I had to power down. Now when I power up and log into Ubuntu my launchbar is gone! I cannot acces applications, places, system, etc. However, my folders are visible on my desktop! Can anyone help me out with this??? I can get to a terminal window at boot up! I have to do the ole CNTR+ALT+DEL to shutdown!

---

### Post by Raffles10 on 2008-08-17
Do you still have your bottom panel ?

If so just right click on it and select "New Panel", it may appear at the top or side, if so right click on it select "Properties" and you can set it to be top.

You can add your menus, shutdown etc by right clicking and selecting "Add To Panel".

---

### Post by kierpaul on 2008-08-17
Raffles10: Thanks, but I have no bottom panel either! I tried right clicking Add to Panel and nothing happens! I am wondering what happened at this point and if I need to somehow repair this installation?

---

### Post by Raffles10 on 2008-08-17
In that case I would suggest complete removal & re-installation of the panel:

sudo apt-get remove --purge gnome-panel

sudo apt-get install gnome-panel

---

