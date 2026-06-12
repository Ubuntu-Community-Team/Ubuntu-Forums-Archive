---
title: "how to uninstal ubuntu netbook remix packages from terminal"
date: 2009-10-12
forum: Desktop Environments
---

### Post by phoenixjgibson on 2009-10-12
hi, i am running 9.04 standard on my netbook (aao) and i installed the netbook remix packages from synaptic and gnome started acting screwy and then crashed. now it crashes everytime on startup. i am prety shure its the netbook remix becouse i have had GUI problems with it before on this computer. so how can i uninstal all the ubuntu netbook remix packages from the terminal?

---

### Post by coldReactive on 2009-10-12
Search for packages that are like the names listed here: [http://en.wikipedia.org/wiki/Ubuntu_Netbook_Remix#Packages_That_Make_Up_UNR](http://en.wikipedia.org/wiki/Ubuntu_Netbook_Remix#Packages_That_Make_Up_UNR)

(if you can't find them, find them in packages.ubuntu.com) then sudo apt-get purge in terminal with the packages.

---

### Post by phoenixjgibson on 2009-10-12
i booted into recovery mode and used the auto fix graphics option and now it works fine, but i have always wanted to know how to uninstal through terminal anyways so thanks!

---

### Post by ugm6hr on 2009-10-13
```
sudo apt-get remove netbook-launcher maximus
```

---

