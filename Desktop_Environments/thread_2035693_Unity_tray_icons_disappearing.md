---
title: "Unity: tray icons disappearing"
date: 2012-07-31
forum: Desktop Environments
---

### Post by edgue on 2012-07-31
He there,

I think I have seen this with 11.10 and 12.04 when running unity: 

Sometimes (not too often) my tray icons disappear. 

This means: the icons that represent certain running applications 
(like IBM Sametime status, SAV antivir, opera, ...) are just no longer displayed. 

Interestingly enough, when I switch to a different workspace ... the icons are visible for a second or so!

The indicator panels (caffeine, load, mail, power, sound, ...) are still there, just my "application icons" are hidden. 

The screen shot that I will attach shows the "expected view" ...
you can see the application icons from the left; the last one is the
red "opera" O ... then the indicators start.

When the problem kicks in, any icon left to the "caffeine" indicator is not showing up any more.

One workaround is to open a console to manually restart unity:
> unity & 

Or to restart the whole machine ;-)

Any idea anybody ... for example: does anybody which component is actually responsible for displaying these icons (so that I might write a bug report ... or restart just that application)?

---

### Post by Frogs Hair on 2012-07-31
I use 12.04 and the Opera icon only appears on the far left when active because it is a third party application with no Unity integration. As soon as I select another open application Opera is no longer displayed.  I don't know about the other applications you are running though.

---

### Post by markbl on 2012-07-31
If you are running xorg-edgers ppa then note the comment about "invisible icons" problem in mesa posted in the [xorg edgers ppa description](https://launchpad.net/~xorg-edgers/+archive/ppa).

---

### Post by edgue on 2012-08-01
> **markbl said:**
> If you are running xorg-edgers ppa then note the comment about "invisible icons" problem in mesa posted in the [xorg edgers ppa description](https://launchpad.net/~xorg-edgers/+archive/ppa).

No, I am not using this ppa. 

But I can tell that the problem was reported by some of my coworkers, too ;-)

---

### Post by shevek. on 2012-08-11
I have exactly the same problem reported in #1. In my case, "gnome-do", "pidgin" and others disappear sometimes and they are only back when restarting. I also see them when switching workspace. 

I have whitelisted "all" icons in dconf and I still have the same issue. It happened with my Ubuntu 11.10, and now in my 12.04 with Unity 5.14.0.

---

