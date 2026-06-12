---
title: "shutdown pc from gdm using keyboard"
date: 2011-07-27
forum: Desktop Environments
---

### Post by mehturt on 2011-07-27
Is it possible to shutdown pc from gdm login screen using just keyboard?

---

### Post by kaspar_silas on 2011-07-27
Not as far as I can see as tab doesn't switch focus on my machine anyway.

You could:
Press Ctrl+Alt+F1 to switch to a text terminal.
Login then do a standard
$ sudo shutdown -h now

but I would guess your are actually trying to avoid logging in at all right?

---

### Post by mehturt on 2011-07-27
Yes.  Actually I have a TV card which has a remote control.  This remote control has a 'power off' button which invokes the shutdown/suspend/hibernate/... dialog of GDM, but I'm not able to simulate this using keyboard.
The problem is I can't use the remote control, since after an upgrade from 10.10 the remote control started to send in each key twice, but that's a different issue.

---

