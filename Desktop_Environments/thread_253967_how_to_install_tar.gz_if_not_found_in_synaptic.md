---
title: "how to install tar.gz if not found in synaptic"
date: 2006-09-09
forum: Desktop Environments
---

### Post by bscook on 2006-09-09
i amt trying to install a program called mrouted on my ubuntu desktop system.  i tried enabling multiverse etc in synaptic, but it couldn't  find it.  i have found it as manually iinstalled program on a couple of places:
[http://dsn-tud.tucows.com/debian/pool/non-free/m/mrouted/]("http://dsn-tud.tucows.com/debian/pool/non-free/m/mrouted/")
[http://pt.archive.ubuntu.com/ubuntu/pool/multiverse/m/mrouted/]("http://pt.archive.ubuntu.com/ubuntu/pool/multiverse/m/mrouted/")
but still can't get it installed.
i tried following the directions on 
[HOW TO INSTALL ANYTHING ON UBUNTU]("http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually")
and also tried step by step directions at
[http://jukie.net/~bart/multicast/Linux-Mrouted-MiniHOWTO.html]("http://jukie.net/~bart/multicast/Linux-Mrouted-MiniHOWTO.html")
but i can't get past the initial MAKE stages.  any help would be greatly appreciated.

-bradley

---

### Post by elettronicha on 2006-09-09
Have you installed the package "build-essential", containing the necessary stuff to compile?

EDIT: the 1st link points to a debian repository, the 3rd element is a binary package .deb and the 4th a source. Probably you can directly install the .deb package with dpkg.

---

### Post by moore.bryan on 2006-09-09
*the tucows site has a deb file ([http://dsn-tud.tucows.com/debian/pool/non-free/m/mrouted/mrouted_3.9-beta3-1.1_i386.deb)](http://dsn-tud.tucows.com/debian/pool/non-free/m/mrouted/mrouted_3.9-beta3-1.1_i386.deb)).  download that to your home folder, then ```
sudo dpkg -i mrouted_3.9-beta3-1.1_i386.deb
``` if that doesn't work, post any error messages for us.*

---

