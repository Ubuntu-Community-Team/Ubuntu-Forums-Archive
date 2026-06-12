---
title: "Script launched at login on MATE 1.18 randomly relaunches again and again"
date: 2017-12-08
forum: Desktop Environments
---

### Post by spcwingo on 2017-12-08
As the title states this only happens with MATE 1.18. The script is as follows:

```
#!/bin/bash

sleep 30 && wbar & exit 0
```

Has anyone else experienced this or have a solution? Thanks, y'all.

---

### Post by again? on 2017-12-09
If you log out and back in do you get another instance of the script running?
FYI.
wbar installs a .desktop file to etc/xdg/autostart (last line of code box).
```
glen@Xen2:~$ dpkg-query -L wbar
/.
/usr
/usr/bin
/usr/bin/wbar
/usr/share
/usr/share/bash-completion
/usr/share/bash-completion/completions
/usr/share/bash-completion/completions/wbar
/usr/share/doc
/usr/share/doc/wbar
/usr/share/doc/wbar/README
/usr/share/doc/wbar/copyright
/usr/share/doc/wbar/README.Debian
/usr/share/doc/wbar/changelog.Debian.gz
/usr/share/icons
/usr/share/icons/hicolor
/usr/share/icons/hicolor/128x128
/usr/share/icons/hicolor/128x128/apps
/usr/share/icons/hicolor/128x128/apps/wbar.png
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/wbar.1.gz
/usr/share/man/es
/usr/share/man/es/man1
/usr/share/man/es/man1/wbar.1.gz
/usr/share/wbar
/usr/share/wbar/make-conf.sh
/usr/share/locale
/usr/share/locale/fi
/usr/share/locale/fi/LC_MESSAGES
/usr/share/locale/fi/LC_MESSAGES/wbar.mo
/usr/share/locale/es
/usr/share/locale/es/LC_MESSAGES
/usr/share/locale/es/LC_MESSAGES/wbar.mo
/usr/share/locale/de
/usr/share/locale/de/LC_MESSAGES
/usr/share/locale/de/LC_MESSAGES/wbar.mo
/usr/share/pixmaps
/usr/share/pixmaps/wbar
/usr/share/pixmaps/wbar/dock.png
/etc
/etc/wbar.d
/etc/wbar.d/wbar.cfg
/etc/xdg
/etc/xdg/autostart
**/etc/xdg/autostart/wbar.desktop**
```

The .desktop already has a 30 second start delay and wbar should start in all sessions.
Whether MATE observes the  "X-GNOME-Autostart-Delay" or not... I don't know.
```
glen@Xen2:~$ cat /etc/xdg/autostart/wbar.desktop
[Desktop Entry]
Name=Warlock Bar
Type=Application
Exec=/usr/bin/wbar
Terminal=false
Icon=/usr/share/pixmaps/wbar/wbar.png
Comment=A light and fast launch bar.
Categories=Utility;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=wbar
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-enabled=true
**X-GNOME-Autostart-Delay=30**
X-Ubuntu-Gettext-Domain=wbar
```

---

### Post by spcwingo on 2017-12-10
I am currently unable to test (I'm working out of town at the moment). I'll give it a shot and report back when I'm back at home. Thank you for replying.

---

### Post by spcwingo on 2017-12-12
I figured out the issue. Thanks for putting me on the right track. I deleted my launch script and changed the

```
X-GNOME-Autostart-Delay=30
```

to

```
X-MATE-Autostart-Delay=30
```

in the autostart .desktop file located in /etc/xdg/autostart.

I really appreciate you putting me on the right track. This issue was driving me absolutely insane! Thanks again!

---

### Post by again? on 2017-12-13
Glad to help. Handy to know about X-MATE settings.
Probably better to copy /etc/xdg/autostart/wbar.desktop to ~/.config/autostart.
The edited version in ~/.config/autostart takes precedence for the $USER.
Doubt it matters though as I don't think wbar gets regular updates... (or irregular :p)

---

