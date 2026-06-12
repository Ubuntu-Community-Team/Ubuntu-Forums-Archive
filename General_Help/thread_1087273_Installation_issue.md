---
title: "Installation issue"
date: 2009-03-04
forum: General Help
---

### Post by SuperIntense on 2009-03-04
I just tried to install Lime wire and I messed up on something so I tried to close it. Now it says I have other programs working and when I go to package manager its say's the below. What do I do to clear this?:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by Crafty Kisses on 2009-03-04
Run the following command:
```
sudo dpkg --configure -a
```

---

### Post by SuperIntense on 2009-03-04
Run under what area. I'm new sorry!

---

### Post by neppakyo on 2009-03-04
> **SuperIntense said:**
> Run under what area. I'm new sorry!

use a terminal

in gnome... Applications > Accessories > Terminal

---

### Post by SuperIntense on 2009-03-04
Now I get and error in the box at the top that says

Error: Failed to satisfy all dependencies (broken cache)

By the way Thanks for helping

---

### Post by neppakyo on 2009-03-04
sudo apt-get -f install maybe..

---

### Post by SuperIntense on 2009-03-04
Help Now when I do up dates it says

Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.

---

### Post by neppakyo on 2009-03-04
apt is probably running in the bg. The quickest and simplist way to stop it is to reboot. heh.

Too tired to explain to look for the process and kill it >.<

---

