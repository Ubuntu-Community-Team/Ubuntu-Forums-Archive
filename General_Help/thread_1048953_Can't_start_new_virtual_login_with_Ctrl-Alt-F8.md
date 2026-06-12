---
title: "Can't start new virtual login with Ctrl-Alt-F8"
date: 2009-01-24
forum: General Help
---

### Post by acl123 on 2009-01-24
Hi, I am trying to change into a new gdm using Ctrl-Alt-F8 but it hangs after displaying a few messages, before reaching the login screen.

First it was hanging at the message "Starting Timidity..." so I thought it was maybe timidity causing the problem, but after removing timidity from /etc/init.d/ it still hangs (this time at the message before the timidity message - "Checking battery state").

Does anyone know how I can find out what is causing it to hang?

---

### Post by dcstar on 2009-01-24
> **acl123 said:**
> Hi, I am trying to change into a new gdm using Ctrl-Alt-F8 but it hangs after displaying a few messages, before reaching the login screen.

First it was hanging at the message "Starting Timidity..." so I thought it was maybe timidity causing the problem, but after removing timidity from /etc/init.d/ it still hangs (this time at the message before the timidity message - "Checking battery state").

Does anyone know how I can find out what is causing it to hang?

tty8 is the destination of start up messages, tty7 is where your X session runs.

---

### Post by acl123 on 2009-01-25
Ah ok - I was following the instructions here: [http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651)
I guess they must be wrong.

---

