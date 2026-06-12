---
title: "Unity only runs from terminal"
date: 2011-05-07
forum: Desktop Environments
---

### Post by atimus on 2011-05-07
Hi, last week before I updated ubuntu and restarted ubuntu give an advertisement telling that I don't have the hardware requeriments to run unity. After that I was running unity with nouveau drivers with any problems. 
I have tested too with de propietary drivers and nothing. If I run unity from terminal it works. It's very strange. Actually I log in in gnome sesion (with the panels), I hid the upper panel and added unity to the startup applications but if I can run unity in this way must be a way to repair it to start a normal session. 
Ideas?

---

### Post by Krytarik on 2011-05-08
Try adding "UNITY_FORCE_START=1" to "/etc/environment".

Greetings.

---

### Post by atimus on 2011-05-13
> **Krytarik said:**
> Try adding "UNITY_FORCE_START=1" to "/etc/environment".

Greetings.

Sorry for the delay in reply, I have just added it to /etc/enviroment and unity is back when I run in Ubuntu session. 
Thanks for the help.

---

