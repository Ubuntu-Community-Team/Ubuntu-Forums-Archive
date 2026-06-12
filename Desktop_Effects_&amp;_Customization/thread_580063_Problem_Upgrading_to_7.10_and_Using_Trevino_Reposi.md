---
title: "Problem Upgrading to 7.10 and Using Trevino Repositories?"
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by Amaranth on 2007-10-18
If you used Trevinho's repo for compiz in Ubuntu 7.04 you have to completely remove all compiz and libcompizconfig packages, make sure his repo is removed from your sources.list, then reinstall compiz.

---

### Post by Forlong on 2007-10-19
I might add, Treviño's repository is this one: [http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/index.html](http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/index.html)

So look for this line in your /etc/apt/sources.list or **System &#8594; Administration &#8594; Software Sources &#8594; Third Party Software**:
```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
```
And you should remove the sources (deb-src) as well (if present).

---

### Post by K.Mandla on 2008-02-28
Unstickying.

---

