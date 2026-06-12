---
title: "Problem with theme after upgrade to 3.8"
date: 2013-04-03
forum: Desktop Environments
---

### Post by Kotrfa on 2013-04-03
wHi.

This will be better place to ask. After upgrade to GNOME 3.8 from 3.6 my themes got broken, as you can see on the screen below. [COLOR=#000000]I tried to install gnome-theme- extra, gnome-themes-extra/standard/ubuntu... But it is still same. [/COLOR][COLOR=#000000]Gnome-tweak-tool says Current theme: Adwaita (default), but it looks like high contrast. [/COLOR]

[IMG]http://imageshack.us/scaled/landing/694/screenshotfrom201304031.png[/IMG]

Does anyone has any ideas? Thanks

---

### Post by neruson on 2013-04-03
Themes always break in Gnome after an upgrade as well as most of the extensions in my experience. It's why I don't use Gnome anymore. You either have to wait until the person who made the theme ports it over to 3.8 or just pick a new theme if any are even available at this point since 3.8 is so new.

---

### Post by Kotrfa on 2013-04-03
But this isn't downloaded theme. It is the default theme. Thats the problem.

---

### Post by Frogs Hair on 2013-04-03
If you have the  synaptic package manager installed check for the installation of the correct theme theme package.It is a testing ppa  so there may be problems. 

gnome-themes-standard 3.7.91
[https://launchpad.net/~gnome3-team/+archive/gnome3/+index?batch=75&memo=75&start=75](https://launchpad.net/~gnome3-team/+archive/gnome3/+index?batch=75&memo=75&start=75)

---

### Post by Kotrfa on 2013-04-04
Finally solved. I reinstalled gnome3 and it works fine now. There was problem with Adwaita gtk+ theme and only High Contrast was working. Thanks.

---

