---
title: "Total reset."
date: 2009-01-04
forum: General Help
---

### Post by Peter_G on 2009-01-04
Is there anyway I can reset everything to the original install state, apart from some files. And backing them up on an external hard drive isn't an option since I'd need to back up about 150gb of stuff and I only have 120gb space on my external hard drive, please help :( , thanks.

---

### Post by northern lights on 2009-01-04
As for installed applications/packages you'd have to manually remove unneeded software.

When it comes to configuration, you could simply add a new user, either via the GUI (System > Administration > Users & Groups) or the commandline```
sudo useradd NEWUSER
sudo passwd NEWUSER
```where NEWUSER needs to be replaced by the desired username.
Subsequently add the new user to the admin group to give him root rights.

```
sudo usermod -G NEWUSER,adm,dialout,cdrom,plugdev,lpadmin,admin,sambashare NEWUSER
```

Log-out, log-in with new user. The system will look like after a fresh install.

Regarding the applications, run```
sudo apt-get autoclean && sudo apt-get autoremove
```to remove obsolete packages that nothing currently installed depends on.

Then remove packages you don't want anymore via```
sudo aptitude purge PACKAGE
```

---

