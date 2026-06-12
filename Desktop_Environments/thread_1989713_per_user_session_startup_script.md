---
title: "per user session startup script"
date: 2012-05-28
forum: Desktop Environments
---

### Post by el_baby on 2012-05-28
Hi,

is there a 'per user' script (like, within ${HOME}) that gets executed whenever I start a graphical (unity) session?

.profile and .bash_rc are run if I start a shell, but not when I log in graphically (at least in precise).

If I undrestand correctly, the programs pointed by entries in /etc/xdg/autostart are run for ALL users.

What I'm looking for is some kind of ${HOME}/.unity.rc or whatever name where I can run commands on graphical session startup.

TIA

---

### Post by brainwash on 2012-05-28
This one here is the user specific autostart folder:
```
${HOME}/.config/autostart
```

---

### Post by el_baby on 2012-05-28
thanx a lot for your help, brainwash.

---

