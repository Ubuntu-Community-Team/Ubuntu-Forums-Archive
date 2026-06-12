---
title: "Brightness and lock not auto locking"
date: 2015-09-05
forum: Desktop Environments
---

### Post by ofrxnz on 2015-09-05
Hey,

So, I suspect this is my own fault for fiddling with gnome and xscreensaver (now removed).  

Currently, regardless of the settings in the 'brightness and lock' applet, it will never lock.  
I can lock it manually with Alt + Ctl + L

It feels like a config issue.  Though, there is a chance I removed the wrong package.  

I was wondering if anyone had any thought on how to restore the default lock behavior or knows a good place to start debugging.  
I'm not seeing any obvious failures in logs.  

I am currently running a fairly vanilla Ubuntu 15.04 with Unity.  

Thanks,

Adam

---

### Post by ofrxnz on 2015-09-05
So, some more info.  The screen sleep settings trigger just fine and result in a locked session.....

It appears to be limited to the lock timer settings.

---

