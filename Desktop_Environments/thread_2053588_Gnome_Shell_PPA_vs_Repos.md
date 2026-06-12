---
title: "Gnome Shell PPA vs Repos"
date: 2012-09-05
forum: Desktop Environments
---

### Post by ajukilibodin on 2012-09-05
Hello,

I was wondering if there was any difference between the two versions? Which one should I go for?  The  gnome3-team/gnome3 ppa or the normal "apt-get install gnome-shell"?

Thanks

---

### Post by Frogs Hair on 2012-09-05
I would use the repository unless you know of a feature that the PPA includes or that you want not in the repository build. Another consideration is if you are using 12.04 for the long term you may want the updates a well maintained PPA provides.

---

### Post by markbl on 2012-09-05
> **ajukilibodin said:**
> I was wondering if there was any difference between the two versions? Which one should I go for?  The  gnome3-team/gnome3 ppa or the normal "apt-get install gnome-shell"?
Actually, there are not "two versions". Go and look at the [gnome 3 ppa](https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=precise) and you will see that gnome-shell is not packaged there, at least not for current 12.04 ubuntu. I.e. If you install gnome-shell then you are getting it from the official ubuntu repository and the gnome 3 ppa is just adding some minor ancillary updated gnome packages around it.

I do recommend that ubuntu gnome-shell users add the gnome 3 ppa though as there are some worthwhile enhancements and fixes in those ancillary packages.

---

