---
title: "Xfce- Stop Beagle from autostarting"
date: 2008-01-07
forum: Desktop Environments
---

### Post by dbbolton on 2008-01-07
Every time I start an Xfce session, Beagle starts up automatically.

I disabled the Beagle Search Daemon (beagled-autostart.desktop) and Beagle Search Tool (beagle-search-autostart.desktop) from  ~/.config/autostart but it still starts up.

How can I disable it?

---

### Post by jej2003 on 2008-01-07
is it still listed under applications -> settings -> auto started appications?

---

### Post by dbbolton on 2008-01-07
> **jej2003 said:**
> is it still listed under applications -> settings -> auto started appications?
no

---

### Post by dbera on 2008-01-08
> **dbbolton said:**
> Every time I start an Xfce session, Beagle starts up automatically.

I disabled the Beagle Search Daemon (beagled-autostart.desktop) and Beagle Search Tool (beagle-search-autostart.desktop) from  ~/.config/autostart but it still starts up.

How can I disable it?

Are you sure that Xfce respects the xdg spec of ~/.config/autostart ? Could you double check that the autostart file for begle-search and beagled are correct ?

---

### Post by dbbolton on 2008-01-08
> **dbera said:**
> Are you sure that Xfce respects the xdg spec of ~/.config/autostart ? Could you double check that the autostart file for begle-search and beagled are correct ?
I'm pretty sure that the contents of ~/.config/autostart show up under Xfce Menu > Settings > Autostarted Applications. In both places, I see Volume Manager, Restricted Drivers Manager, Power Manager, and Update Notifier. 

I changed the beagle .desktop files to non-executable plain text files.

---

### Post by dbbolton on 2008-01-10
Well, I decided to uninstall beagle. However, I would still appreciate a solution.

---

### Post by dbera on 2008-01-11
> **dbbolton said:**
> Well, I decided to uninstall beagle. However, I would still appreciate a solution.

I can think of two possibilities:
1) There is another installation of beagle in an incorrect prefix (like /usr/etc or /usr/local/etc) which is starting beagled even though it is disabled in the right place.

2) The .desktop file is incorrect. If you can post it here, maybe someone will spot an error. I know how the autostart line looks in gnome, "X-Gnome-Autostart..."

---

