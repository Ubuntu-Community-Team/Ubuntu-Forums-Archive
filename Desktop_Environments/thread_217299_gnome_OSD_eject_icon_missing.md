---
title: "gnome OSD eject icon missing"
date: 2006-07-16
forum: Desktop Environments
---

### Post by ico on 2006-07-16
Hi all,

I am using dapper with latest updates and recently I've noticed that while OSD for volume (I am using macbook pro, but this is not mbp-specific) has a nice speaker icon above the horizontal level bar, the eject OSD (on-screen-display) icon has simply a generic icon of a white file with a red "x" in the middle. This leads me to believe that the eject icon is missing and that a simple inclusion of an icon in the right place ought to solve the problem. However, I am not sure where the icon needs to be placed and/or which config file needs to be altered to fix this.

Hence, I would greatly appreciate any help I can get on this matter.

Thank you very much!

Best wishes,

Ico

---

### Post by ico on 2006-07-17
Ok, so I've figured out that the OSD for volume and eject button is part of the acme package which has been merged into gnome-control-center, or more precisely to gnome-settings-daemon. I've just spent last 4 hours compiling and hacking the gnome code and no matter how I attempt to alter the code (it's in gnome-settings-daemon/gnome-settings-multimedia-keys.c), i.e. by hardwiring the path to the image of my choice, upon restarting gnome-settings-daemon, as soon as I press the eject button (whose image has been altered), the daemon crashes... So it seems that something else is not happy with me hardwiring the icon.

Any ideas? Or perhaps more importantly, does anyone else have this problem (even if you do not have an eject key, you can map one in System -> Keyboard Shortcuts, and then scroll all the way down for eject button simply to test this thing out)? 

Ico

---

