---
title: "Compiz update problem"
date: 2006-09-22
forum: Desktop Environments
---

### Post by kberglun on 2006-09-22
I installed Compiz yesterday and everything went well. Today my system says there are updates for Compiz - compiz-core 0.0.13.57 and compiz-gnome 0.0.13.57.

When I try to do the update it says:
Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.

That doesn't work.


If I try to update it anyway it says:
E: /var/cache/apt/archives/compiz-core_0.0.13.57-0ubuntu1_i386.deb: trying to overwrite `/usr/bin/compiz', which is also in package compiz
E: /var/cache/apt/archives/compiz-gnome_0.0.13.57-0ubuntu1_i386.deb: trying to overwrite `/usr/share/gnome/wm-properties/compiz.desktop', which is also in package compiz


If I do
sudo apt-get dist-upgrade
it says:
Unpacking compiz-core (from .../compiz-core_0.0.13.57-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-core_0.0.13.57-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/compiz', which is also in package compiz
dpkg-deb: subprocess paste killed by signal (Broken pipe)



I haven't seen anyone else having the same problem. Any ideas? Need more info?

---

### Post by ayoli on 2006-09-22
try:
sudo apt-get -f dist-upgrade

---

### Post by kberglun on 2006-09-22
Nope didn't work, same result.

---

### Post by elgalad525 on 2006-09-22
I had a similar problem with the latest updates, with synaptic refusin to let me apply the appropriate updates.

I resorted to removing compiz completely (ie. going back to KDE, as I'm using kubuntu) and reinstalling/reconfiguring using the new packages.

No problems so far, and the new config utility for compiz (CSU) is great!

Good luck ;)

---

### Post by amoore on 2006-09-23
im having the same problem too!!! if someone has a solution it would sure help.

thanks:-)

---

