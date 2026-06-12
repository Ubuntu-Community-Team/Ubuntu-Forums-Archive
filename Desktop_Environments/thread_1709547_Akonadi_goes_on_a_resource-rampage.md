---
title: "Akonadi goes on a resource-rampage"
date: 2011-03-18
forum: Desktop Environments
---

### Post by tuxerman on 2011-03-18
I'd just upgraded (rather, fresh install) to Kubuntu 10.10 two months back. For the record, I'd also installed xfce4 package (not xubuntu-dekstop) a few days back.. For the past few days, every time I start my computer and log into the kde desktop, it got very sluggish, and froze with the system monitor widgets recording a ramp-like increase in RAM usage and CPU being constantly at 100%.
A glance at the system monitor showed akonadi-contacts to be the culprit, and I killed it. Everything returned to normal, but problem persisted with every login. I even tried disabling it from services. I also removed it from the packages but kde also got removed along with it, and I had to reinstall KDE from apt. But even after reinstalling kde the problem was back.

At wits end what to do. Please help!

PS: I dont use akonadi for anything so good riddance options also welcome :D

---

### Post by tuxerman on 2011-03-18
bump

---

### Post by tuxerman on 2011-03-23
It's fine folks, i just added a shell script with:

pkill akonadi

to my KDE startup :D

---

### Post by Alejandro Nova on 2011-03-25
Looks like the [Contacts + Nepomuk + Akonadi mega bug fixed in KDE 4.6.1.]("https://bugs.kde.org/show_bug.cgi?id=246678")

Load the Kubuntu Backports PPA and upgrade everything to KDE 4.6.1. Ensure yourself you have Akonadi 1.5.1. Shouldn't give you headaches. Instructions to do that are in [http://www.kubuntu.org](http://www.kubuntu.org)

---

