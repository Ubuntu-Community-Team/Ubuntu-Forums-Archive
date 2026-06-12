---
title: "system moniter not opening"
date: 2009-05-30
forum: General Help
---

### Post by MimziM on 2009-05-30
sometimes an application, in gui, will have have
to close but continue to struggle in the
background.  normalyl you cam then open 
system moniter and kill the process,.

My problem is sometimes the system moniter gui wont open
must i then go to a terminal and if so how would i kill 
selected proccesses

---

### Post by drs305 on 2009-05-30
You can kill apps with
```

killall <appname>  # example:  killall firefox
*or find the PID*
ps -u *username*  # or "ps  aux" for all including root
*then*
kill -9 PID   # example  "kill -9 8876"
```
Include "sudo" if it's a root run app.

Don't forget there is also the "Force Quit" gui, which you can place as a shortcut on the panel via rt click, Add to Panel, Force Quit.

---

