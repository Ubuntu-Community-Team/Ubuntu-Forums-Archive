---
title: "Uninstalling Evolution without uninstalling Ubuntu Desktop"
date: 2005-01-10
forum: Desktop Environments
---

### Post by Ubuntu_User on 2005-01-10
I recently uninstalled Evolution, but the result was that I also had to uninstall Ubuntu Desktop, and with that the bar at the top of the screen disappeared. Can I uninstall Evolution without removing Ubuntu Desktop, since I guess the bar at the top of the screen is part of it? 

Thank you.

---

### Post by randy on 2005-01-10
You can't uninstall evolution without uninstalling ubuntu desktop.  It's part of the ubuntu-desktop metapackage.  The bar at the top of the screen isn't part of the ubuntu-desktop package, it's a part of your gnome configuration.  You can add it by right clicking on an existing panel and clicking New Panel.  You'll neeed to add the applets and the menu bar that you had on the bar then.

---

### Post by #Greg on 2005-01-10
Ubuntu-desktop can be safely removed, it says it on the site somewhere I believe. I uninstalled evolution using apt and 'evolution-*' the other day (simply because I don't use it).

---

### Post by Ubuntu_User on 2005-01-10
OK, then I'll try again and see what happens. Thanks.

---

### Post by Ubuntu_User on 2005-01-10
I just removed Evolution using apt-get, so far all is still in working order. I guess last time something just went wrong. 

What belongs all to the Ubuntu-Desktop, since it is now gone? I would have thought that Gaim would also be gone, or at least not functional anymore, since it showed an interdependency with Ubuntu-Desktop, but it's still there and working.

---

### Post by poptones on 2005-01-12
The bar depends on evolution data server, which you seem to have removed the first time.

This time you removed evolution, but evolution data server (which gaim and the bar depend upon) is still installed.

---

### Post by Stefan Koopmanschap on 2005-01-13
I just ran into some confusion as well because of this. I was a bit scared at seeing the ubuntu-desktop package in the to-uninstall list after selecting the uninstallation of Evolution. Good to see though that it isn't a problem to actually remove it. But isn't the name of the ubuntu-desktop package slightly confusing and thus chosen incarefully? Seeing that name in the list of apps to remove might make people think they're uninstalling their whole desktop system.

---

### Post by Ubuntu_User on 2005-01-13
poptones> Thanks for the explanation.

Stefan> I agree, it is a bit confusing if you don't know what is meant with 'ubuntu-desktop'.

---

