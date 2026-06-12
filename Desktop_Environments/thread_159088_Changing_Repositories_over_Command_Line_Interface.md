---
title: "Changing Repositories over Command Line Interface"
date: 2006-04-12
forum: Desktop Environments
---

### Post by bluemike807 on 2006-04-12
Hi, I need to set my Server - which I can only really access over SSH - to use all the Multiverse and Universe repositories (right now I think its only on the basic default)
but I need to do it from CLI. How can I?

---

### Post by Ramses de Norre on 2006-04-12
sudo nano /etc/apt/sources.list or sudo vi /etc/apt/sources.list
And uncomment all the lines starting with deb.

---

### Post by zerhacke on 2006-04-12
sudo apt-get install pico

sudo pico /etc/apt/sources.list

I find pico to be a lot easier to use than vi or nano.

---

### Post by aysiu on 2006-04-12
I recommend ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
``` When you're done, press 
**Control-x**
**y**
**Enter** to get out of Nano and save your changes.

---

