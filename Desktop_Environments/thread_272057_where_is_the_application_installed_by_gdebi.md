---
title: "where is the application installed by gdebi"
date: 2006-10-05
forum: Desktop Environments
---

### Post by ryu kun on 2006-10-05
I installed a debian package by gdebi but I can't find neither its path nor Gdebi in my Applications menu. I've also checked my Debian menu but Gdebi is not here either.

I wonder where to find installed app's and how do we manage (uninstall/reinstall) installed packages by Gdebi.

Any ideas?

Regards

---

### Post by Jagot on 2006-10-05
It should show up in Synaptic.

To run it, try hitting alt+f2 and type the package name.

---

### Post by lamego on 2006-10-05
You can also type:
```
dpkg -L package
```

To list the filest installed by the package.

---

