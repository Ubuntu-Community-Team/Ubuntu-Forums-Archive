---
title: "Removing Amarok and KDE dependencies from Gnome"
date: 2007-12-07
forum: Desktop Environments
---

### Post by betes on 2007-12-07
Hi. I use gnome only, but installed amarok to try it out.  I would now like to remove amarok and all of the kde dependencies that it installed.

Is there a simple way to do this or do I need to go through the packages in synaptic and try to figure out which ones to remove.

---

### Post by maybeway36 on 2007-12-07
After removing amarok try:
```
sudo apt-get autoremove
```

---

### Post by vishzilla on 2007-12-07
```
sudo apt-get autoremove amarok
```

---

### Post by betes on 2007-12-07
Thanks!

---

### Post by ajopaul on 2007-12-07
to remove any packages completely use ```
sudo apt-get remove --purge *package*
```

---

