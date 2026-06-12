---
title: "Kubuntu xgl - compiz not working"
date: 2006-08-28
forum: Desktop Environments
---

### Post by ouroboros1827 on 2006-08-28
I've been following a LOT of guides lately, and [this]("http://www.linuxjournal.com/node/1000081") is the one that got compiz working for me (I've deviated a bit from that one, though, according to other guides' advice). It was working great for a little bit, until I opened Kaffeine to play a movie clip, then compiz disappeared. Never got it back, even after logouts, X restarts, and reboots...can't figure this one out on my own.

I'd be willing to try *anything* lol. I might get this straight in a little bit and post back...this is almost a complete HOWTO lol

/etc/apt/sources.list
```
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb http://ubuntu.compiz.net/ dapper main
deb http://media.blutkind.org/xgl/ dapper main

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://www.getautomatix.com/apt kubuntu main

```
the relevant portion of /etc/kde3/kdm/kdmrc:
```
ServerCmd=/usr/bin/Xgl -br -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
```
~/.kde/Autostart/compiz.desktop:
```
[Desktop Entry]
Encoding=UTF-8
Exec=compiz --replace decoration wobbly fade switcher minimize cube rotate zoom scale move resize place & gnome-window-decorator &xmodmap -e "keycode 22 = BackSpace" &
GenericName[en_US]=
StartupNotify=false
Terminal=false
TerminalOptions=
Type=Application
X-KDE-autostart-after=kdesktop

```

---

### Post by ouroboros1827 on 2006-08-28
Ok, I got it working...

Don't ask me how but compiz-gnome wasn't installed (yes, it was working...and compiz-gnome got uninstalled). I'm using runcompiz.sh and putting that into ~/.kde/Autostart/compiz

Heh I definitely recommend gnome-compiz-manager or whatever...MOST useful

Any questions?

---

