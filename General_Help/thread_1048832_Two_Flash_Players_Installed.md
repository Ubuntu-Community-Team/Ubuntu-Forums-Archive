---
title: "Two Flash Players Installed"
date: 2009-01-23
forum: General Help
---

### Post by sjl127 on 2009-01-23
Since I have two different flash players installed within firefox, how do I delete one of them, specifically the adobe one?

---

### Post by mikewhatever on 2009-01-24
Adobe flash is usually removed by <sudo apt-get remove flashplugin-nonfree>.

---

### Post by philinux on 2009-01-24
sudo apt-get remove adobe-flashplugin

It comes from the partner repo.

flashplugin-nonfree downloads and install the adobe plugin anyway. They are the same version. But you only need one installed.

---

