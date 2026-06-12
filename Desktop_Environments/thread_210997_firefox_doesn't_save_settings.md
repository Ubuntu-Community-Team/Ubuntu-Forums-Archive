---
title: "firefox doesn't save settings"
date: 2006-07-07
forum: Desktop Environments
---

### Post by BungaMan on 2006-07-07
Changing simple things like the icon size doesn't save.  I've looked at the files under .mozilla/ and they all have the right user assigned (me).  When I run firefox as root it works just fine.  With my own user every time I start firefox everything is reset.

Any idea's where to look?  I've already reinstalled ff with synaptic.  It doesn't allow to do a complete uninstall because that would require gnome-app-install, ubuntu-desktop and yelp to be uninstalled as well (for whatever reason that may be).

---

### Post by BungaMan on 2006-07-10
No idea's? Do you need more details?

---

### Post by aysiu on 2006-07-10
You looked at *every* single file in the .mozilla folder?

I think it's probably best to use ```
sudo chown -R bungaman:bungaman ~/.mozilla
``` and then the next time you need to run Firefox as root, do ```
gksudo firefox
``` instead of ```
sudo firefox
``` Read more about why here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by BungaMan on 2006-07-14
I'll give it a try this evening and post the results. thanks

---

### Post by BungaMan on 2006-07-14
Well it didn't do the trick so I renamed my .mozilla directory and now it's fine.

---

