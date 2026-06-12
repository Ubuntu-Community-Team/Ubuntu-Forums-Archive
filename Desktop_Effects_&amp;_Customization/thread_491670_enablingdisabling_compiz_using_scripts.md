---
title: "enabling/disabling compiz using scripts"
date: 2007-07-03
forum: Desktop Effects &amp; Customization
---

### Post by TheFuzzy0ne on 2007-07-03
Hi everyone. I install Compiz a few days ago, and I am running KDE with an NVidia GeForce FX 5200 AGP card. Everything seems to work great, until I go to play an OpenGL game, and then the screen goes black, flickers a little bit, then stays black.

I have seen many remedies for getting OpenGL games to work with Compiz, but as Compiz is really geared towards Gnome, I would very much like a way for me to enable and disable Compiz at the touch of a button.

To enable Compiz, I can simply run this:

#!/bin/bash

compiz --replace 
# initiates compiz

emerald --replace 
# gives me back my titlebar and makes it look funky. :D

I think that's what I need to run, anyway... In any case, it seems to work.

How can I stop compiz running, so I can play my game, and then re-enable compiz again when I am done?

I think it would also be nice to just be able to enable it and disable it when I want, as my PC is not very high spec, and I sometimes run CPU intensive programs.

I would appreciate any pointers.

Many thanks in advance.

Daz.

---

### Post by superyounan1 on 2007-07-03
cant you just kill the processes?
```
ps -e | grep compiz
```

you'll get a list of processes, one of them will be called "compiz.real". Note the leftmost number, that will be the process id.

if the process id for compiz.real is 11313, do
```

sudo killall compiz
sudo kill -9 11313

``` 

that ought to stop it completely. 

you could also use the system monitor and end it that way, 
```
gnome-system-monitor
```

---

### Post by TheFuzzy0ne on 2007-07-04
> **superyounan1 said:**
> cant you just kill the processes?
```
ps -e | grep compiz
```

you'll get a list of processes, one of them will be called "compiz.real". Note the leftmost number, that will be the process id.

if the process id for compiz.real is 11313, do
```

sudo killall compiz
sudo kill -9 11313

``` 

that ought to stop it completely. 

you could also use the system monitor and end it that way, 
```
gnome-system-monitor
```

I should have thought of that...

It works, but I can't get kde-window-decorator to fire up again. It just keeps crashing.

---

