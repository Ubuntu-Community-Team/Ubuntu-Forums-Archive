---
title: "AptOnCD,installed package to cache???"
date: 2009-05-25
forum: General Help
---

### Post by colau on 2009-05-25
Hi,
Is it possible to cache whole installed packages?
If I do aptitude clean then is there any way to cache those packages again?

---

### Post by colau on 2009-05-25
Bump.

---

### Post by nhasian on 2009-05-26
Yes, use aptoncd to make a CD/DVD/iso image of your installed packages.  you could then either just insert the disc and install your packages directly from the disc, or copy them all back to /var/cache/apt/archives.  AptOnCD is quite easy to use :)

> **colau said:**
> Hi,
Is it possible to cache whole installed packages?
If I do aptitude clean then is there any way to cache those packages again?

---

