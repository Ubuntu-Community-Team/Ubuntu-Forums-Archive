---
title: "emacs server startup script in  KDE"
date: 2008-05-26
forum: Desktop Environments
---

### Post by KuroRyuu on 2008-05-26
I'm trying to run a small script at KDE startup to start an emacs session that I can use to connect all subsequent emacs instances to for quicker startups. the script works if I run it myself, but no matter where I put it, .xinitrc, .kde/Autostart/, etc, it won't start up at login.

here's the script to start it up:
```
#!/bin/sh
/usr/bin/dtach -n kuro /usr/bin/emacs -nw
```

I'm using dtach to emulate a screen session, it runs the program completely separate from wherever it's started from. Also, I'm using emacs-snapshot, it supports this multi-TTY behavior. Am I doing something wrong? any help would be greatly appreciated.

---

