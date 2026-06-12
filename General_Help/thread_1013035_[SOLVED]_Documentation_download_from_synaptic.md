---
title: "[SOLVED] Documentation download from synaptic"
date: 2008-12-16
forum: General Help
---

### Post by juanp.contreras on 2008-12-16
Hi,

I have downloaded the following documentation...

c++-annotation
haskell98
libace-doc
perlprimer-doc
python-doc
texlive-doc-en

¿Where does Synaptic store that packages/files?

Thanks

---

### Post by unutbu on 2008-12-16
Here is one way to find the files installed by a package:
```
dpkg --listfiles PACKAGE
```
For example:
```
dpkg --listfiles python-doc
```

Alternatively, right-click on the package in Synaptic. Choose Properties, and look under the "Installed files" tab.

---

