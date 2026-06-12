---
title: "poor speeds in all package managers"
date: 2009-02-12
forum: General Help
---

### Post by notatoad on 2009-02-12
i've been getting really poor speeds in all package managers.  torrents and http downloads run perfectly fine (i.e. they max out my 6Mbit connection), but whenever i try to download something through a package manager my speeds are below 1kbps.  this problem persists through 4 different physical machines, virtual machines on 2 of those physical machines, aptitude, synaptic, emerge (gentoo), and pacman (arch), 2 different ISPs, countless different mirrors, and using 2 different routers.  esentially the only commonality between all the computers i've experienced this problem on is that they all used the same ethernet cable.

any ideas what could be causing this?

---

### Post by mb_webguy on 2009-02-12
Have you tried changing to a different mirror?

---

### Post by dcstar on 2009-02-12
> **notatoad said:**
> i've been getting really poor speeds in all package managers.  torrents and http downloads run perfectly fine (i.e. they max out my 6Mbit connection), but whenever i try to download something through a package manager my speeds are below 1kbps.  this problem persists through 4 different physical machines, virtual machines on 2 of those physical machines, aptitude, synaptic, emerge (gentoo), and pacman (arch), 2 different ISPs, countless different mirrors, and using 2 different routers.  esentially the only commonality between all the computers i've experienced this problem on is that they all used the same ethernet cable.

any ideas what could be causing this?

Test things by going to [http://packages.ubuntu.com](http://packages.ubuntu.com) and manually downloading a big package using your web browser - you should be able to select a close by mirror to test the HTTP download.

---

