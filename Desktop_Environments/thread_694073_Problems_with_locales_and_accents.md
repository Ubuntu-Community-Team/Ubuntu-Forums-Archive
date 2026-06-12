---
title: "Problems with locales and accents"
date: 2008-02-11
forum: Desktop Environments
---

### Post by Compact on 2008-02-11
I use Kopete in Gnome. When I try to write a letter with an accent the accent appears before the letter, like this: `a. I have executed Kopete from console to see if there is any error. These are the errors i get when trying to write:
```
Qt: Locales not supported on X server
QInputContext: no input method context available
QInputContext: no input method context available

```

Does anybody know how to solve this? Thank you in advance.

---

### Post by polmir on 2008-02-11
type in terminal 
```
locale
```
```
dpkg -l | grep xfont
```
```
dpkg -l | grep locales
```
and post output of it.

---

### Post by Compact on 2008-02-12
What you asked for:
```
arnau@maxwell:~$ locale
LANG=ca_ES.UTF-8@valencia
LC_CTYPE="ca_ES.UTF-8@valencia"
LC_NUMERIC="ca_ES.UTF-8@valencia"
LC_TIME="ca_ES.UTF-8@valencia"
LC_COLLATE="ca_ES.UTF-8@valencia"
LC_MONETARY="ca_ES.UTF-8@valencia"
LC_MESSAGES="ca_ES.UTF-8@valencia"
LC_PAPER="ca_ES.UTF-8@valencia"
LC_NAME="ca_ES.UTF-8@valencia"
LC_ADDRESS="ca_ES.UTF-8@valencia"
LC_TELEPHONE="ca_ES.UTF-8@valencia"
LC_MEASUREMENT="ca_ES.UTF-8@valencia"
LC_IDENTIFICATION="ca_ES.UTF-8@valencia"
LC_ALL=
```

```
arnau@maxwell:~$ dpkg -l | grep xfont
ii  libxfont1                                  1:1.3.0-0ubuntu1.1                                X11 font rasterisation library
ii  xfonts-100dpi                              1:1.0.0-3                                         100 dpi fonts for X
ii  xfonts-75dpi                               1:1.0.0-3                                         75 dpi fonts for X
ii  xfonts-base                                1:1.0.0-4                                         standard fonts for X
ii  xfonts-encodings                           1:1.0.2-1                                         Encodings for X.Org fonts
ii  xfonts-scalable                            1:1.0.0-6                                         scalable fonts for X
ii  xfonts-utils                               1:1.0.1-1ubuntu1                                  X Window System font utility programs
ii  xfontsel                                   1:1.0.2-0ubuntu1                                  X client - xfontsel
```

```
arnau@maxwell:~$ dpkg -l | grep locales
ii  belocs-locales-bin                         2.4-2.2ubuntu5                                    tools for compiling locale data files
ii  locales                                    2.6.1-1                                           common files for locale support
ii  util-linux-locales                         2.13-8ubuntu1                                     Locales files for util-linux

```

Thank you!

---

### Post by polmir on 2008-02-12
```
sudo dpkg-reconfigure locales
```
kopete instant messenger for KDE
Install kde-i18* for your locale
If you know this language red this
[http://ubuntuforums.org/showthread.php?t=513377]("http://ubuntuforums.org/showthread.php?t=513377")

---

