---
title: "Custom .Xsession behaviour not normal"
date: 2010-07-19
forum: Desktop Environments
---

### Post by itismesteve on 2010-07-19
My problem is, when I start my custom xsession through startx I get almost ideal results; the network manager requires a password every time. But when it is run through gdm I cannot use any of the awesome3 hotkeys (and so alas, cannot actually do _anything_) although the wireless does connect automatically (?).

Any help would be appreciated, let me know if you need any more things for debugging. 

Cheers.

[quote=.xinitrc]#!/usr/bin/env bash
xsetroot -solid black &
gnome-settings-daemon &
# gnome-power-manager &
# gnome-panel &
stalonetray &
nm-applet &
exec /usr/bin/awesome[/quote]

> -rwxr-xr-x  1 steve steve   156 2010-07-19 20:10 .xinitrc
lrwxrwxrwx  1 steve steve     8 2010-07-19 19:31 .Xsession -> .xinitrc

[quote=/usr/share/xsessions/custom.desktop][Desktop Entry]
Encoding=UTF-8
# The names/descriptions should really be better
Name=Custom Session
Comment=This starts a custom session
Exec=custom
# The "default" Exec is a very special one and is handled specially in
# the Xsession script, you could also have "custom" which would just run
# "~/.xsession" directly
Icon=
Type=Application[/quote]

---

### Post by masebase on 2010-07-19
Perhaps I don't understand, but is your goal to not have to enter a keyring password to have your network just work when you login? If so I got around this once by just setting the keyring password to be blank. Not very secure.

Sorry if I misread what you are trying to do.

---

### Post by itismesteve on 2010-07-20
My goal is that when I use the "custom" option in gdm to have the behaviour that happens when i run "startx," currently the "custom" option is very buggy (can't use any hotkeys or open any menu's).

---

