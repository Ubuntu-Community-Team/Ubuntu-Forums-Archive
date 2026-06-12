---
title: "GDM Issues - Unable to read .ICEauthority"
date: 2005-07-07
forum: Desktop Environments
---

### Post by keyshawn on 2005-07-07
hey,

I had a problem exactly the same as steve did in this thread - [http://ubuntuforums.org/showthread.php?t=1209]("http://ubuntuforums.org/showthread.php?t=1209")
however, I did follow the instructions, and I'm still having the same problems as described in his problem.

btw, my .xsession-errors log is 
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "myusername"
/etc/gdm/Xsession: Beginning session setup...

** (gnome-session:9909): WARNING **: Unable to read ICE authority file: /home/myusername/.ICEauthority

``` 

and the ownership line on the .ICEauthority is:
 ```
-rw-------  1 myusername myusername 2868 2005-07-06 21:41 .ICEauthority

``` 

I tried to reply in the previous thread mentioned above, but vbulletin said I didn't have access to preview the page. Ah well. 

Thanks for any help in advance,
skora.

EDIT: Ah...silly me ! I should have restarted the computer after following the directions in the other thread. It's all good here now !

---

