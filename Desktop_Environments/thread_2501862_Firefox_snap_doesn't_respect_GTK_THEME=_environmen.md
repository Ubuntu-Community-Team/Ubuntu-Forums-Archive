---
title: "Firefox snap doesn't respect GTK_THEME= environment variable"
date: 2024-10-23
forum: Desktop Environments
---

### Post by SpoZen on 2024-10-23
I'm coming from Debian where this worked. I set ```
GTK_THEME=Gruvbox-Dark
``` and all my GTK apps use this theme. On Ubuntu firefox is installed by snap so I gather it works differently. 

How can I use a custom theme on Firefox snap?

---

### Post by Dennis N on 2024-10-23
The theme has to be a snap package before a snap application will use it.
Search for available themes and theme collections with:

snap search theme | grep -i theme

Many users uninstall the snap and use another packaging option for Firefox like Flatpak or a .deb from a PPA.
Firefox also has 'themes' installable from Firefox Menu > Tools > Add-ons and Themes

---

### Post by SpoZen on 2024-10-25
Thanks, I decided to install Firefox from the [mozilla repos]("https://askubuntu.com/questions/1516223/how-to-install-firefox-from-official-mozilla-repository-on-ubuntu-24-04") instead. But Canonical should really fix this if they want people to use snap.

---

