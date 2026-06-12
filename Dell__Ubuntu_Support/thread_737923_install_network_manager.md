---
title: "install network manager"
date: 2008-03-28
forum: Dell  Ubuntu Support
---

### Post by eranga_04 on 2008-03-28
Hi

I try to install network manager-gnome but it can't install without dependencies. then, I downloaded several dependencies and last one is tzdata. it doesn't need any dependencies but it failed to install package. I don't understand how it continue.

---

### Post by unoodles on 2008-03-28
First question: Is your ubuntu machine connected to the internet?
If so, all you should have to do it type:
sudo apt-get update
sudo apt-get install network-manager-gnome
and you're done.

If you do not have internet on your ubuntu machine, you will have to go to packages.ubuntu.com and download each package and its dependencies.

---

