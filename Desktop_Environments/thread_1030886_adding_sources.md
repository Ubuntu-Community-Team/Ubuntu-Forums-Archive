---
title: "adding sources"
date: 2009-01-04
forum: Desktop Environments
---

### Post by num on 2009-01-04
hello,

i am trying to add the freenx source into source.list but i cannot edit as it says i do not have permission. how can i edit this file as root?

---

### Post by keithld on 2009-01-04
have you tried gksudo gedit and open the file in there then save???

You can also add in it the Synaptic Package Manager under Settings > Repositories> Third Pary Software if I'm not mistaken...

---

### Post by SuperSonic4 on 2009-01-04
GUI: gksu gedit /etc/apt/sources.list

CLI: sudo nano /etc/apt/sources.list

---

