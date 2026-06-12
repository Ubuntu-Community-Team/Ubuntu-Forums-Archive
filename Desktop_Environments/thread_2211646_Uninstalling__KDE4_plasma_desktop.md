---
title: "Uninstalling  KDE4 plasma desktop"
date: 2014-03-17
forum: Desktop Environments
---

### Post by nashtrik on 2014-03-17
I was using Trinity desktop environment ( Based on KDE3)  alongside my 12.04 when on an unfortunate day I decided to install kde4 palsma desktop as well. Now I desperately want to remove the latter but am not sure how to uninstall it without messing up my Trinity desktop.I am not sure what all packages were installed with the Plasma Desktop and fear that incorrect uninstallation might corrupt the Trinity desktop as well.

---

### Post by ajgreeny on 2014-03-17
```
grep -iw install /var/log/dpkg.log.1 && grep -iw install /var/log/dpkg.log
``` will give you a list of everything you have installed recently in time and date order,so if you installed the plasma desktop as a single operation and can remember when it was, but did not add it with a lot of other packages at the same moment, you may be able to figure out the many and various packages that were installed as part of the plasma desktop.

You could also try removing just the metapackage (kde-plasma-desktop) then running ```
sudo apt-get -s autoremove
``` in order to see what would be removed if hat command was run without the "-s" switch (simulate- ie show what would happen, but not actually remove anything).  That way you could make sure anything autoremove uninstalled was either added back, or removed from the list when uninstalling.

---

