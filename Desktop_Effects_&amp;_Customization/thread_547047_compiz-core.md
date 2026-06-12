---
title: "compiz-core?"
date: 2007-09-09
forum: Desktop Effects &amp; Customization
---

### Post by czepluch on 2007-09-09
I cant update compiz-core . It's says that one update is available, but when I try to install it, it says that the package is installed, but it still says that the same update is available. and if I go to synaptic and look compiz-core is marked automatically for updating, but still cant be updated, and because of that i cant get compiz-extra .

```


E: /var/cache/apt/archives/compiz-extra_0.3.6.1-0ubuntu2_i386.deb: trying to overwrite '/usr/lib/compiz/libbench.so', which is also in the package compiz-fusion-plugins-extra

```

The error code is not totally perfect written. Had to translate it from danish

---

### Post by Chymera on 2007-09-12
if you are using amaranth's repo than it's because of the server that hosts it. It's got some technical difficulties.

---

### Post by Nythain on 2007-09-12
yeah there's a big note in the installation guide i used saying thats gonna happen so you're best off commenting out the repo in /etc/apt/sources.list after you are done installing what you need from it

---

### Post by Forlong on 2007-09-13
If you're on GNOME, just go to *System &#8594; Administration &#8594; Software Sources &#8594; Third Party Software* and uncheck the repository you used.

---

