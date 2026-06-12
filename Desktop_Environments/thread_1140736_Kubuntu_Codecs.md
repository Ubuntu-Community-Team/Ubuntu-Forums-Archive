---
title: "Kubuntu Codecs?"
date: 2009-04-27
forum: Desktop Environments
---

### Post by dsg536 on 2009-04-27
Once again, I've spent a while trying to figure this out on my own (including google and the native search function here).

How do I view video files with the Dragon player?  Is it possible?  It doesn't appear so (e.g. - no native "w32codecs" in KDE).

Please help.

EDIT - when I try to play files, I get a message along the lines of "Dragon player recommends installing packages for extra multimedia functionality".  But it does not tell me what packages to install - nor does google.

---

### Post by Monsieur Gonzalez on 2009-04-28
You want to install kubuntu-restricted-extras, either from the package manager of from the command line (sudo apt-get install kubuntu-restricted-extras).

---

### Post by kde4-core-user on 2009-04-28
KPackagekit 0.4.0 is not able to show confirmation dialog boxes, so you must install this with:

```
sudo apt-get install kubuntu-restricted-extras
```

w32codecs:
[http://packages.medibuntu.org/jaunty/index.html](http://packages.medibuntu.org/jaunty/index.html)

---

