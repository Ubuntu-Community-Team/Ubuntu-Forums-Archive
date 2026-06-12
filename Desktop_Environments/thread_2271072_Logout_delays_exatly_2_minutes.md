---
title: "Logout delays exatly 2 minutes"
date: 2015-03-27
forum: Desktop Environments
---

### Post by wkoell on 2015-03-27
Hi!

I freshly installed 64bit 14.04 Lubuntu and one strange thing bothers me. When i click on logout in menu, it takes exactly 2 minutes to bring up logout dialog. During this time machine is very laggish, it is hard to change open windows, responsiveness is very low. And exactly after 2 minutes pops out logout dialog and I may choose logout/restart/whatever...

I figured out that runned command is "lxsession-default quit" and straced it. strace reached nicely to exit and during next 2 minutes nothing happened.

What may be wrong here?

Tia,

Gunnar

---

### Post by CantankRus on 2015-03-27
Are you running anything else other than default apps?
eg plank or cairo-dock

---

### Post by wkoell on 2015-03-28
No, nothing special, pretty standard install from mini-CD and then ```
apt-get install lubuntu-desktop
```

---

### Post by andy.drummond on 2015-07-28
try 

apt-get install lxsession-logout

this made the menu work for me

---

### Post by claracc on 2015-07-29
Exactly the same problem with ubuntu 14.04.2 ubuntu gnome flashback. Logout button takes more than two minutes to do action.

If I use xterm and run the order ```
gnome-session-quit
``` the logout takes place inmediatly.

I think it is a problem with certain desktops, but I haven't find any workaround or explanation for such a weird behaviour.

---

