---
title: "Log out menu"
date: 2006-01-09
forum: General Help
---

### Post by Mazin on 2006-01-09
In the Log Out... dialog in the KMenu, the only option listed is "End Current Session".  I want Shut Down and Restart on there too, but I don't know how.  I went to the session manager and made sure "Offer shutdown options" was ticked, but it doesn't show up.

(BTW, mine's actually Ubuntu with KDE installed later)

---

### Post by aysiu on 2006-01-09
```
kdesu kwrite /etc/X11/default-display-manager
```
Change ```
/usr/sbin/gdm
``` to ```
/usr/bin/kdm
``` and save.

---

### Post by noeluylee on 2006-01-10
You installed kde on Ubuntu right? :) that happen because your default desktop environment is GNOME.

if you like the kde to have shutdown and restart option, you have to download and install the kdm.. else you wont get any shutdown option.

run the command on konsole or terminal.

sudo apt-get install kdm
- to get/ download  and install the kdm package for kde

sudo dpkg-reconfigure kdm
- to configure and make kde as your default desktop environment

hope this helps...   if you encounter any error.. just post it here.

---

