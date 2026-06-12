---
title: "how do i make XDM load JWM rather than Xterm at login?"
date: 2008-10-20
forum: Desktop Environments
---

### Post by erlinux on 2008-10-20
how do i make XDM load JWM rather than Xterm at login?
i tried ~/.xinitrc, but i still start with xterm

---

### Post by fisherama on 2008-10-20
dont know sorry you should google it that can help

[project management](http://www.contractsystem.com/)

---

### Post by go_beep_yourself on 2009-07-21
What's in your .xinitrc? It should be

[PHP]exec jwm[/PHP]

Oh, and XDM doesn't read the .xinitrc file. What you should do is remove all graphical login managers, put that in your .xinitrc, and type startx after logging in through the command line.

---

