---
title: "Gnome Terminal"
date: 2010-11-15
forum: Desktop Environments
---

### Post by ricpat51 on 2010-11-15
Hi,
Why the auto-completion command with tab key in a gnome terminal window on maverick is not working? Is it a configuration or something?

thanks in advance to everyone and sorry for my English! :frown:

---

### Post by deconstrained on 2010-11-16
The first thing I'd try: 'echo $SHELL'. If that doesn't return /bin/bash or some other shell program that supports completion, you can change it to bash (one shell that supports completion) via 'sudo usermod -s /bin/bash [username]'. If your login shell is bash already, the next thing to try is 'sudo apt-get install --reinstall bash-completion' and/or 'sudo dpkg-reconfigure bash-completion'.

---

### Post by ricpat51 on 2010-11-16
> **deconstrained said:**
> The first thing I'd try: 'echo $SHELL'. If that doesn't return /bin/bash or some other shell program that supports completion, you can change it to bash (one shell that supports completion) via 'sudo usermod -s /bin/bash [username]'. If your login shell is bash already, the next thing to try is 'sudo apt-get install --reinstall bash-completion' and/or 'sudo dpkg-reconfigure bash-completion'.

Thank you very much mate. I'll try it when I'm home.

---

### Post by ricpat51 on 2010-11-19
Well I tried what I was told to do in the previous replies but it didn't worked.
The weird thing is that in text mode the auto-completion works fine. The problem occurs only in terminal window on desktop mode.
Could it be a gnome bug???

Please any help will be very welcome.

Thanks in advance.

---

