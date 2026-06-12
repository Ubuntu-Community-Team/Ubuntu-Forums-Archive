---
title: "How to start Emerald with Compiz-Fusion"
date: 2007-08-23
forum: Desktop Environments
---

### Post by Netsurfer on 2007-08-23
After installation of Compiz-Fusion and Emerald (you can find guides in this forum) edit compiz starter (make a copy):

**sudo gedit /usr/bin/compiz**

change line **238** and **240**
 from "/usr/bin/gtk-window-decorator" to "**/usr/bin/emerald**"

save file.

This is an extract of the file:

[COLOR="Red"]# start the gtk-window-decorator if present
if [ -x /usr/bin/gtk-window-decorator ] && [ -n "$GNOME_DESKTOP_SESSION_ID" ]; then
	      /usr/bin/emerald --replace &
elif [ -x /usr/bin/kde-window-decorator ] && [ -n "$KDE_FULL_SESSION" ]; then
             /usr/bin/emerald --replace &
	FALLBACKWM="/usr/bin/kwin"
fi[/COLOR]

To check the patch run Alt+F2 and write "compiz --replace". 
If all is ok you will see the correct emerald theme active.

Bye

Last Minute. 
Using Trevino repository for installation you have to add "compiz --replace -c emerald" only to start session.

---

### Post by Chymera on 2007-08-23
or, without editing any files you can just remember the following 2 commands
```
emerald --replace &
```
```
compiz --replace &
```
and you get the advantage that if you get a bug you dont have to edit the launcer again to launch compiz alone in order to find out it the bug is with emerald or compiz.

---

