---
title: "How Suspend after 2/3 hours"
date: 2011-11-27
forum: Desktop Environments
---

### Post by SushiAddiction on 2011-11-27
I desperately need to know how to Suspend/Hibernate after 2 or 3 hours. Does anyone know how I could do this?

Thanks. 

Also who do I message to get the power management app updated with the option to set whatever time you want.

edit> I'm trying 
```
sleepd -A -a -N -r 5 -l 0.01 -U 7200 -n -v
```IT SEEMS SLEEPD does not work with -A option for some reason so it's only good as a sleep timer :( 

I've also found out that the power management can't be set over 1 hour even with gcof-editor.
see>
[https://answers.launchpad.net/ubuntu/+question/39065](https://answers.launchpad.net/ubuntu/+question/39065)

EDIT> Installed xfce4-power-manager instead. It's so much better.

---

### Post by shubham1 on 2011-11-27
> **SushiAddiction said:**
> I desperately need to know how to Suspend/Hibernate after 2 or 3 hours. Does anyone know how I could do this?

Thanks. 

Also who do I message to get the power management app updated with the option to set whatever time you want.

edit> I'm trying 
```
sleepd -A -a -N -r 5 -l 0.01 -U 7200 -n -v
```I've also found out that the power management can't be set over 1 hour even with gcof-editor.
see>
[https://answers.launchpad.net/ubuntu/+question/39065](https://answers.launchpad.net/ubuntu/+question/39065)
install qshutdown
from software center

---

### Post by SushiAddiction on 2011-11-27
> **shubham1 said:**
> install qshutdown
from software center

I can't thank you enough.

I must have missed this before

---

### Post by oscarivera9 on 2011-12-11
This isn't quite what I was hoping it would be, but it's the closest I can get right now.  Prior to Ubuntu 11.10 we were able to have the computer suspend/shutdown after it was sitting idle for 2 or 3 hours.  Now, the default only waits at the most 1 hour while idle before shutting down/suspend.  For now, qshutdown will have to do.

---

