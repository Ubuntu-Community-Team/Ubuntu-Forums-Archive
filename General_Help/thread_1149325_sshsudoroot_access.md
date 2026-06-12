---
title: "ssh/sudo/root access"
date: 2009-05-05
forum: General Help
---

### Post by christian.ry on 2009-05-05
Dear all,

this is a question about ssh/sudo, if anyone knows a more appropriate place for this (instead of the general forum) please let me know, I'll post there.



I need to execute a script on an ubuntu-server with root rights. With my old debian-box, using putty, this was a one-click operation from windows.
[login password-less with ssh2, calling the sh-script as root -> done]

Now that I switched to ubuntu, I cannot do this anymore. Sudo->root does not work without the need to enter the password.

I can log in via putty without password, but I'll end up with only USER-rights, and there is no way to execute the script as root without entering the password. 



Any Ideas?
Thanks
- Christian

---

### Post by slakkie on 2009-05-05
Check the NOPASSWD directive in sudo. 

eg:

youuser ALL=(root) NOPASSWD: /path/to/script

This prevents that you are prompted for a password when running /path/to/script.

Good luck!

---

### Post by christian.ry on 2009-05-06
That worked - thanks a lot!!
Christian

---

