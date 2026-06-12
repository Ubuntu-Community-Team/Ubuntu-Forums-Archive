---
title: "Having 2 problems..."
date: 2006-07-16
forum: Desktop Environments
---

### Post by DAaaMan64 on 2006-07-16
Hey all, using XFCE here and for some reason I have having that same shift+backspace problem that forced X to restart when you used xgl... How can I disable this completely so my XFCE doesn't do it?

Also, ever sense I command line called nautulis gnome has controlled my desktop until I tell the XFCE settings manager to do it.  Whats the deal?  It wouldn't bother me except I hate desktop icons and gnome won't let me turn them off.  

Thanks for your help in the past.

---

### Post by computx on 2006-07-16
Can't help with the first problem but what your seeing with nautilus is it's default method of operation. I believe there is a way to call it so it doesn't take over the desktop. Maybe --noroot. But in any case when you want to get rid of it controlling your desktop just open a terminal and type killall nautilus.

---

### Post by DAaaMan64 on 2006-07-16
But this is happening everytime I login. :(

---

### Post by computx on 2006-07-20
You probably had nautilus running at some point when you exited xcfe and picked the option save settings.

I haven't used xfce for a while but somewhere in your home directory is a file telling xfce what to load at startup. could be .xinitrc or maybe in a subdirectory called .xfce. You need to remove nautilus from there then it shouldn't auto start any longer.

---

