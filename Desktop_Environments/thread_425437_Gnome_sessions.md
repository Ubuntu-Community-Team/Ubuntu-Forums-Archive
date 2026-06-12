---
title: "Gnome sessions"
date: 2007-04-27
forum: Desktop Environments
---

### Post by teHIngo on 2007-04-27
Hey guys,

I'll keep it short:

A few days ago I saved a session in ubuntu, just to check out what happened (System -> Preferences -> Sessions). 
However, now, with a delay of maybe 2-3 minutes, the same windows show up on every single system startup.

How can I get rid of that?! :)

Thanks in advance! :)

---

### Post by mannheim on 2007-04-27
There's a bug-report on this in [launchpad]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/34321"). You need to turn off auto-saving of sessions (if it is enabled), and then delete ~/.gnome2/session. I'm quoting from the bug-report; I haven't tried this.

---

### Post by lw5 on 2007-04-27
I think it's actually the .session file in your home dir you should delete. You could also just empty your desktop and 'save your current session' once again, just the way you like it :)

---

### Post by teHIngo on 2007-04-28
Thanks, this worked! :)
Hopefully this bug will be fixed in gusty!

---

### Post by kaede on 2007-04-29
hi, anyone know what is default program for gnome?
recently i just remove all of my session program. because of desktop effect problem
now i need help about what is the default program for starting up ?

such as metacity, nautilus, gnome-panel. anyone?

---

