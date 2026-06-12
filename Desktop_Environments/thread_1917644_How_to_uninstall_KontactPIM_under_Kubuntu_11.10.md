---
title: "How to uninstall Kontact/PIM under Kubuntu 11.10?"
date: 2012-01-30
forum: Desktop Environments
---

### Post by uqbar on 2012-01-30
I've been asked to uninstall any PIM-related stuff from a number of Kubuntu desktops.
This seems not to be doable without uninstalling KDE.
KDE people say there'd be no side effect: KDE can live without akonadi, nepomuk, Kontact, KMail etc.

Any idea?

Thanks.

---

### Post by uteck on 2012-01-30
That is correct, KDE works fine without the PIM and the akonadi/nempomuk stuff.  Many say it even works better since akonadi and nepomuk have a tenancy to make the system unusable while unused files are indexed for the ten thousandth time that day.

---

### Post by oldos2er on 2012-01-30
Worked for me: ```
root@ann-Dell-XPS-410:~# aptitude remove kontact
The following packages will be REMOVED:  
  kontact 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 930 kB will be freed.
(Reading database ... 310425 files and directories currently installed.)
Removing kontact ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```

---

