---
title: "How do you add networkmanager to the upstart routine?"
date: 2005-11-24
forum: Desktop Environments
---

### Post by Paragdim on 2005-11-24
I've tried with sudo nm-applet in a terminal. That only adds it to the panel as long as the terminal is active. I would like it to start automatically everytime U start the KDE interface. Any ideas?

---

### Post by odin on 2005-11-24
Dont know If you can do that with the boot up manager but try.

sudo apt-get install bum

---

### Post by mlomker on 2005-11-24
[QUOTE=Paragdim]I've tried with sudo nm-applet in a terminal. That only adds it to the panel as long as the terminal is active. I would like it to start automatically everytime U start the KDE interface. Any ideas?[/QUOTE]

I assume that you could add a link to the ~/.kde/Autostart directory.

---

