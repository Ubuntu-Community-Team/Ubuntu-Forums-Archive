---
title: "After remote desktop session -background stuck"
date: 2009-01-17
forum: Desktop Environments
---

### Post by rcolson9333 on 2009-01-17
I have installed 8.10 server edition, then added the desktop environment, and Webmin.  
Under System-Preferences-remote desktop,  I clicked "disable wallpaper while connected" and started a TightVNC connection to the machine.  After ending my session,(I didn't like the resulting remote desktop look),I unclicked the "disable wallpaper" option and rebooted my machine.

Now when I login to the machine locally, the background did not return to normal (Ibex).  I miss the Ibex.  I go to appearances and try to change back to Ibex but it is already selected and not being used. Help Please.  Searched forums for "remote desktop" "stuck background" etc.

Thanks, Ryan

---

### Post by sarath_it on 2009-01-17
open gconf-editor

check /desktop/gnome/background/draw_background

---

### Post by rcolson9333 on 2009-01-17
> **sarath_it said:**
> open gconf-editor

check /desktop/gnome/background/draw_background

YOU GOT IT!.

Seriously, well done.  Ubuntu community rocks.

---

### Post by sarath_it on 2009-01-17
Glad I could Help!

---

### Post by killercow84 on 2009-02-05
Thank you verry much, is this a common bug?

i received it whit disabling and enabling the desktop background for remote users.


Thanks for the solution:D

---

