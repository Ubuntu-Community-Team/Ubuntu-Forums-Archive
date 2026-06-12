---
title: "cant install login theme in karmic"
date: 2010-02-23
forum: Desktop Environments
---

### Post by mike1312 on 2010-02-23
[_that_]("http://ubuntuforums.org/showpost.php?p=8733684&postcount=29") was 3 weeks ago and no1 answered

  I dont have "System>Administration>Login Window" menu item in my ubuntu karmic 64bit so i cant do [_this_]("http://www.ubuntugeek.com/how-to-install-gdm-gnome-display-manager-theme-in-ubuntu.html"),
but i would like to.

Please help

---

### Post by spiderbatdad on 2010-02-23
True. The program "gdm" that handles login is a new version in Karmic, and no longer supports all those great gdm themes of the past. Down grading to gdm-2.20 is likely to cause future breakage, though there are some good guides for doing so. [http://joeb454.ubuntuforums.org/showthread.php?t=1331457](http://joeb454.ubuntuforums.org/showthread.php?t=1331457) This one is least likely to break the system as it makes use of symbolic links.

There is also a limited amount of editing, such as background change, that can be done to the current gdm-2.28 such as this: [http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html](http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html) (which I have not tried.)

---

### Post by mike1312 on 2010-02-24
Thanks a lot man

think the second [way]("http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html") is enough for me
and as ive found somwhere re&#1089;ently may be realised by only one command in trerminal
```
gksudo -u gdm dbus-launch gnome-appearance-properties
```
:P
(first i didnt understand what this command do)

yeah any ..grading is risky

---

### Post by MooPi on 2010-02-24
Try this:  [http://ubuntuforums.org/showthread.php?t=1358026&highlight=gdm-setup.py](http://ubuntuforums.org/showthread.php?t=1358026&highlight=gdm-setup.py)

---

### Post by mike1312 on 2010-02-26
Thanks but im using 64bit so this script will not work in my system
(tried to add repo - doesnt work)

[I]
But i digged out how **to disable this annoying sound on startup :**

```
 sudo -u gdm gconftool-2 --type bool --set /desktop/gnome/sound/event_sounds 'false'
```[/I]

**UPD** after first reboot i get into trouble - gdm didnt login
so i have to```
 startx -- :1
``` from console

---

