---
title: "Having issues with Nautilus"
date: 2009-02-24
forum: General Help
---

### Post by Kritner on 2009-02-24
hey guys, new Ubuntu 8.10 user here.  I've been attempting to setup apache, php, sql, and coldfusion... i've been able to do everything but the coldfusion, and it seems like every time i mess something up i need to reinstall the OS because something stops working.  There's got to be an easier way to get this set up.  Basically right now i'm not so worried about getting CF installed, but ever since 2 days ago, my nautilus has been giving me major issues.  
The issues i'm running into are the inability to make edits to root owned folders even when authenticated as root.  The program also hangs for 10 seconds at a time when trying to input data into the directory field, which also causes the rest of the system to hang.

Do we have any idea what could cause this? and how i can remedy it?

---

### Post by ibuclaw on 2009-02-24
Have you tried editing files without the use of Nautilus ?


ie:
```
sudo gedit /etc/test.conf
```
?

Regards
Iain

---

### Post by Kritner on 2009-02-24
> **tinivole said:**
> Have you tried editing files without the use of Nautilus ?


ie:
```
sudo gedit /etc/test.conf
```
?

Regards
Iain

that does indeed work, but why is nautilus not working? :P

---

### Post by ibuclaw on 2009-02-25
I am not the one to say why nautilus isn't working for you.
But, as a general rule, I use the least amount of administrative power when I work on my computer.

So, if I suddenly decide to install application X and a config file needs editing, then I use a text editor. There is no need really to run nautilus as root, if you think it through. :)

Regards
Iain

---

