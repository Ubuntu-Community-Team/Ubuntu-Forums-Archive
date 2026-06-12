---
title: "make: command not found"
date: 2006-01-11
forum: Desktop Environments
---

### Post by GQed76 on 2006-01-11
I am trying to install the latest ndiswrapper and when i go to make it, it says bash command not found.

this is a new install of AMD64 with no net connection..what do i need to do to make this...or

how to i make the tar file a deb file so i can dpkg -i it

---

### Post by 23meg on 2006-01-11
If you don't have a net connection you'll need to grab all packages you need (basically everything installed with build-essential) off [http://packages.ubuntu.com](http://packages.ubuntu.com) one by one, with their dependencies, and transfer them to your computer, and I know this is a painful task, because I've had to do it.. I'd say do your best to get that machine online first and install build-essential via apt if possible.

---

### Post by aysiu on 2006-01-11
```
sudo apt-get install build-essential
```

---

