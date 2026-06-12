---
title: "Can not log on, xsession-error"
date: 2006-10-06
forum: Desktop Environments
---

### Post by jae1227 on 2006-10-06
I was trying out this way to use the back button on mouse. 

[URL="http://www.ubuntuforums.org/archive/index.php/t-28374.html"]

Then after I did control ALt Backspace and tryed to log on I could not. It said to look at your .xsession-errors file , well i looked at it and it did not make to much sence. It must be from something stupid ](*,)  I did when i was trying to do this mouse thing.

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "justin"
/etc/gdm/Xsession: Beginning session setup...
xmodmap:  commandline:1:  bad number of buttons, must have 9 instead of 7
xmodmap:  1 error encountered, aborting.
```

---

### Post by arkangel on 2006-10-06
in the  xorg.conf you have edited 
what happens if you cahnge this line
**Option "Buttons" "7"**
to 
**Option "Buttons" "9"**

to edit from console 

**sudo nano /etc/X11/xorg.conf**


if that doesnt work
you have a back up of your  xorg.conf?  
just restore or undo what you have done 

if yo dont have a bk in the /etc/X11/  directory  there is a xorg.confxxxx,  chosee the most recent , to know the modification date  type in your console 
**ls -l**
and then pick one 
[B]sudo mv xorg.confxxx  xorg.conf 
startx[/B]

---

### Post by jae1227 on 2006-10-06
Hey i did not try your suggestion but i did install xubuntu-desktop package and now it works. I'll tell you if the back button now works or not

---

