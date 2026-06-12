---
title: "SU Menu App?"
date: 2009-12-06
forum: Desktop Environments
---

### Post by VcDeveloper on 2009-12-06
How do you create a su app in the menu?  I'm unable to login at the term prompt?  Why does Xubuntu make it hard to use su mode?  I keep getting a failed login?  It seems the only way you can use any su apps is by a dialogbox!...

---

### Post by lisati on 2009-12-06
For starters, I'd recommend (gk)sudo in place of su.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aysiu on 2009-12-06
Create a launcher for the command ```
gksudo thunar
```

---

### Post by VcDeveloper on 2009-12-07
Well, that does work, but when you use certain apps like editors you get a lot of file ownership error like these:

> 
administrator@anointed-server:~$ sudo kate
[sudo] password for administrator: 
Error: "/var/tmp/kdecache-administrator" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-administrator" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-administrator" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-administrator" is owned by uid 1000 instead of uid 0.
kdeinit4: Shutting down running client.
kdeinit4: preparing to launch /usr/lib/libkdeinit4_klauncher.so


.....  So I rather create a su app from the menu so it can create it's own config files.

---

### Post by VcDeveloper on 2009-12-07
Ok, I will give that a try!... also, I got a clean execution with gedit, so I'm aussming Ubuntu is mainly a gnome OS?  Is there a gnome flavor of kate?  kate is really advance and I like it!

---

### Post by aysiu on 2009-12-07
You're not supposed to use *sudo* with graphical applications.

Use ```
kdesu kate
``` not *sudo kate* and ```
gksudo gedit
``` not *sudo gedit*

---

### Post by VcDeveloper on 2009-12-07
Thanks for the help, but I would still like to create my own menu apps.   So where can I get doc's showing me how?

---

### Post by aysiu on 2009-12-07
> **VcDeveloper said:**
> Thanks for the help, but I would still like to create my own menu apps.   So where can I get doc's showing me how?
I don't have Xfce in front of me.

This may help:
[http://www.xfce.org/documentation/4.2/manuals/xfdesktop#xfdesktop-menu](http://www.xfce.org/documentation/4.2/manuals/xfdesktop#xfdesktop-menu)

---

### Post by VcDeveloper on 2009-12-07
Thanks you so much!

---

