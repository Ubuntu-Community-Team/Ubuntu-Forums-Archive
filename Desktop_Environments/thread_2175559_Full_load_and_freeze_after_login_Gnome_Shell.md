---
title: "Full load and freeze after login Gnome Shell"
date: 2013-09-19
forum: Desktop Environments
---

### Post by mandu2 on 2013-09-19
Hello all,   i am experiencing an issue for a long now and i could not find any solutions, so i am asking for your help.    I am using Ubuntu 12.04 with Gnome Shell.  After i login into my session and after the top bar appears (which means after gnome shell is loaded) the system directly freezes for ~6-7 seconds. While on that, the led of the hard disc is always on green without any blinks. Meanwhile i can move the cursor but without any results on clicking anything.  After those seconds i can use the system as normal.    Something is occupying the whole system after login but i do not know what. Also i do not know where to look for that. By the way, if i create a new user, the above issue does not appear.    Any ideas or informations?  Thanks :)

---

### Post by ashokshah25 on 2013-09-19
Use "top" command to find processes. Either SSH to your box before logging into Gnome, or Ctl+Alt+F1, and once you login just monitor output of top. Probably some user specific initialization is taking too long to initialize.

---

### Post by sudodus on 2013-09-20
Please specify your computer, brand name and model, cpu, ram (size) and graphics card :-) Then it will be easier to give good advice.

---

