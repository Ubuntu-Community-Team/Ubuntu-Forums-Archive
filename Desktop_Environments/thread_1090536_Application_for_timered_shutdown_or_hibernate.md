---
title: "Application for timered shutdown or hibernate"
date: 2009-03-08
forum: Desktop Environments
---

### Post by hyapadi on 2009-03-08
I used to use an application for shutdown in Vista
[http://www.vistashutdowntimer.toflo.de/](http://www.vistashutdowntimer.toflo.de/)

Is there any equivalent to it?

Thanks

---

### Post by binbash on 2009-03-08
gshutdown

---

### Post by chubble10 on 2009-03-08
You can set the alarm clock thing to shutdown when the alarm goes off

---

### Post by warp99 on 2009-03-08
You don't need an application since there's already one:

```
sudo shutdown -h +90
```

This will shutdown the computer in 90 minutes. You can also set this up as a crontab and shutdown at a specific time or date. 

You don't need a GUI for a simple one line command.

---

### Post by hyapadi on 2009-03-09
Thank you for the suggestions!

Gshutdown is very similar to what I have looking for.
It will be better if it has option for scheduled hibernate, since shutdown will shutdown all the running software as well.

Thanks guys.

---

