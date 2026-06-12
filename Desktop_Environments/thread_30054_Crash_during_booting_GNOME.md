---
title: "Crash during booting GNOME"
date: 2005-04-27
forum: Desktop Environments
---

### Post by davegahan on 2005-04-27
This morning, after entering my username and password, my Ubuntu suddenly hang during loading the metacity windows manager. Clicking on a mousebutton made my screen go black, and in the end I had to disconnect my laptop from power and take my battery out to restart. Help ! How can i get to resume my work, or retrieve my files ?

---

### Post by graigsmith on 2005-04-27
does it do it on every boot? every user account?

---

### Post by davegahan on 2005-04-27
Yes, there is only one user - me. 

Yesterday I had a problem when Totem turned a blue screen and I had to reboot as well the system. Today, well, I need to find a way to retrieve my files.  I am in quite a predicament.

---

### Post by fordfan753 on 2005-04-27
Have you editted /etc/X11/xorg.conf lately?
This could be stopping X from loading, also try ctrl + alt + backspace to kill gdm, log in, and type "startx" see if you get any error messages

---

### Post by davegahan on 2005-04-27
I managed to get into GNOME by choosing from the session manager "fail-safe" disabeling all startup scripts. What do I do now ?

I made a backup of my homedirectory. Should I just reinstall hoary all over again and restore my settings (how do I do that?).

Any help would be much appreciated.

---

