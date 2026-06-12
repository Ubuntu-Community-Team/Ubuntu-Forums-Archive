---
title: "No burn animation in Karmic CCSM"
date: 2009-11-15
forum: Desktop Environments
---

### Post by ontwowheels on 2009-11-15
Any way to get the burn animation?  Doing some searches I found some information but they didn't seem correct for Karmic.

THANKS

---

### Post by waspbr on 2009-11-15
the animation is there just enable the animation-add-on icon and go to the animation menu, then you can select the burn animation

---

### Post by sahilsonu on 2009-11-15
i really wanna know to know which desktop environment these images depicts??:sad:

---

### Post by ontwowheels on 2009-11-15
> **waspbr said:**
> the animation is there just enable the animation-add-on icon and go to the animation menu, then you can select the burn animation

Nope...burn isn't there.  See screenshot.

---

### Post by ontwowheels on 2009-11-15
> **sahilsonu said:**
> i really wanna know to know which desktop environment these images depicts??:sad:

It's off topic....but check gnome-look.org

---

### Post by ontwowheels on 2009-11-15
You can also see here, no burn as an option.

---

### Post by stinkeye on 2009-11-15
If you don't have the animations add-on 
[ATTACH]136321[/ATTACH]
it means you don't have the compiz-fusion-plugins-extra package.
If you do have this package it probably means you updated compiz-fusion-plugins-extra
from the compiz repository.
If so,disable the compiz repository and uninstall compiz-fusion-plugins-extra.
Refresh your sources and download compiz-fusion-plugins-extra from the ubuntu repo
and you should have the animations add-ons with beam and burn.
[ATTACH]136322[/ATTACH]


On a side note if you want the tile and snow plugins to work download the
compiz-fusion-plugins-unsupported package
from the compiz repo.
But after doing so disable the repo so you dont update compiz-fusion-plugins-extra
and loose the animations add-ons.

---

### Post by ontwowheels on 2009-11-15
> **stinkeye said:**
> If you don't have the animations add-on 
[ATTACH]136321[/ATTACH]
it means you don't have the compiz-fusion-plugins-extra package.
If you do have this package it probably means you updated compiz-fusion-plugins-extra
from the compiz repository.
If so,disable the compiz repository and uninstall compiz-fusion-plugins-extra.
Refresh your sources and download compiz-fusion-plugins-extra from the ubuntu repo
and you should have the animations add-ons with beam and burn.
[ATTACH]136322[/ATTACH]


On a side note if you want the tile and snow plugins to work download the
compiz-fusion-plugins-unsupported package
from the compiz repo.
But after doing so disable the repo so you dont update compiz-fusion-plugins-extra
and loose the animations add-ons.

THANKS....that was it.  I had Animations selected, but not Animations-Add ons.  DOH.  Thanks again.

---

