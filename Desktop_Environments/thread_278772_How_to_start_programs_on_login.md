---
title: "How to start programs on login?"
date: 2006-10-16
forum: Desktop Environments
---

### Post by Number6 on 2006-10-16
All I want to do is have a program such as xscreensaver run when I login.
In the old days I'd use xinitrc but of course that's no use anymore since I never use startx, I use GDM! There's several config files with GDM like gdm.conf, postlogin,presession,xsession where the hell does user startup stuff go?? It's driving me a bit crazy ](*,)

---

### Post by skirkpatrick on 2006-10-16
Add them to System->Preferences->Sessions on the Startup Programs tab.

---

### Post by drummer on 2006-10-16
In Gnome, System >> Preferences >> Sessions > Startup tab

---

### Post by Number6 on 2006-10-16
Ahh! So simple thanks very much! 

  Just out of interest, If I didn't have such a simple method, ((ie) If I wasn't using Gnome) which config files are involved? I'd assume it's Xsession but there seem to be multiple versions of this file, and there isn't one in my home directory!

---

### Post by drummer on 2006-10-17
I think you can put a .Xsession file in you home directory, it's just not there by default.

---

### Post by D!mon on 2006-10-17
How can I do the same in the KDE?

---

### Post by TheWizzard on 2006-10-17
> **D!mon said:**
> How can I do the same in the KDE?

you can put a script in the ~/.kde/Autostart folder. scripts in here are run as you login to kde. 

also you can run scripts on logout if you put them in the ~/.kde/shutdown folder. you need to create this folder.

---

### Post by T.Ephraim on 2007-10-04
Hey,

and how can the prioritization be set (within Gnome)?
e.g. I have two programs where one program must be started before another, because the other depends on the first.
Just to add them in that order, makes me not feel certain.

Thx.
Ephraim

---

