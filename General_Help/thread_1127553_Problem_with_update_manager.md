---
title: "Problem with update manager"
date: 2009-04-16
forum: General Help
---

### Post by ismialexis on 2009-04-16
I get this error message
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

then i put sudo dpkg --configure -a in a terminal
and it gave this message

dpkg: failed to write status record about `dnsutils' to `/var/lib/dpkg/status': No space left on device


I tried to delete stuff using disk usage analyzer and when i click move to trash it says could not find a trash folder on this sytem The folder "user" was not moved to the trash.

what should I do?

---

### Post by taurus on 2009-04-16
Applications -> Accessories -> Terminal
```
sudo apt-get clean
sudo apt-get autoremove
df -h
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ismialexis on 2009-04-16
E: Unmet dependencies. Try using -f.

---

### Post by taurus on 2009-04-16
```
sudo apt-get install -f
```

---

