---
title: "how to uninstalll a install software"
date: 2009-04-30
forum: General Help
---

### Post by mubbashar on 2009-04-30
please tell me how to uninstalll a install software

---

### Post by Grenage on 2009-04-30
sudo apt-get remove xxx

Or via the package manager.

---

### Post by taurus on 2009-04-30
How did you install it initially?  Did you install it through add/remove, synaptic, apt-get/aptitude, dpkg, or compile it yourself?

---

### Post by mubbashar on 2009-04-30
i have install deb file

---

### Post by taurus on 2009-04-30
If you installed the .deb, then you must have used **sudo dpkg -i package_name.deb**.  If you want to remove it, use the -r option then.

```
sudo dpkg -r package_name
```

---

