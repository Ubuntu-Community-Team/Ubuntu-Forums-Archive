---
title: "Alas my Gnome-Classic Top Panel is back"
date: 2012-03-05
forum: Desktop Environments
---

### Post by bturrie on 2012-03-05
I'm running 11.10 Gnome-Classic session with AWN as my launcher. I had removed the top bar some time back by editing /usr/share/sessions/gnome-session (and the gnome-fallback file) taking panel out of the list of required components. Then today I did an update. The top panel is back but it's still not listed as a required components in the gnome-session file.

So, is there any way to get rid of it now?? It's not really hurting anything, but I never use it and my desktop looks better without it.

---

### Post by Krytarik on 2012-03-05
I'll happily presume that you are not exactly having Gnome Panel up there now, but the Global Menu of Nautilus; to disable Global Menu completely in any non-Unity sessions, just run:
```
echo '[ ${DESKTOP_SESSION#ubuntu} = $DESKTOP_SESSION ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy
```You need to relogin for the change to take effect. If you want to revert that later, just remove the created file.

Regards.

---

### Post by bturrie on 2012-03-05
That did it. Thanks!

---

