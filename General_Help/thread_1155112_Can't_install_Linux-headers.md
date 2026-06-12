---
title: "Can't install Linux-headers"
date: 2009-05-10
forum: General Help
---

### Post by gletob on 2009-05-10
I need them to install virtualbox
```
glenn@glenn-laptop:~$ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.28-8-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.28-8-generic has no installation candidate
```

---

### Post by danwood76 on 2009-05-10
If you install linux-headers-generic it should just install the correct version for you.

If that doesnt work I would update your kernel, the latest version is -11 so you are a few releases behind.

---

### Post by gletob on 2009-05-10
Thank you.  I had to delete my menu.lst, for some reason update-grub was not changing my menu.lst I ended up just deleting it and running sudo update-grub.  I already had the linux-image and linux-headers installed but I was running old kernel!

---

