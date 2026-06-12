---
title: "libpng12.so.0 is missed"
date: 2019-08-22
forum: Debian
---

### Post by setonic on 2019-08-22
I am trying to install Maya 2019. Runing comand  ./setup gave me this: error while loading shared libraries:  libpng12.so.0: cannot open shared object file: No such file or directory

Where and how to get libpng12.so.0?

---

### Post by #&amp;thj^% on 2019-08-22
According to [https://github.com/tcoopman/image-webpack-loader/issues/95](https://github.com/tcoopman/image-webpack-loader/issues/95), you can use:
```

wget -q -O /tmp/libpng12.deb http://mirrors.kernel.org/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.54-1ubuntu1_amd64.deb \
  && dpkg -i /tmp/libpng12.deb \
  && rm /tmp/libpng12.deb
```
This code d-loads the package to the /tmp/ directory and installs it, then removes the .deb (Package)
**_Let it be clear here I bare no responsibility, if this creates other problems with your OS. ;)_**

---

### Post by CatKiller on 2019-08-23
Libpng 1.2 is the version from 2016. It's pretty bad that Autodesk are putting in hard dependencies on things that old.

You can get it from [packages.ubuntu](https://packages.ubuntu.com/xenial/libpng12-0) and either install it like any other package or just extract the file you need and stick it in Maya's directory.

You might even be able to just symlink your existing libpng 1.6 to  libpng12.so.0 without installing anything.

---

### Post by setonic on 2019-08-23
> **CatKiller said:**
> Libpng 1.2 is the version from 2016. It's pretty bad that Autodesk are putting in hard dependencies on things that old.

You can get it from [packages.ubuntu]("https://packages.ubuntu.com/xenial/libpng12-0") and either install it like any other package or just extract the file you need and stick it in Maya's directory.

You might even be able to just symlink your existing libpng 1.6 to  libpng12.so.0 without installing anything.

1. Thanks, will try to download from old repositories (I am on Debian 10 - so will try to get it from jessy).
2. I tried to create symbilic link - did not work - still wants original libpng12-0.
3. I also found out that Autodesk requiers to have multi-network license to run Maya on Linux. This is sad evem more than issue with libpng12.

---

### Post by setonic on 2019-08-23
[QUOTE=According to [https://github.com/tcoopman/image-we...ader/issues/95]("https://github.com/tcoopman/image-webpack-loader/issues/95"), you can use:[/QUOTE]

Thanks.

---

### Post by oldos2er on 2019-08-23
Thread moved to *Debian.*

---

### Post by mikeinse on 2020-02-15
I have also faced same problem. Thank you very much for the information.

---

### Post by wildmanne39 on 2020-02-15
Old thread closed.

---

