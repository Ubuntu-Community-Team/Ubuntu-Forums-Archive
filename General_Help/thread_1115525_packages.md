---
title: "packages"
date: 2009-04-03
forum: General Help
---

### Post by shane8002 on 2009-04-03
Im trying to get packages installed on one computer and transfer them to another so I don't half to download them again. Is there a certain place all packages are stored in the file system so I could put them on USB and transfer them to another computer.

---

### Post by vegetarianshrimp on 2009-04-03
you can search for the packages at [here]("http://packages.ubuntu.com"), download the debs, and transfer them to your other computer.

---

### Post by taurus on 2009-04-03
They should be in /var/cache/apt/archives.

Applications -> Accessories -> Terminal
```
ls -la /var/cache/apt/archives
```
Look in aptoncd.

---

### Post by shane8002 on 2009-04-03
You were right bro, thats exactly what I was looking for thanks alot.

---

