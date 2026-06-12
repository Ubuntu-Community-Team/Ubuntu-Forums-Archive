---
title: "what is linux-server package?"
date: 2009-05-29
forum: General Help
---

### Post by TDK800 on 2009-05-29
sudo apt-get upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-image-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.



Fresh ubuntu server. What are these two packages and why are they kept back?

---

### Post by Yellow Pasque on 2009-05-29
They are just metapackages that point to the actual kernel packages. I don't know why they're held back (try manually upgrading them to find out) or maybe apt-get dist-upgrade is necessary to upgrade them.

---

### Post by TDK800 on 2009-05-29
thanks, dist-upgrade fixed it.

---

