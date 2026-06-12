---
title: "Compiz Locks up after logging in."
date: 2008-02-09
forum: Desktop Environments
---

### Post by demoric on 2008-02-09
**System Info:** I have Ubuntu 7.10 "Gutsy Gibbon" installed on a Dell 1525 Insprion laptop.

**Cause of Problem:** I was playing with some Compiz Settings specifically the water effect and it locked up my desktop.  I believe it is a conflict between the water effect plugin, and the  mouse over transparency accesability effect (sorry don't remember what it's called).  When there is a prompt telling me to disable something the whole system freezes. [I] I'll see if I can repeat this after I find out how to fix it to see if it's a bug.
[/I]
**Current Problem:**  I have the setting enabled to resume all the windows when I log in.  When I log in after a couple of windows are loaded successfully  the system locks up.  CTRL+ALT+Backspace will only give me a black window, and a wait icon that is stuck in the center screen.

**Solutions sought for Current Problem: ** 
[LIST]
[*]I would like to know how to reset my compiz settings.
[http://ubuntuforums.org/showthread.php?t=259831](http://ubuntuforums.org/showthread.php?t=259831) didn't work for me as I don't seem to have /home/yourname/.compiz/csm_settings Although, I didn't try the apt-get install, and dpkg --purge as these seem to be releated to an older version of ubuntu when compiz wasn't enabled by defautlt. (Fiesty maybe).

[*]Another thing that might help is knowing how to turn off the resume programs at startup option from the shell.
[/LIST]

Any help is appreciated.

---

### Post by RudolfMDLT on 2008-02-09
I hope you don't have auto user login enabled?

Anyway - at the login screen, select "session", and select "Failsafe Gnome". This will bypass all custom config files and you should be able to use the Compiz GUI to reset your settings.

Cheers,

Rudolf

---

### Post by demoric on 2008-02-09
Thank you. That enabled me to reset it.

---

