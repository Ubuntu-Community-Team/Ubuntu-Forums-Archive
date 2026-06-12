---
title: "Deb files"
date: 2009-02-19
forum: General Help
---

### Post by u'b'u'n't'u on 2009-02-19
When i open up a deb it goes to the installer and says "close any open package managers" and i dont have any open! i even looked in sessions

---

### Post by Yellow Pasque on 2009-02-19
If you're absolutely sure you don't have any package managers running (you might want to reboot), then you can remove the lock file
```
sudo rm /var/lib/dpkg/lock
```

---

