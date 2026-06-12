---
title: "k3b burning failed- cdrecord has no permission to open the device - solved"
date: 2009-02-06
forum: General Help
---

### Post by ggeller on 2009-02-06
Set the suid bit for wodim. Open a terminal and:

$ chmod +s /usr/bin/wodim

I have some notes about this at: wsms.wikiplanet.com/mediawiki/index.php/K3b

George

---

### Post by afeasfaerw23231233 on 2009-10-16
Thanks. It helps.

---

