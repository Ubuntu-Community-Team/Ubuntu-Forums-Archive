---
title: "[SOLVED] problem with Screenlets"
date: 2008-03-11
forum: Desktop Effects &amp; Customization
---

### Post by mikepac69 on 2008-03-11
Hi all,

Newbie here to Ubuntu. (Microsoft guy).  I recently installed Screenlets on my Ubuntu Gutsy.  I am trying to load the screenlets but nothing starts. I installed with no errors. I go into the manager and see all the screenlets, but when I choose to start them, nothing happens...

Any ideas? I am also running Compiz and AWN on my system.  I have a Dell 6400 Inspiron.

Any way to debug this?

Thanks for your help,

Mike

---

### Post by FuturePilot on 2008-03-11
How did you install them? 
Try running
```
screenlets-manager
```
from a terminal and then try to start some screenlets and see if there are any errors.
Applications&#8594;Accessories&#8594;Terminal

---

### Post by mikepac69 on 2008-03-11
this is what I get:

[I]It looks like you are running gnome
Error - Please install python image module
/home/michael/.config/autostart/Screenlets Daemon.desktop
/home/michael/.config/autostart/screenlets-daemon.desktop
False
Starter already exists.
DAEMON FOUND!
Quit!
[/I]


What Do I do?

---

### Post by mikepac69 on 2008-03-11
ok, I got it working. I had a permission problem and I installed Python...

Thanks for the help!!!

---

