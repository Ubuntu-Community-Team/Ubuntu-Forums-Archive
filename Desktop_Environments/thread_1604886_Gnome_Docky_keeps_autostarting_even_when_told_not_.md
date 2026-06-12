---
title: "Gnome Docky keeps autostarting even when told not to"
date: 2010-10-24
forum: Desktop Environments
---

### Post by ryukent on 2010-10-24
I had the problem where Docky would ignore turning off 'start when computer starts' function. It would run automatically every time I logged in, even in KDE and LXDE.

The solution was as follows:

sudo add-apt-repository ppa:docky-core/ppa

This adds the docky repository. Then do:

sudo apt-get update

Finally, check for updates and the new docky should be installed removing the bug.

**EDIT**: For more information on making it only start in Gnome and not KDE and removing the hard links so that you can pin whatever you want try this link:

[http://www.ryukent.co.uk/2010/10/setting-up-docky-in-ubuntu-10-10/]("http://www.ryukent.co.uk/2010/10/setting-up-docky-in-ubuntu-10-10/")

---

