---
title: "Add/Remove miising from application dropdown"
date: 2009-08-15
forum: Desktop Environments
---

### Post by greyghost60 on 2009-08-15
My add/remove entry has disappeared from the application dropdown. How do I get it back?. I have Ubuntu Tweaks loaded maybe... 

Any help appreciated


:confused:
Thanks everyone
the app gnome-app-install was missing. Reinstalled and all is well now :)

---

### Post by Raffles10 on 2009-08-15
If you right click on 'Applications' > 'Edit Menus', is it not listed at the bottom of the Applications list ? If not you can get it back by adding a 'New Item':

Type: Application
Name: Add/Remove...
Command: /usr/bin/gnome-app-install
Comment: Install and remove applications

---

### Post by colau on 2009-08-16
+1

---

