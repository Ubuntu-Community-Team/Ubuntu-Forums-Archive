---
title: "How do I rename my computer?"
date: 2009-03-30
forum: General Help
---

### Post by Peter_G on 2009-03-30
I made a typo in the installation process with the computer name, is there anyway I can fix it?

---

### Post by hexanol on 2009-03-30
Yes there is. Look for the command "hostname" with "man hostname". It will tell you how to set a new hostname.

But actually I'm not 100% sure if the computer name is the same as the hostname. Well, guess you'll discover.

---

### Post by stereomuffin on 2009-03-30
sudo gedit /etc/hostname

---

### Post by Avinash.Rao on 2009-03-30
The easiest and quickest way to do it is edit the /etc/hosts file.

---

### Post by CatKiller on 2009-03-30
It certainly used to be the case that if the hostnames in /etc/hostname and /etc/hosts didn't match, then **sudo** didn't work to let you change the other one to fix it. Open them both with ```
gksudo gedit /etc/hostname
gksudo gedit /etc/hosts
``` (this will open gedit with root privileges with both documents open) then make your changes and save both of them.

---

