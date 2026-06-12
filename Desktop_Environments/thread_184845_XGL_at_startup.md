---
title: "XGL at startup"
date: 2006-05-30
forum: Desktop Environments
---

### Post by blanc11 on 2006-05-30
I am using Gnome, and currently have to get XGL/Compiz running by clicking a launch icon on my desktop. Is there anyway to make it autmatically start up when I log in?

---

### Post by JoWilly on 2006-05-30
[QUOTE=blanc11]I am using Gnome, and currently have to get XGL/Compiz running by clicking a launch icon on my desktop. Is there anyway to make it autmatically start up when I log in?[/QUOTE]

wow... there are so many threads about this already.... -> search ;) 

Pointer:
1. to start xgl : edit /etc/gdm/gdm.config-custom

```
[server-Standard]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer -kb
flexible=true

```


2. add gnome-window-decorator and "compiz --replace gconf" to startup in your gnome sessions (menu system/prefs/sessions).

---

### Post by QuacoreZX on 2006-05-30
Sure, from Gnome, System -> Preferences -> Sessions -> Startup Programs (it's a tab), then add the script you use to initiate Compiz! That's it!

---

### Post by blanc11 on 2006-05-30
Sorry, couldn't find one that really answered this. I will try better next time ;) Thanks!

---

