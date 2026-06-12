---
title: "can't login anymore"
date: 2005-02-25
forum: Desktop Environments
---

### Post by doni on 2005-02-25
hi there...

if i type in my name and pw in gdm it logs me out and sais "your session wasn't longer than 10 secons" or something like that.

error in .xsession-errors:
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "aaron"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxfce4: X server already running on display :0
Agent pid 5275
xfce4-session: Unable to access file /home/aaron/.ICEauthority: Keine Berechtigung
Agent pid 5275 killed
``` 

i tried to copy the ICEauthority file from my other user (which i created newly, i can login with him)...but that didn't work....

how can i fix that?
thanks

doni

---

### Post by doni on 2005-02-25
aahh I've fixed in.

copied my .ICEauthority from a new made user over to /home/aaron 
and owned it by me using 

```
chown aaron .ICEauthority
``` 

and it works :D

thanks ubuntuforums!

---

