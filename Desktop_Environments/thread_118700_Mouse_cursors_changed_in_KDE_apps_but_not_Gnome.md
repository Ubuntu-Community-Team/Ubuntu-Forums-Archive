---
title: "Mouse cursors changed in KDE apps but not Gnome"
date: 2006-01-17
forum: Desktop Environments
---

### Post by eddiewalker on 2006-01-17
I'm using Gnome with a few KDE apps installed.  I tried installing a cursor theme from gnome-look.org using the packaged install script.

The theme didn't show up in the gnome mouse preference pane, or apply to any Gnome apps, but it stuck in all of my KDE apps (amarok, kmymoney, etc)

The mouse them I installed turned out to be really ugly and I'd like to get rid of it in my KDE apps.  Where can I start?

---

### Post by earobinson on 2006-01-17
why not just find the defult mouse on the same site and install it?

---

### Post by eddiewalker on 2006-01-17
I can't find it, besides:

Each package comes with its own installer script.  I don't know enought about what they do to be guaranteed that another script will undo what the first one did.

This has to be in some KDE config file, or some system file that KDE reads but Gnome ignores, but I dont have all of kubuntu installed, so I don't know where to look.

---

### Post by eddiewalker on 2006-01-17
Here is the shell script that caused all of this nonsense:

```
#!/bin/bash
mkdir -p $HOME/.icons/default
tar xzf pantherx.tar.gz
cd pantherx && cp -R cursors $HOME/.icons/default/
echo "[Icon Theme]" > $HOME/.icons/default/index.php
echo "Inherits=cursors" >> $HOME/.icons/default/index.php 

```

---

