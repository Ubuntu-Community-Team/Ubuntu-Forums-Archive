---
title: "Beryl-settings crashes trying to set F6 to gnome-terminal"
date: 2007-01-23
forum: Desktop Environments
---

### Post by jsully1 on 2007-01-23
I'm trying to bind F6 to gnome-terminal with the latest version of beryl (1.99-2.0 beta2) but it crashes every time either entering F6 manually or doing grab key F6.  I can bind it to F7 with no issues, and I can bind other stuff to F6, such as scale.  Any ideas?  Is there any file I can manually edit the key bindings in directly?

Running beryl-settings from a command prompt then trying to bind F6 to command1 or command 2, which is set to gnome-terminal:

sully@sullyslaptop:~$ beryl-settings
Sending reload event...
Segmentation fault (core dumped)
sully@sullyslaptop:~$
Then I get a message that Python 2.5 has crashed.

---

### Post by jsully1 on 2007-01-23
Editing /home/user/.beryl/settings and setting a_run_command0__keyboard=F6 worked just fine ](*,)

---

