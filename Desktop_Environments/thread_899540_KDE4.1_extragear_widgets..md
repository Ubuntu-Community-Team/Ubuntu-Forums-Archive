---
title: "KDE4.1 extragear widgets."
date: 2008-08-24
forum: Desktop Environments
---

### Post by OldGaf on 2008-08-24
Hi all,

I installed the extragear package to get more widgets. They show up in the "add widgets" menu, but when I add any of them, I get a small black circle.
If I right click on it, the bottom of the pop up menu says "remove unknown widget"

What am I missing here?

BTW.... I have added kde4 desktop to my kubuntu 8.04 x86_64 system and switch between kde3 and kde4 if that make a difference.

---

### Post by Lek130 on 2008-09-01
Hey I have the same issue did you figure out the issue?

---

### Post by TheUnabeefer on 2008-09-02
> **OldGaf said:**
> Hi all,

I installed the extragear package to get more widgets. They show up in the "add widgets" menu, but when I add any of them, I get a small black circle.
If I right click on it, the bottom of the pop up menu says "remove unknown widget"

What am I missing here?

BTW.... I have added kde4 desktop to my kubuntu 8.04 x86_64 system and switch between kde3 and kde4 if that make a difference.


AFAIK, the extragear packages aren't supposed to be used anymore, as they conflict with the newer plasma libs. (ie, dont work)  All of the plasmoids from those appear in another package... I am at work at the moment and don't recall which.  Maybe kde-plasma-addons.

I usually go into adept and search for plasma or plasmoid, and it will show all the available packages.  A few are still there stating they are "filler" packages that are empty and just there for the name... and the description tells you what to actually use.

Anyone know the actual packages?  I will check when I get home.

---

### Post by TheUnabeefer on 2008-09-03
Use "kdeplasma-addons".  the extragear packages and "kdeplasmoids" no longer work.

---

### Post by irrdev on 2008-09-03
Also, make sure you restart your computer after installing the kdeplasma-addons, or any other type of plasmoids for that matter. Otherwise, the newly installed plasmoids will show up in the widgets list, but they can't actually be referenced, hence little black circles on your desktop. :grin:

---

### Post by justinlawrence on 2008-09-03
Do you guys have this in your /etc/apt/sources.list ?

```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main

```

(I added it, according to the instructions at:)

[http://www.kubuntu.org/news/kde-4.1rc1]("http://www.kubuntu.org/news/kde-4.1rc1")

And then, somehow, when i run

```
aptitude install kdeplasma-addons
```

i get:


```
The following packages have unmet dependencies:
  libqt4-opengl: Depends: libqtcore4 (= 4.4.0-1ubuntu5~hardy1~ppa2) but 4.4.1-1ubuntu1~hardy1~ppa1 is to be installed.
                 Depends: libqtgui4 (= 4.4.0-1ubuntu5~hardy1~ppa2) but 4.4.1-1ubuntu1~hardy1~ppa1 is to be installed.
  libqt4-assistant: Depends: libqt4-network (= 4.4.0-1ubuntu5~hardy1~ppa2) but 4.4.1-1ubuntu1~hardy1~ppa1 is to be installed.
                    Depends: libqtcore4 (= 4.4.0-1ubuntu5~hardy1~ppa2) but 4.4.1-1ubuntu1~hardy1~ppa1 is to be installed.
  libqt4-test: Depends: libqtcore4 (= 4.4.0-1ubuntu5~hardy1~ppa2) but 4.4.1-1ubuntu1~hardy1~ppa1 is to be installed.
  libqt4-core: Depends: libqt4-dbus (= 4.4.0-1ubuntu5~hardy1~ppa2) but 4.4.1-1ubuntu1~hardy1~ppa1 is to be installed.
               Depends: libqt4-network (= 4.4.0-1ubuntu5~hardy1~ppa2) but 4.4.1-1ubuntu1~hardy1~ppa1 is to be installed.
               Depends: libqt4-script (= 4.4.0-1ubuntu5~hardy1~ppa2) but 4.4.1-1ubuntu1~hardy1~ppa1 is to be installed.
               Depends: libqt4-xml (= 4.4.0-1ubuntu5~hardy1~ppa2) but 4.4.1-1ubuntu1~hardy1~ppa1 is to be installed.
               Depends: libqtcore4 (= 4.4.0-1ubuntu5~hardy1~ppa2) but 4.4.1-1ubuntu1~hardy1~ppa1 is to be installed.
  libqt4-xmlpatterns: Depends: libqt4-network (= 4.4.0-1ubuntu5~hardy1~ppa2) but 4.4.1-1ubuntu1~hardy1~ppa1 is to be installed.
                      Depends: libqtcore4 (= 4.4.0-1ubuntu5~hardy1~ppa2) but 4.4.1-1ubuntu1~hardy1~ppa1 is to be installed.
  libqt4-help: Depends: libqt4-sql (= 4.4.0-1ubuntu5~hardy1~ppa2) but 4.4.1-1ubuntu1~hardy1~ppa1 is to be installed.
               Depends: libqtcore4 (= 4.4.0-1ubuntu5~hardy1~ppa2) but 4.4.1-1ubuntu1~hardy1~ppa1 is to be installed.
               Depends: libqtgui4 (= 4.4.0-1ubuntu5~hardy1~ppa2) but 4.4.1-1ubuntu1~hardy1~ppa1 is to be installed.
  libqt4-gui: Depends: libqt4-designer (= 4.4.0-1ubuntu5~hardy1~ppa2) but 4.4.1-1ubuntu1~hardy1~ppa1 is to be installed.
              Depends: libqt4-svg (= 4.4.0-1ubuntu5~hardy1~ppa2) but 4.4.1-1ubuntu1~hardy1~ppa1 is to be installed.
              Depends: libqtgui4 (= 4.4.0-1ubuntu5~hardy1~ppa2) but 4.4.1-1ubuntu1~hardy1~ppa1 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Upgrade the following packages:
libqt4-assistant [4.4.0-1ubuntu5~hardy1~ppa2 (now) -> 4.4.1-1ubuntu1~hardy1~ppa1 (<NULL>)]
libqt4-gui [4.4.0-1ubuntu5~hardy1~ppa2 (now) -> 4.4.1-1ubuntu1~hardy1~ppa1 (<NULL>)]
libqt4-help [4.4.0-1ubuntu5~hardy1~ppa2 (now) -> 4.4.1-1ubuntu1~hardy1~ppa1 (<NULL>)]
libqt4-opengl [4.4.0-1ubuntu5~hardy1~ppa2 (now) -> 4.4.1-1ubuntu1~hardy1~ppa1 (<NULL>)]
libqt4-test [4.4.0-1ubuntu5~hardy1~ppa2 (now) -> 4.4.1-1ubuntu1~hardy1~ppa1 (<NULL>)]
libqt4-xmlpatterns [4.4.0-1ubuntu5~hardy1~ppa2 (now) -> 4.4.1-1ubuntu1~hardy1~ppa1 (<NULL>)]

Downgrade the following packages:
libqt4-core [4.4.0-1ubuntu5~hardy1~ppa2 (now) -> 4.3.4-0ubuntu3 (hardy)]

Score is 200

Accept this solution? [Y/n/q/?]

```

:confused:

Should i go ahead and say "yes" to this? i'm afraid i'll break something.

---

