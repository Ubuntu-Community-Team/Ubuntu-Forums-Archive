---
title: "Update Manager vs apt-get upgrade"
date: 2009-03-17
forum: General Help
---

### Post by ufarmer on 2009-03-17
What's the difference between using the Update Manager and running apt-get update/upgrade?  I just ran apt-get update and apt-get upgrade and noticed that there were still updates that could be installed using the Update Manager.

---

### Post by Nano_ext3 on 2009-03-17
Upgrade in terminal only updates packages "marked" for upgrade, while update manager probes all packages for new "versions" not just ones marked for upgrade.  You will notice this in Synaptic Package manager, the ones marked for upgrade have a star in the highlighted green box.  Update Manager I think does an extensive probe for new versions.  I could be wrong, but thats the way I view it.

Cheers!

-Nano

---

### Post by kerryhall on 2011-08-05
Is there a way to emulate the upgrade manager functionality using just apt? Thanks!

---

