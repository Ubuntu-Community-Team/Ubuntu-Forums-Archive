---
title: "How to automate updates"
date: 2006-01-31
forum: Desktop Environments
---

### Post by smullie on 2006-01-31
Hallo All,

Is it possible to run and execute te updates automaticly, perhaps in the backround?
The users on the computers has no rights to update and now i have to go to all the workstations to update the systems.
Is there a way 'aka windows' that the users them selves can execute the updates without knowing the sudo/root password, so it stays secure?

All the help is welcome.

Richard.

---

### Post by nocturn on 2006-01-31
You could do this with a cron script (search the forum for documentation).
But you do risk breakage, specially when the system is shutdown during something important like a kernel upgrade.

---

### Post by smullie on 2006-01-31
So i can run such a script also on bootup?

---

### Post by nocturn on 2006-01-31
[QUOTE=smullie]So i can run such a script also on bootup?[/QUOTE]

Yes, you could do so.  Or run it on shutdown (which may even be a better option since updates that require a reboot actually get it).

If you set update manager to download updates daily, it should last only as long as the installation of the packages.

To do this, search one of the cron scripts and adapt it to behave like an init script (look in /etc/init.d at the others).

---

### Post by smullie on 2006-01-31
OK, i will have a look , Thanks!

---

