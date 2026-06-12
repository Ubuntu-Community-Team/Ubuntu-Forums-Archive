---
title: "GUI minimum packages &quot;apt-get&quot;"
date: 2008-07-23
forum: Desktop Environments
---

### Post by Kylibar on 2008-07-23
ok, I know the MINIMUM packages you have to install to the KDE GUI on ubuntu server;

apt-get install -
x-window-system-core
kde-core
kdm


I read somewhere else that for the other GUIs its basically the same? but its not. gnome-core dosent exist?

I want to try my hand and a MINIMUM Ubuntu GUI, but it seems to be a little more elusive. 

apt-get install -
x-window-system-core
???gnome-core (dosent exist)
gdm


any help would be nice.

---

### Post by kerry_s on 2008-07-23
```
sudo apt-get install xorg gnome-session gnome-panel gdm metacity gnome-terminal
``` 

use xorg instead of x-window-system-core

also learn "apt-cache search" it will make your life easier.
example: apt-cache search gnome

also have you made sure all your repos are on?

---

