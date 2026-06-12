---
title: "Package compiz-gnome broken (?)"
date: 2007-09-09
forum: Desktop Effects &amp; Customization
---

### Post by WanderingKnight on 2007-09-09
I'm following the instructions specified in the ubuntuguide.org wiki to install Compiz-Fusion on GNOME, but I've run on this problem: When I try to install the following packages:

```
sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
```

I get this error on package compiz-gnome:

```
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.5~git20070905+3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20070905+3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20070905+3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any ideas?

---

### Post by GatorV on 2007-09-10
I'm getting the same error and can't remove it :(

---

### Post by RonBoy25 on 2007-09-12
I am having the exact same issue...:(

---

### Post by RonBoy25 on 2007-09-12
I figured it out.  Go into synaptic and completely remove the broken packages.  Wipe them both.  I received the same error from before when removing the first one, and the second one goes quietly.  Then when you close synaptic you should receive an update notification.  Update the suggested files and that should fix the problem.

Worked for me.

---

