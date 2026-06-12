---
title: "Conky on Startup"
date: 2009-04-15
forum: Desktop Environments
---

### Post by LesterPalooza on 2009-04-15
I have tried this guide:

[http://ubuntuforums.org/showthread.php?t=386078&highlight=conky+start]("http://ubuntuforums.org/showthread.php?t=386078&highlight=conky+start")

but it doesn't work for me. **I am using Ubuntu Intrepid Ibex 8.10 and I am using Beryl/Compiz/ccsm**

How to run conky on startup? Any ideas?

---

### Post by ostrm on 2009-04-15
Is conky actually running? What does 
```
ps ax | grep conky
```
tell you?

If it is running, you could play with own_window_type in .conkyrc. The following lines do it for me:
```

# use own window
own_window yes
own_window_type override # possible values: default, desktop, override

# reduce flicker 
double_buffer yes 

```

---

### Post by gjoellee on 2009-04-15
Can't you just add Conky to your session? 

System->Preferences->Session, then click on "Add". Name it whatever you want, then on the command write: ```
conky
```
and then click on "OK" or whatever it says. 

The next time you log in conky should start.

---

### Post by LesterPalooza on 2009-04-16
I tried adding conky to the Startup programs.

By the way, I am running Compiz too. Everytime I add something in the startup programs list, it just disappears after I close the list.

---

