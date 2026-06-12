---
title: "GNU GRUB issue"
date: 2011-04-06
forum: Desktop Environments
---

### Post by jeshrel on 2011-04-06
Hi

I have dual booted Windows 7 and Ubuntu 10.10, as soon i would start my computer in the grub i get even the older version of ubuntu kernel 10.10 along with windows 7, i have attached a picture of my GNU GRUB, what should i do to only get the latest version of ubuntu kernel 10.10 in my grub and stop the previous versions from being shown on screen.

---

### Post by Krytarik on 2011-04-06
First, you should always retain at least the two most recent kernels! See this guide about how to remove the old kernel packages:
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

And you should definitely not only remove the kernel's image package,  but also it's header packages, like described, since it frees up a lot  of disk space! I recommend using Ubuntu Tweak for all that.

The guide describes the way to download the deb-package and install it manually.

But, actually, the better way is to add their PPA and install it through a package manager:
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```You will find Ubuntu Tweak in "Applications -> System Tools" after the installation.

Greetings.

---

