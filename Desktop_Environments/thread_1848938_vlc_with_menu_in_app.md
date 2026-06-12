---
title: "vlc with menu in app ?"
date: 2011-09-23
forum: Desktop Environments
---

### Post by ottosykora on 2011-09-23
I am just trying to make vlc player to launch so that it contains the menu in the app itself and not on the top in the panel.

While the global menu on the top can be good idea with things like browser or similar, it is not useful in apps like vlc which have small GUI size and are often pplaced somewhere in the corner.

I tried to follow:
[http://askubuntu.com/questions/6784/is-it-possible-to-make-indicator-appmenu-ignore-a-specific-application](http://askubuntu.com/questions/6784/is-it-possible-to-make-indicator-appmenu-ignore-a-specific-application)

but somehow no luck.

UBUNTU_MENUPROXY= vlc 

does not help, still all on the top

setting both=1 works however, could be an oprtion.

But somehow I can not manage to set it so it works permanently.

---

### Post by mc4man on 2011-09-23
simplest way for all ways to open vlc - remove the global menu for qt4 apps
```
sudo apt-get remove appmenu-qt
```

To just fix vlc (exception opening from a terminal
```
gksudo gedit /usr/share/applications/vlc.desktop
```
scroll down & find the Exec=vlc %U line, edit it to this - see screen
```
Exec=env QT_X11_NO_NATIVE_MENUBAR=1 vlc %U
```

To adjust vlc from cli  - ask..

---

### Post by ottosykora on 2011-09-23
OK thanks, did not know this is qt4 , it simply did not work with the menuproxy at all.


And I think this should be definitely made to some GUI function, as definitely user should be able to configure the menu behaviour for each app himself some easy way.

So far I am trying to do it the recomended way, copying all the desktop files in question to the .local, but all that is lot of work .

As for number of programs the top menu is useful, those which anyway force open full screen, like browsers or office etc, it is nice to keep the functionality and not uninstall it completely.

But many programs are simply not made for that and need the menu inside the app.

Have just set up launcher for gedit too, as it also needs the menu 'inside'. Here all worked with UBUNTU_MENUPROXY however.

But to do this for all apps by hand is a pain.

---

### Post by mc4man on 2011-09-23
I generally move the menus back to apps for all my gui A/V players, (vlc, audacious, umplayer ), gedit, gnome-terminal, a few others.

If it wasn't for the appmenu on Desktop focus I'd probably just get rid of them altogether
(the appmenu has a small, fairly insignificant mem leak in 11.04, ATM there is a fairly decent sized one in 11.10

---

