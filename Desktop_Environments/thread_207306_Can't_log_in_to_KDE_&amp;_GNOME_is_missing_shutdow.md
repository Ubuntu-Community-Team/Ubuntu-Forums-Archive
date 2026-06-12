---
title: "Can't log in to KDE &amp; GNOME is missing shutdown and restart options"
date: 2006-07-01
forum: Desktop Environments
---

### Post by ewl1217 on 2006-07-01
I installed the kubuntu-desktop package today to try out KDE and I've been having two odd issues. I'm using KDM rather than GDM, if that makes any difference.

First, when I try to log in to KDE I get an error that goes like this:
```
Could not start kstartupconfig. Check your installation.
``` I click "ok" on the error box, and it takes me back to KDM.

Also, I don't know if this is related or not, GNOME is missing the options to shutdown and restart my computer. I only have the options to log out, lock the screen, switch users, and hibernate.


**EDIT:** I included the actual error message. I couldn't remember it at first.
**EDIT (again):** I've been using the default Ubuntu installation (with the ubuntu-desktop package), and I installed kubuntu-desktop on top of this installation. I was just thinking about this, and decided that was an important point to mention.
**Yet another EDIT:** I was able to fix the KDE issue. Apparently when I installed Google Earth it created my /~/.kde directory as root,so I removed this and everything worked. I'd still like some help on the GNOME issue though.

---

### Post by ewl1217 on 2006-07-01
I hate to do this, but oh well...

BUMP

---

### Post by DanWoz on 2006-07-02
As far as your GNOME problem, go to System> Administration> Login Window and make sure under the Menu Bar that the Show actions menu is checked. That should add the shutdown and restart.

---

