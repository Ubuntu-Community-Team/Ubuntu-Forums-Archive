---
title: "Kubuntu Compiz window decorator..."
date: 2007-05-13
forum: Desktop Effects &amp; Customization
---

### Post by rich.bradshaw on 2007-05-13
Hi,

Installed Compiz in Kubuntu, how do you get the window decorator going? Which package is it in? How do I configure Compiz once it's going? I tried compiz-settings, but the box comes up with the settings, but I can't interact with it at all.

---

### Post by russianbandit on 2007-05-14
Did you install it using?

sudo apt-get install compiz compiz-kde

Then run:

compiz --replace gconf &
kde-window-decorator --replace &

---

### Post by FuturePilot on 2007-05-14
If you're using KDE I would use Beryl instead of Compiz. Compiz is very centered around Gnome. Trying to use it in KDE will just result in headaches. Just make sure you have your graphics driver installed then
```
sudo apt-get install beryl beryl-manager emerald-themes
```
Then to start it just type ```
beryl-manager
``` in a terminal.

---

### Post by alynx on 2007-05-15
> **russianbandit said:**
> Did you install it using?

sudo apt-get install compiz compiz-kde

Then run:

compiz --replace gconf &
kde-window-decorator --replace &

Worked for me :guitar: 
Thanks alot

---

### Post by octaedro7 on 2007-05-19
> **FuturePilot said:**
> If you're using KDE I would use Beryl instead of Compiz. Compiz is very centered around Gnome. Trying to use it in KDE will just result in headaches. Just make sure you have your graphics driver installed then
```
sudo apt-get install beryl beryl-manager emerald-themes
```
Then to start it just type ```
beryl-manager
``` in a terminal.

Been trying to use Beryl for days, in Kubuntu.  Tried a lot of things posted on this and other forums and nothing.  Just install compiz from Synaptic and work like a Charm  so far except for a little bug that changes KDE cursor when hovering titlebar.

---

