---
title: "If I remove update-manager and update notifier what happends?"
date: 2005-12-09
forum: Desktop Environments
---

### Post by dcast on 2005-12-09
It seems that everytime i try to isntall something say through dpkg that has a dependency problem the package comes up as broken. The icon for update manager pops up in the right hand corner of my gnome toolbar and it seems that stuff starts crashing left right and center. it says if i remove these packages ubuntu-desktop will be removed. When I try to open the update manager it starts opening then crashes. Im not sure what to do?

---

### Post by blueplazma on 2005-12-09
Try bringing up a command prompt and running ```
sudo apt-get -f install
``` and see if that clears things up.

---

