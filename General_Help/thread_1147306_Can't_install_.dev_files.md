---
title: "Can't install .dev files"
date: 2009-05-03
forum: General Help
---

### Post by jdevuser on 2009-05-03
When I try to install and .deb package that I download the Gdebi package manager gives me and error saying Error: Wrong Architecture "i386". But my computer is and i386 computer. I tried to reinstall Gdebi using synaptic but that didn't help

---

### Post by Happy_Man on 2009-05-03
What are your computer's specs?

---

### Post by Vaphell on 2009-05-03
are you sure you haven't installed 64bit version of ubuntu? because if that's the case, then you need amd64 architecture not i386 - otherwise you get an error.

---

### Post by jdevuser on 2009-05-03
I installed ubuntu using wubi. Wouldn't of ubuntu not work at all if I installed the 64bi version? Everything else works fine

---

### Post by jdevuser on 2009-05-03
My computer has 1gb of ram with a Intel Core 2 Duo T5250 1.5ghz processer. I use wubi to dual boot between ubuntu and vista

---

### Post by Peasantoid on 2009-05-03
This isn't a solution, but you might be able to force the package to install.
```
sudo dpkg -i --force-architecture path/to/package.deb
```

---

### Post by Diabolis on 2009-05-03
Run this command:
```
uname -a
```
It will tell you the specs of your machine/os installation

---

### Post by Peasantoid on 2009-05-03
The Intel Core 2 Duo is x64_64, by the way.

---

### Post by oldos2er on 2009-05-03
> **jdevuser said:**
> My computer has 1gb of ram with a Intel Core 2 Duo T5250 1.5ghz processer. I use wubi to dual boot between ubuntu and vista

 So you've most likely got 64-bit Ubuntu. You'll need to find a 64-bit version of whatever *deb you're trying to install. Or, you can install ia32-libs and use "force-architecture" as was suggested.

---

### Post by jdevuser on 2009-05-03
but I run 32 bit vista on 1gb of ram and have not had a problem

---

