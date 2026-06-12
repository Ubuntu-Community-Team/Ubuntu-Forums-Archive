---
title: "Remove Gnome 3.10 settings"
date: 2013-11-13
forum: Desktop Environments
---

### Post by dankojoffrey on 2013-11-13
Hi, I wanted to test gnome 3.10 on ubuntu 13.10. I installed it from:
```
sudo add-apt-repository ppa:ricotz/testing
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo add-apt-repository ppa:gnome3-team/gnome3-staging
sudo apt-get update
sudo apt-get install gnome-shell

```
then after a while I removed gnome like this:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:gnome3-team/gnome3-staging
sudo ppa-purge ppa:gnome3-team/gnome3-next
sudo purge gnome-shell

```
Now I'm back in Unity, but some hings remained from gnome 3.10, like:
window decorations
close-maximize-minimize buttons are gone (only one large button on the right side like in gnome) in nautilus and others...
touchscreen is not working properly like before - touch to click has bugs like in gnome 3.10
and more...

How do I go back to original Ubuntu settings like before...???


**Update: **so I managed to do it.
```
sudo apt-get purge unity ubuntu-desktop nautilus* gnome* compiz* 

sudo apt-get install unity ubuntu-desktop nautilus compiz gnome-session
```

_These problems remain:_
1. there are two different network indicators on unity panel (one with some lock icon)
2. in session menu there is red icon before username

Any ideas...???

---

### Post by Frogs Hair on 2013-11-13
Install the synaptic package manager and check for auto removable packages under status or use the following command .```
 sudo apt-get autoremove
``` I too tried the gnome 3 team ppa on my last release and the purge left a number of packages on my system which I removed with synaptic. Logout/in after the packages have been removed.

---

