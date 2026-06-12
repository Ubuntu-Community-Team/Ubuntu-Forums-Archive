---
title: "how to reset desktop/gnome/compiz settings to default ?"
date: 2011-09-22
forum: Desktop Environments
---

### Post by Andre-D on 2011-09-22
I am having problems with windows freezing after few hours of run time.  Locking desktop, may also be slow, and unlocking as well.
sometimes when a new window opens, everything flashes and freezes for a minute.

I'd like to reset(delete) all my compiz/gnome/unity settings and start over with clean/default settings.
how do I do that ? (what to delete?)

this is on a 11.10, (an upgraded 11.04)

---

### Post by ajgreeny on 2011-09-22
To reset compiz and unity in 11.04 you need the two commands:-
```
gconftool-2 --recursive-unset /apps/compiz
```followed by                    ```
unity --reset
``` so I assume the same in 11.10.  However the change to gnome3 may have changed everything so be prepared to troubleshoot if it doesn't work.

---

### Post by Krytarik on 2011-09-22
Before you do something harsh like that, I'd check if those issues are present in a fresh, new user profile, too. Especially reg. the Gnome part.

Greetings.

---

### Post by Andre-D on 2011-09-22
nice, thank you.

---

### Post by ajgreeny on 2011-09-22
> **Andre-D said:**
> nice, thank you.
So, can we assume that those two commands worked without a problem?  It is nice to know for future reference.

---

### Post by Andre-D on 2011-09-22
yes, commands worked. 
whatever that solved the problem, or still may be caused because I use the beta, well... I will know that tomorrow.

---

