---
title: "GNOME FLASHBACK in Ubuntu 14.04 Set XDG_CURRENT_DESKTOP as Unity"
date: 2014-09-11
forum: Desktop Environments
---

### Post by Thomas6818 on 2014-09-11
Hello,

In Ubuntu 14.04, I am running the GNOME Flashback (metacity) desktop environment. It sets the value of environmental variable XDG_CURRENT_DESKTOP as Unity. See the output of printenv, 

```
$ printenv | grep XDG
XDG_VTNR=7
XDG_SESSION_ID=c4
XDG_GREETER_DATA_DIR=/var/lib/lightdm-data/foo-user
XDG_MENU_PREFIX=gnome-flashback-
XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session1
XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
XDG_CONFIG_DIRS=/etc/xdg/xdg-gnome-fallback:/usr/share/upstart/xdg:/etc/xdg
XDG_SEAT=seat0
XDG_DATA_DIRS=/usr/share/gnome-fallback:/usr/share/gnome:/usr/local/share/:/usr/share/
XDG_RUNTIME_DIR=/run/user/1000
XDG_CURRENT_DESKTOP=Unity
```

I compared the output of printenv with that in Ubuntu 13.10. The latter (Ubuntu 13.10) does set XDG_CURRENT_DESKTOP as GNOME.

```
XDG_VTNR=7
XDG_SESSION_ID=c2
XDG_MENU_PREFIX=gnome-
XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0
XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
XDG_CONFIG_DIRS=/etc/xdg/xdg-gnome-fallback:/usr/share/upstart/xdg:/etc/xdg
XDG_SEAT=seat0
XDG_DATA_DIRS=/usr/share/gnome-fallback:/usr/share/gnome:/usr/local/share/:/usr/share/
XDG_RUNTIME_DIR=/run/user/1000
XDG_CURRENT_DESKTOP=GNOME
```

I am wondering if this is a bug, or an intentional choice -- I would believe that the value of XDG_CURRENT_DESKTOP should be GNOME when I am running the GNOME flashback/fallback environment.

At present, as a result that Ubuntu 14.04 sets the variable to be Unity, I have a probem with VMware Unity mode. I am running Ubuntu 14.04 as a guest OS using VMware. Leaving the variable value unchanged, I cannot enter VMware Unity mode. When I manually set the variable to GNOME, I can enter VMware Unity mode; but it does not sound like a correct thing to do.

---

### Post by ibjsb4 on 2014-09-11
XDG_CURRENT_DESKTOP=Unity

I get the same thing on my Flashback install.  I suspect this is because flashback now has Unity dependencies.

[ATTACH=CONFIG]256386[/ATTACH]

I am running it in VirtualBox and not familiar with VMware.

---

### Post by dragon-788 on 2015-03-02
ibjsb4 is correct, it definitely appears there are some dependencies. This also affects VMware's Unity mode because it isn't reporting Gnome so it won't work. You can use the steps in this blog post to correct VMware Unity working with Ubuntu Gnome-fallback-session. [http://notesofaprogrammer.blogspot.com/2014/09/ubuntu-1404-trust-and-vmware-unity-mode.html](http://notesofaprogrammer.blogspot.com/2014/09/ubuntu-1404-trust-and-vmware-unity-mode.html)

---

