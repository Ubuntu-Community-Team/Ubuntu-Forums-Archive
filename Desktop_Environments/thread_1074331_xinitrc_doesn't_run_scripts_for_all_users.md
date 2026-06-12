---
title: "xinitrc doesn't run scripts for all users"
date: 2009-02-19
forum: Desktop Environments
---

### Post by kirilstankov on 2009-02-19
Hi all,

I need to start a background program for all users logging in to Gnome.
I tried adding a line to xinitrc to call a script, but this doesn't seem to work. Same with rc.local.

Any ideas how I can do this?

Thanks a lot in advance!

Kiril.

---

### Post by geos-one on 2009-02-19
i have done this via /usr/share/autostart/

createt there a .desktop file that points to the the script

---

### Post by kirilstankov on 2009-02-19
Thanks, 

but doesn't seem to work.
Tried syn link, hard link, script... nada...

Any other ideas,

thanks!](*,)

---

### Post by kirilstankov on 2009-02-20
The correct path is /usr/share/gnome/autostart.

Thanks!:D

---

