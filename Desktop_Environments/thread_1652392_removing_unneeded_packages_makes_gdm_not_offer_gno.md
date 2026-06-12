---
title: "removing unneeded packages makes gdm not offer gnome?"
date: 2010-12-24
forum: Desktop Environments
---

### Post by bcrowell on 2010-12-24
I run linux on some machines with 40 Gb hard disks, which turns out to be too small to hold a standard lucid install plus openoffice. I found a list of packages that I don't need on these machines and that are not required in order to run the gnome desktop:

```
bluez\-.* ttf-thai-tlwg ttf-indic-fonts-core vinagre ubuntu-wallpapers totem-common empathy-common gnome-games-common rhythmbox brasero-common libsane libgweather-common tomboy f-spot libmono.* evolution evolution-common gnome-screensaver tex-common
```

If I apt-get remove this list, then after I restart the computer, gdm no longer offers gnome as an option when I log in. Your first reaction will probably be that hidden somewhere on that long list there must be something that's crucial for the gnome desktop. But that's not the case, because I know for sure that it is possible for gnome to run without these packages -- I have systems that do it. It seems that the process that works is to apt-get remove all these, restart, apt-get install gnome-desktop-environment, and then again apt-get remove all the ones I don't want. Is there any easier way to accomplish this?

TIA!

-Ben

---

### Post by mikewhatever on 2010-12-24
So what does it offer instead?

... and by the way, 40GB is enough to hold 10 default installations of Lucid Lynx.

---

### Post by bcrowell on 2010-12-24
> **mikewhatever said:**
> So what does it offer instead?
An xterm session.

> **mikewhatever said:**
> ... and by the way, 40GB is enough to hold 10 default installations of Lucid Lynx.
Ah, thanks for correcting me on that. I recently had a machine with a 40 Gb disk fill up after installing lucid+ooo, but on the one I'm installing on now I can see that I still have 90% of the space free. I'm guessing that either the other machine had a dying hard disk with 90% bad sectors, or maybe when I did the install I inadvertently left another OS on the disk instead of overwriting it.

---

### Post by wilee-nilee on 2010-12-24
Some of that apt list is attached to the desktop, did you look at what else was going down with the ship?

---

