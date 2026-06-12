---
title: "What is the best way to remove Openoffice 2.4 before Upgrade Openoffice 3.0?"
date: 2008-12-04
forum: General Help
---

### Post by asaren on 2008-12-04
Hi All,

What is the best way to remove Openoffice 2.4 before Upgrade Openoffice 3.0? 

Synaptic? but it shows up a lot stuff. I dont know which one to remove.

Thank you so much.

---

### Post by iaculallad on 2008-12-04
To remove your existing OO version:

```
sudo apt-get --purge remove openoffice.org-core
```

---

