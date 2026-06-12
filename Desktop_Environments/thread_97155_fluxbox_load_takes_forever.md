---
title: "fluxbox load takes forever"
date: 2005-11-30
forum: Desktop Environments
---

### Post by monkeyking on 2005-11-30
Well only 20 secs, but it is hell annoying.

Btw there was no default .fluxbox/menu, or more precisly it only had an xterm and a logout.
And where are all the default styles.?

thanks in advance

---

### Post by Xian on 2005-11-30
[QUOTE=monkeyking]Well only 20 secs, but it is hell annoying.[/quote]
There have been some issues with this in the past. In Hoary most people just compiled fluxbox from source. I run fluxbox on Breezy and it loads promptly (5 secs), but I did make a little tweak:

Change your fluxbox.desktop entry to reflect a diff exec line:

```
$ sudo nano -w /usr/share/xsessions/fluxbox.desktop
```

```
[Desktop Entry]
Encoding=UTF-8
Name=Fluxbox
Comment=Highly configurable and low resource X11 Window manager
Exec=/usr/bin/startfluxbox
Terminal=False
TryExec=/usr/bin/startfluxbox
Type=Application

[Window Manager]
SessionManaged=true
```


[QUOTE=monkeyking]Btw there was no default .fluxbox/menu, or more precisly it only had an xterm and a logout.[/quote]

This is the Debian method and it pertains to Ubuntu.
You can install this package & update menus:

```
$ sudo apt-get install menu-xdg
$ sudo update-menus
```

- or -

You can follow this entry I made in the Debian wiki.
[Traditional Menu Generation](http://wiki.debian.org/FluxboxMenu?highlight=%28fluxbox%29)


[QUOTE=monkeyking]And where are all the default styles.?[/QUOTE]

Can't help you there as they are on my box by default.
Check the contents of /usr/share/fluxbox/styles

---

