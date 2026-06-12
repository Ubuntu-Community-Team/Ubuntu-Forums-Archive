---
title: "Unity and LibreOffice interface doesn't match ubuntu 11.10"
date: 2011-10-06
forum: Desktop Environments
---

### Post by kakesh on 2011-10-06
In Ubuntu 11.10 beta 2  Unity window interface and office doesn't match for some reason. Seems like LibreOffice has some old 5 year old square buttons instead of something more aesthetically beautiful (as AbiWord on screenshot). Is there a way to fix that so it will look more like all other GUI's?

---

### Post by Copper Bezel on 2011-10-06
Under Gnome 2, the separate package libreoffice-gtk provided the Gnome desktop integration for the Libreoffice suite. It has been ported to GTK3 (as Oneiric uses) but I'm not certain whether it's under the same package name. I'd look around in Synaptic for a similarly named package. A quick Google search isn't bringing up anything relating to this problem, and I know that Libreoffice had this desktop integration when it first hit Oneiric, so it's possible that something else is broken, here.

That should give you some terms to poke around until someone else doing testing can give you a more definitive answer. I'm on 11.04, myself.

---

### Post by coffeecat on 2011-10-07
Just to confirm that what you are seeing is not what usually happens. See my screenshot. That's LibreOffice in an updated Oneiric Beta. I'm not sure where yours has gone wrong - probably in LO's settings. If I find something I'll post back.

**EDIT**: it could be theme-related. Is that the Adwaita theme? Try the default Ambiance and see if you get the same as in my screenshot.

---

### Post by proxy.qtz on 2011-10-07
Yeah, that's definitely not supposed to happen...

---

### Post by kakesh on 2011-10-07
So I ended up completely removing old libreoffice, installed new one but the problem still was there. Than I checked add-ons and installed GNOME integration (libreoffice-gnome) and GTK+ integration (libreoffice-gtk) and everything is fine now. I guess could've just install add-ons without removing old office, but didn't know that , missing add-ons were a problem. I do not know why those add-ons weren't installed at firs place.

---

