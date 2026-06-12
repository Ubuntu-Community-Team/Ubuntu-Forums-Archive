---
title: "I can't boot into GNOME"
date: 2007-04-21
forum: Desktop Environments
---

### Post by CSMatt on 2007-04-21
Ever since I installed the GMONE app for Compiz in Feisty and turned GL efects on, X keeps freezing and restarting.  Now I can't log in without Compiz turning on and freezing the system and making X restart each time.  How do I get back to Metacity and/or turn Desktop Effects off?

Beryl worked fine for me when I was using Edgy.  Is this an issue with Feisty or Compiz?  Is it possible that Beryl will work for me on Feisty since it worked on Edgy?

---

### Post by e00878 on 2007-04-21
I have the same problem with matrox g400 graphic card.

---

### Post by CSMatt on 2007-04-21
bump

---

### Post by ComplexNumber on 2007-04-21
can you post your xorg.conf file, please? you will find it in /etc/X11 directory.

---

### Post by CSMatt on 2007-04-21
Sure.

---

### Post by CSMatt on 2007-04-21
Bump again.

---

### Post by CSMatt on 2007-04-21
Never mind.  I managed to fix it myself by booting into recovery mode and typing "sudo dpkg-reconfigure xserver-xorg" at the prompt.  Compiz is working now.

---

