---
title: "sudo in launcher (shortcut on desktop)"
date: 2005-12-15
forum: General Help
---

### Post by Reggie on 2005-12-15
I want to run a program which I normally run as root (or use with sudo).
So i've made a "launcher" on my desktop .. and tried to add the command "sudo binfile". This doesn't work, cause I he probably needs a password. How can I fix this ?

---

### Post by bogoliubov on 2005-12-15
Use 
gksudo application-name

When I want to fix stuff like that, I usually check /usr/share/applications folder. It contains the stuff in the Gnome-menu...

---

### Post by Reggie on 2005-12-15
cool, thnx for the tip :)

---

