---
title: "Bonded network working but not recognised in gnome desktop"
date: 2020-06-05
forum: Desktop Environments
---

### Post by gourmetsaint on 2020-06-05
I am running Ubuntu Server 20.04 with two NICs bonded as bond0. The connection is working but the installed ubuntu-desktop does not recognise the bond0 connection and doesn't allow me to share desktop or implement Livepatch (says requires internet connection).

Any ideas?

Regards,

Mark

---

### Post by gourmetsaint on 2020-06-06
Found it! Just had to rewrite the yaml file and change renderer to NetworkManager. Some syntax changes to suit and then sudo netplan generate to check before sudo netplan apply.

---

