---
title: "Adept Notifier"
date: 2006-06-17
forum: Desktop Environments
---

### Post by pizeta on 2006-06-17
I had lots of trouble upgrading breezy to dapper using dist-upgrade (caused by gstreamer) but now everything seems fine exept the adept notifier.

It keeps telling that there's an upgradable package but it lies, when i fetch the update list i see the truth, my sistem is up to date, and the icon with the false message won't disappear...

any help ?
i tried spt-get -f install, dpkg --configure -a but nothing

---

### Post by pizeta on 2006-06-19
i found the problem

/etc/apt/source.list was not user readable.

---

