---
title: "Pekwm troubles"
date: 2005-11-03
forum: Desktop Environments
---

### Post by justin on 2005-11-03
I was able to install pekwm without any trouble, but I am unsure how to replace gnome with it. Any suggestions?

---

### Post by Juippisi on 2006-03-12
You could try adding PekWM to GDM-menu so everytime you log in you can choose between Gnome and PekWM. I think this works with GDM as well:

cd /usr/share/xsessions/
sudo vim pekwm.desktop
----------
[Desktop Entry]
Encoding=UTF-8
Name=PekWM
Comment=Log in using PekWM (Version 0.1.4)
Type=XSession
Exec=/usr/bin/pekwm
TryExec=/usr/bin/pekwm
----------

just change the paths.

---

