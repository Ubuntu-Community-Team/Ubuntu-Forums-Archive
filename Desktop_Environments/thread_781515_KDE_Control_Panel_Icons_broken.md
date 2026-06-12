---
title: "KDE Control Panel Icons broken?"
date: 2008-05-04
forum: Desktop Environments
---

### Post by hodenkat on 2008-05-04
After upgrading to Hardy, I've noticed in my Applications/Other menu, many of the icons are "generic". They all seem to be part of a KDE package called "kcontrol" and they each bring up one kind of control panel or another dealing with everything from "cache" to "file associations". There are over 20 of them and they all have the same icon (generic). Does anybody else have this? Is it possible to fix the icons so they look like normal program icons?

---

### Post by Xiong Chiamiov on 2008-05-04
It sounds like the icon theme you're using doesn't have icons for those things.  Which icon set are you using?  Do you have KDE installed on top of Ubuntu?

---

### Post by hodenkat on 2008-05-04
Thanks for the reply!

No, I don't have KDE installed on top of Ubuntu.
I don't think that's even possible.
I'm using the standard Gnome icon set and the only thing I've loaded besides a few programs is a download manager from SUN (java).

I had to download it to get virtualbox from their website.
I have since uninstalled virtualbox because I could not get it to work.

The apps that have broken icons do work, and I don't wish to uninstall them because they look like a few of them could be useful in the future.

Thanks!

---

### Post by hodenkat on 2008-05-05
Quick update:

I don't know how I ended up loading the package, but all the broken icons (and a few that look fine) are part of a package called kcontrol.
Dependent packages are kdebase-data, kicker, and libkonq4.

I removed kcontrol and all the generic icons went with it.
Just to see if reloading would fix the icons I reloaded it but they were still broken. Functional, but with generic icons.:confused:

---

