---
title: "Login restarts after successful login..."
date: 2008-08-14
forum: Desktop Environments
---

### Post by esrise on 2008-08-14
...ok, i log in at the standard Kubuntu login screen, then, after entering accurate credentials, one of two things happens, 1) the computer goes to a black screen where text can be inputted [but no commands], or 2) the computer goes back to the login screen. either way, i cannot access my computer visually. I've kept on restarting and restarting xserver, but this persists. any help much appreciated!!

---

### Post by phidia on 2008-08-14
Wherever you end up with this cycle press the Alt+Ctrl+F1 (or F2-F7 function keys)
That should open a tty for you that you can enter commands in. You can try "startx" Record any error messages and/or check the logfiles /var/log/dmesg; messages; xorg.0.log   Paste relevent outputs back here.

---

### Post by esrise on 2008-08-14
ok... this is what came up...

Fatal Server Error:
Server is already active for display 0
     If this server is no longer running, remove /tmp/.XO-lock
     and start again

No protocol specified
giving up.
xinit: resource temporarily unavailable (errno 11): unable to connect to X server
xinit: No such process (errno 3): Server error.

---

### Post by buntu_hugenewbie11 on 2008-09-17
Did you ever find a solution to this?

---

