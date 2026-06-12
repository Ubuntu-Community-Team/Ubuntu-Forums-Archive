---
title: "No_pubkey cebec1b70570c5c6"
date: 2009-05-08
forum: General Help
---

### Post by klausner on 2009-05-08
The latest 3.1 OpenOffice upgrade is bitching about missing keys again in Intrepid. Anyone have the fix?

---

### Post by fooman on 2009-05-08
not sure,  but try this command in a terminal:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com cebec1b70570c5c6
```hope that helps.

---

### Post by klausner on 2009-05-08
> **fooman said:**
> not sure,  but try this command in a terminal:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com cebec1b70570c5c6
```hope that helps.

Thanks. That seemed to do it. Now aptitude just complains the package has been kept back, presumably awaiting language packs (at least that's what a Goggle search suggests.)

Don't know why every OO upgrade seems to be a PITA in regard to getting the right keys installed.

Thanks again.

---

### Post by zvacet on 2009-05-08
```
sudo apt-get dist-upgrade
```

---

