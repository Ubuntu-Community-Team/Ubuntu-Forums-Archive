---
title: "Custom default Xsession"
date: 2010-10-19
forum: Desktop Environments
---

### Post by Silver Doe on 2010-10-19
Hi, All!
I have installed slim login manager.
I configured it to autologin.
How do I change the default Xsession to awesome display manager?
I tried changing in slim.conf:
```

login_cmd           exec /bin/sh - ~/.xinitrc %session
# login_cmd           exec /bin/bash -login /etc/X11/Xsession %session

```
but the sound was gone, and cyrillic support too, and keyboard control also. So I switched back.
Everytime I start computer, slim chooses gnome (metacity) as the default manager.
I tried:
```
sudo update-alternatives --config x-window-manager
```
with no results.
How do I set awesome as my default Xsession?
The system is 10.10.

---

