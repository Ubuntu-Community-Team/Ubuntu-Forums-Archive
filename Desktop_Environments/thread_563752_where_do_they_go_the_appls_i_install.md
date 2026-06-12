---
title: "where do they go the appls i install?"
date: 2007-09-30
forum: Desktop Environments
---

### Post by asprofridis on 2007-09-30
when i install an appl that is relative to internet to goes to internet submenu
when there is not a relative submenu where does it goes???

i am talking about kubuntu 7.04

---

### Post by max.diems on 2007-09-30
Use Katapult to find it.

---

### Post by asprofridis on 2007-09-30
how does it works is starts a logo with a Katapult and it doesnt do anything :confused:

---

### Post by benerivo on 2007-09-30
I don't know about Katapult, but if you want to know where programs get installed, then they are usually put in /usr/bin or /usr/lib. If you know the name of the package that you installed, then you can type whereis PACKAGENAME in a terminal. For example ```
whereis firefox
```

Once you find it, it can be added manually to your KDE menu.

---

### Post by max.diems on 2007-10-01
Start typing :). (Type the name of the app into Katapult)
Actually, benerivo's idea might help more as you'll avoid having to type the name all the time.

---

### Post by hallowname on 2007-10-01
Goto your package manager (synaptic, adept_manager, kpackage, etc...) and find the package you installed then view the files in the packages, any files in a /bin or /usr/bin or /usr/sbin, are programs that you can run... (from a terminal, some are runnable from Alt+F2)...   :)

---

