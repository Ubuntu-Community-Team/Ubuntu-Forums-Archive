---
title: "Kde 4.5.1"
date: 2010-09-15
forum: Desktop Environments
---

### Post by OSLinuxFreak on 2010-09-15
Hope this is the right area for this, if not I do apologize. I just recently added the ppa:kubuntu-ppa/backports to my repository as the KDE site suggested for 4.5.1. One I refreshed there were several updates available seem o be fine but there is also approx 145 Blocked Updates with a big red X beside them.

Could someone tell my what blocked updates are and should I hold off on installing them?

Anyhelp would be appreciated :)

---

### Post by solar george on 2010-09-15
Blocked updates is an annoying description, basically it means that an update would need to install/remove another package to satisfy its dependencies and the ordinary update manager won't do this.
You can either run an apt-get dist-upgrade at the command line or use a full package manager like synaptic or muon to do the upgrade. In either case check what other changes get marked to make sure some mistake is not causing it to try and remove the kernel or something.

---

### Post by OSLinuxFreak on 2010-09-16
> **solar george said:**
> Blocked updates is an annoying description, basically it means that an update would need to install/remove another package to satisfy its dependencies and the ordinary update manager won't do this.
You can either run an apt-get dist-upgrade at the command line or use a full package manager like synaptic or muon to do the upgrade. In either case check what other changes get marked to make sure some mistake is not causing it to try and remove the kernel or something.

Thanks Solar I appreciate the reply. Will see what happens lol :D

---

