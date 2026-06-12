---
title: "Fonts ugly in Xorg after XGL install"
date: 2006-08-17
forum: Desktop Environments
---

### Post by Ramses de Norre on 2006-08-17
Yesterday and today there were upgrades for a couple of packages in the XGL repos, I use this ones: ```
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main

```
This upgrades included libfreetype(-dev) and libcairo2(-dev), and since then my fonts look very blurry and ugly.. Restoring this packages to previous versions results in packages as libpango being uninstalled..

Is there any way to restore my font quality without harming XGL or Xorg? (I use them both)

EDIT: the title isn't correct, I allready noticed the fonts are the same in XGL (blurry!)

---

### Post by squishywalrus on 2006-08-29
Anybody know the answer here?  I'm having the same trouble.

---

### Post by lazyd2 on 2006-08-29
These packages have been removed you'll have to downgrade.
Check [this post in Compiz forum]("http://www.compiz.net/topic-3116-6.html")

---

