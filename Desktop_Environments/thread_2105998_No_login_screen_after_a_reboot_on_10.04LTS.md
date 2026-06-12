---
title: "No login screen after a reboot on 10.04LTS"
date: 2013-01-17
forum: Desktop Environments
---

### Post by JohnsonMR on 2013-01-17
I'm using a version of 10.04LTS as a printer server.  I had a print job that was stuck in the queue an unable to cancel/delete through my normal methods.  So I opened a command prompt and entered "cancel -a" which worked.  But when I then rebooted I'm left with no login prompt.  What do I need to do to fix this?

I guess I should add that I'm using the desktop version and not the server version.  After the reboot I can see the wallpaper without the login dialog to enter a username or password.  I'm also not able to login remotely or mount a shareable disk (at least at this point).

---

### Post by ajgreeny on 2013-01-17
The command ```
who
``` will tell you if anyone is logged already after the reboot.

---

