---
title: "Need learn 'purge'"
date: 2009-01-30
forum: General Help
---

### Post by jesse c on 2009-01-30
Trying to get acer wifi working i found a forum that tells me to 'purge' all evidence of 'ndiswrapper' and the athos driver that shows up in sys/admin/hardware driver.I can uninstall the athos driver but how do i 'purge all evidence' of things?

---

### Post by drs305 on 2009-01-30
There is an option for both apt-get and aptitude to "purge" to remove the app and all configuration files ( example: sudo aptitude purge *appname* ). You can read about it by typing:
```

man apt-get
man aptitude

```

The closest synaptic equivalent would be "Mark for complete removal"

---

