---
title: "My right click is broken in gnome"
date: 2006-09-24
forum: Desktop Environments
---

### Post by thenetduck on 2006-09-24
Hi, 
  I have an installed Xubuntu distro. and just installed Gnome on my desktop as well. 

 sudo aptitude install gnome

It worked just the way I wanted it to, however, my right click is broken. Whenever I right click it doesn't work. Anyone know how to fix that? It's kind of irritating. Thanks, 
 
 The Net Duck

---

### Post by thenetduck on 2006-09-24
Im going to BUMP this post because I still need help on the same problem and can't see to figure out a solution :) Any help is wanted thanks, 
 
The Net Duck

---

### Post by R3d3y3 on 2008-02-10
I have the very same problem. Searching for an answer now. I'm running Ubuntu 7.10.

---

### Post by R3d3y3 on 2008-02-10
You can try this... 

[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

---

### Post by erfahren on 2008-02-10
first try this - open the gnome-configuration-editor

press Alt+F2 and enter
```

gconf-editor

```
navigate to: apps/nautilus/preferences/show_desktop key - and make sure it's checked

if you needed to check it - logout and back in and see if it helped

---

