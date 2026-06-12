---
title: "[SOLVED] configure: error: Fluxbox"
date: 2007-08-02
forum: Desktop Environments
---

### Post by killphil on 2007-08-02
I used apt-get --purge autoremove to get rid of fluxbox cause repos version wouldn't save menu config changes.  I download  tar.gz and type 
tar -zxvf 
then

```
./configure
```
and I get
```
configure: error: Fluxbox requires the X window System libraries and headers.
```

---

### Post by killphil on 2007-08-02
solved using
```
apt-get install xorg-dev
```

---

### Post by kerry_s on 2007-08-02
for next time->

```
apt-get source packagename

apt-get build-dep packagename
```

and you won't run into things like that

---

