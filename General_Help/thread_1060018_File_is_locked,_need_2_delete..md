---
title: "File is locked, need 2 delete."
date: 2009-02-04
forum: General Help
---

### Post by nemiux on 2009-02-04
Ok, look, i need to delete 1 file, but it doesn't let me (no-ip directory in [http://img22.imageshack.us/img22/418/helpmewithittr0.png](http://img22.imageshack.us/img22/418/helpmewithittr0.png) picture)
I tried gksu nautilus, but it didnt help, still premission denied, how should i delete it?

---

### Post by taurus on 2009-02-04
Applications -> Accessories -> Terminal
```
cd ~/Desktop
sudo rm -rf noip-2.1.9-1
ls -la
```

---

