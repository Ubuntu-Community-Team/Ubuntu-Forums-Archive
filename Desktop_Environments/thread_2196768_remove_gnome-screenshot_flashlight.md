---
title: "remove gnome-screenshot flashlight"
date: 2013-12-31
forum: Desktop Environments
---

### Post by pedryvo on 2013-12-31
Hello there,

been looking for a way to remove automatic light of gnome-screeshot (common print screen software in ubuntu) but i didn't found any solution. anyone know how to do it? maybe uninstalling the package and modifying the source code, but I have not found one package of it sources, and I don't know how to install this specific modified package. some help would be very welcome.

thanks!

---

### Post by mc4man on 2014-01-01
source is -
apt-get source gnome-screenshot

The flash effect in a Gs session is done thru 'cheese-flash'
Possibly you can disable it or failing that set it, (thru it's defines), to be almost unnoticeable

The other possibility is to extend the ubuntu patch(s) to include gnome session (whether the source used in the Ubuntu Gnome install has ubuntu/unity patches I don't know

---

