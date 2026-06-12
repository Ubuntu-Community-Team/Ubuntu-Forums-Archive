---
title: "Start programs at Xfce (Xubuntu) login"
date: 2006-01-01
forum: Desktop Environments
---

### Post by stuporglue on 2006-01-01
I've got Xubuntu installed and want to always start up xscreensaver and gnome-volume-manager when I log in. I'm assuming there's a startup script somewhere, but I can't find it and .xinitrc didn't work. 

Thanks!

---

### Post by towsonu2003 on 2006-01-01
not sure if this would work but... login to xfce, start those two programs and log out xfce after telling it to save the session. next log in, you should have those two running (this works with gnome-terminal), check with: ps aux | grep partofprogramnamehere

---

### Post by stuporglue on 2006-01-01
> not sure if this would work but... login to xfce, start those two programs and log out xfce after telling it to save the session. next log in, you should have those two running (this works with gnome-terminal), check with: ps aux | grep partofprogramnamehere

It does work, but I'm not sure it's the best solution in this case. 

I'm giving this computer to a student who doesn't have a computer, and who has no linux experience. Since saved sessions settings are quite easily changed via the GUI, I'd rather stick gnome-volume-manager and xscreensaver somewhere a little more tamper-proof. 

Is my thinking reasonable, or would the saved session be the best bet?

Thank you!

---

### Post by vayu on 2006-01-01
xfce runs executables found in the ~/Desktop/Autostart directory upon startup.  Make a script that calls the programs you want and put it there.

---

### Post by stuporglue on 2006-01-02
> xfce runs executables found in the ~/Desktop/Autostart directory upon startup. Make a script that calls the programs you want and put it there.

It seems odd to me that there's not a dot folder or file somewhere to stick them, but that does work. Thank you!

---

