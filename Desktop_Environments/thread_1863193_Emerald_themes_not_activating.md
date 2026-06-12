---
title: "Emerald themes not activating"
date: 2011-10-17
forum: Desktop Environments
---

### Post by Ra'anan on 2011-10-17
Hi,

does anyone have a link to a fix or instructions for Emerald themes?

I have compiz-fusion / fusion-icon, have selected emerald as window decorator, but I still see my standard GTK theme, the Emerald theme manager is available but I can't activate the themes.

emerald is listed as 'Zombie' in gnome-system-monitor

---

### Post by Frogs Hair on 2011-10-17
Hello and Welcome

What version of Ubuntu ? I was looking for information about emerald in Gnome 3 and what I found indicates that emerald doesn't work with the Gnome Shell , but found no information Unity / Gnome 3 . The old command is below .
```
emerald --replace
```

---

### Post by Ra'anan on 2011-10-17
Hey Frog's Hair! :]

I have followed all the instructions on this forum before posting.

Ubuntu 10.04 lucid (ubuntu studio)

I have just now removed Emerald after 2 versions were loaded, both 'Zombie'

list of installed packages now (from synaptic)

compiz
python-compizconfig
compizconfig-settings-manager
compiz-fusion-bcop
compiz-plugins
compiz-gnome
compiz-core
libemeraldengine0
libdecoration0
compiz-fusion-plugins-main
fusion-icon
simple-ccsm
compizconfig-backend-gconf
cairo-dock-core
cairo-dock-data
cairo-dock

At the moment, the only settings that I want that are working are the cairo-dock installed window/menu shadows and Konsole transparency proper.

other installed window managers:

Metacity
FVWM

I've probably botched the installations.

---

### Post by Frogs Hair on 2011-10-17
I tried Emerald on Ubuntu 10.04 with Cairo dock and with the Compiz Fusion Icon from the dock activated it worked pretty well .

I'm not sure how you could have botched the installation if you installed emerald from software center / repository unless you tried to install the packages individually .  [http://wiki.compiz.org/Decorators/Emerald](http://wiki.compiz.org/Decorators/Emerald)

---

### Post by Ra'anan on 2011-10-17
I did some reinstalling and managed to get compiz effects and emerald working on 1024x768.

I have two screens, 

one on my notebook - 1280x800 preferred
and a 19inch lcd 1280x1024...

when i startx now with 1024x768 mirrored on both screens the FX work, but not when I raise the res and turn off mirroring...

i've seen some other threads in google, its probably my GPU...

so where do i go from here? :)

want the sleek emerald look with transparency, don't need the wobbly/zoomy compiz fx... and emerald won't work on high resolutions.

---

