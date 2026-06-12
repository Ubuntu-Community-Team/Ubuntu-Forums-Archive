---
title: "gnome-apt-install not working - freeze"
date: 2005-08-08
forum: Desktop Environments
---

### Post by wjp.reg on 2005-08-08
Not life or death, but..

Add/Remove Programs (gnome-app-install) module does not play right; pressing "Advanced" throws me into Synaptic however.

Tried reinstall, but no cigar  :-? 

A search of the forum came up empty.. any one have any ideas?

I considered uninstalling, but the ubuntu-desktop was then also marked for removal and I didn't think that was a good idea. right?

---

### Post by TristanMike on 2005-08-08
If you mean that the add/remove list doesn't come up, and the little wait symbol spins around for all eternity, then that's a package problem.

Under Synaptic, look for python-xdg and Force to Orginal Hoary Version. But the catch is, that when ever you update, you have to make sure that this package doesn't get upgraded too, or you'll lose the add/remove list and again you have to look for the python-xdg package and, well, you get the picture.

I hope this is what you meant.

---

