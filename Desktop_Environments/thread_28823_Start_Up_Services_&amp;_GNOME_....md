---
title: "Start Up Services &amp; GNOME ..."
date: 2005-04-21
forum: Desktop Environments
---

### Post by Shinkan on 2005-04-21
HI there !

I'm now using Ubuntu 5.04 with GNOME 2.
I would like to know what utility/application should I launch to manage (i.e. Add, Delete ...) services and applications which are launched with GNOME and/or linux.
I've heard about utilities such as rcconf or sysvconfig but they're all ONLY managing linux services, and not gnome additional services (i.e. Evolution alarm ...).

Nutshel >> Is there any graphical utility which can manage GNOME and LINUX startup services ?

Thx !  ](*,)

---

### Post by Leif on 2005-04-21
One way is system-preferences-sessions-startup programs

---

### Post by Shinkan on 2005-04-22
I have "Sessions" (sessions)" incon, which open a windows where I can found a "Startup Programs" (programmes aux démarrage) tab, which is empty (even if I have startup daemons automatically lauchend by GNOME such as Evolution Alarm).

... ok ... I'll stay calm ... I'll drink coffee ...  :-? ...  ](*,)

---

### Post by Alexander Kirillov on 2005-04-22
[QUOTE=Shinkan]I have "Sessions" (sessions)" incon, which open a windows where I can found a "Startup Programs" (programmes aux démarrage) tab, which is empty (even if I have startup daemons automatically lauchend by GNOME such as Evolution Alarm).

... ok ... I'll stay calm ... I'll drink coffee ...  :-? ...  ](*,)[/QUOTE]
 Startup programs tab is there for programs which are not "session-managed" - that is, older or non-gnome programs like emacs, not the default ones started by GNOME. More info in GNOME help. 

To delete default one, switch to "current session" tab, then find the ones you wnat to remove, click "remove", then make sure the checkbutton "save changes to session" is checked in "session options" tab. Logout and login again.

---

