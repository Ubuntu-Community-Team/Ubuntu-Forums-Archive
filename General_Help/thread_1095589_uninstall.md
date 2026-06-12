---
title: "uninstall"
date: 2009-03-13
forum: General Help
---

### Post by Sojurner on 2009-03-13
IF i use apt-get install to install a package how do i uninstall that same package.

---

### Post by aesis05401 on 2009-03-13
apt-get remove

Read 'man apt-get' 

Some other nice features:
apt-get autoclean
apt-get autoremove 

Either that or launch Synaptic via 'gksudo synaptic', search for your package, right click, remove/completely remove.

---

### Post by iaculallad on 2009-03-13
That would be:

```
sudo apt-get remove application_name
```

---

