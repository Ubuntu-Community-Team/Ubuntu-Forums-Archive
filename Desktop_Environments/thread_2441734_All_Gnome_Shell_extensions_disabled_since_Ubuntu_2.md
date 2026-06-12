---
title: "All Gnome Shell extensions disabled since Ubuntu 20.04"
date: 2020-04-26
forum: Desktop Environments
---

### Post by Valeryan_24 on 2020-04-26
Hi,

Since the last updates of the mid-week - those who lead to final Ubuntu 20.04 version, I already used the beta since the beginning of development - all my Gnome Shell extensions are always disabled, except "Desktop Icon".

They all well appear in the page extensions.gnome.org/local but, even if I enable them, it does nothing nor changes the look. If I reload the page or restart computer, all come back to disabled. And all worked very well until this week.

Is there a package, library, dependency... that could have been deleted during the update and is needed ? If you know, thanks for your help !

In dconf I have :

```
/org/gnome/shell/disabled-extensions []

/org/gnome/shell/enabled-extensions
['clipboard-indicator@tudmotu.com', 'cpufreq@konkor', 'dash-to-dock@micxgx.gmail.com', 'emoji-selector@maestroschan.fr', 'Move_Clock@rmy.pobox.com', 'gsconnect@andyholmes.github.io',
'appindicatorsupport@rgcjonas.gmail.com', 'set-columns@maestroschan.fr', 'no-title-bar@jonaspoehler.de', 'sensory-perception@HarlemSquirrel.github.io', 'ShellTile@emasab.it', 
status-area-horizontal-spacing@mathematical.coffee.gmail.com', 'syncthingicon@jay.strict@posteo.de', 'user-theme@gnome-shell-extensions.gcampax.github.com']
```

Even if I enable one addon, as said nothing happens : its icon doesn't appear in the top bar. Never had this before...

---

### Post by rbmorse on 2020-04-26
check to see if the package

```
gnome-shell-extensions-prefs
```

is installed, or reinstall it if it's present.  Fixed the problem for me.

---

### Post by Valeryan_24 on 2020-04-26
> **rbmorse said:**
> check to see if the package

```
gnome-shell-extensions-prefs
```

is installed, or reinstall it if it's present.  Fixed the problem for me.

Hi, no gnome-shell-extensions-prefs package available to install, but yes, when starting "Gnome Tweaks", on the Extensions part: Extensions were disabled, if I enable them, they rework.

Thanks a lot !

---

