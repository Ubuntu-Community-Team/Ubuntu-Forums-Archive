---
title: "removing kde programs in gnome"
date: 2008-12-22
forum: General Help
---

### Post by Howitzer777 on 2008-12-22
i installed kde on ubuntu to see what i would be like but i uninstalled it but the programs stayed. so how would i go about removing them?

---

### Post by taurus on 2008-12-22
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Howitzer777 on 2008-12-22
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by taurus on 2008-12-22
Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

---

