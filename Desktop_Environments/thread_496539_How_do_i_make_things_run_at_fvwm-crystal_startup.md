---
title: "How do i make things run at fvwm-crystal startup?"
date: 2007-07-09
forum: Desktop Environments
---

### Post by the music man on 2007-07-09
I want to run firestarter and x11vnc automatically after logging in into my fvwm-crystal desktop. In what file do i have to place the commands?

Firestarter needs to be run as root, and i don't want a password prompt at each boot, so i have this line in /etc/sudoers: ```
server ALL = NOPASSWD: /usr/sbin/firestarter
```
(my user is 'server') but it doesn't work. Sudo still asks for a password when i do ```
sudo firestarter
``` How do i solve this?

---

### Post by ChillMonkey on 2007-09-19
copy /usr/share/fvwm-crystal/fvwm/preferences/Startup

to

~/.fvwm-crystal/preferences/Startup

and edit as needed.

---

