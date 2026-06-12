---
title: "Help on Programs on startup"
date: 2009-06-19
forum: General Help
---

### Post by dsdeiz on 2009-06-19
Hi! What I want to do is simply do 'xsetroot -solid midnightblue' after my window manager (w/c is xmonad) is executed. I tried creating a file ~/.xsession and just added that command there but no luck. I also tried ~/.xinitrc, added command, still no luck. I tried 'chmod +x ~/.xinitrc' and 'ln -s ~/.xinitrc ~/.xsession', still no luck. I tried modifyingn /etc/X11/Xsession, still no luck.. Any ideas what is wrong? :confused:

Thank you.

---

### Post by jhannah on 2009-06-19
Do you have a shebang line in your .xinitrc? If not, just prepend the below and see if it does the trick:

```
#!/bin/sh
```

If that doesn't work, you can also try to modify the system wide xinitrc file in /etc/X11/xinit/xinitrc. It's worth noting that the system wide xinitrc file is not used if a .xinitrc is found in the user's home directery.

---

