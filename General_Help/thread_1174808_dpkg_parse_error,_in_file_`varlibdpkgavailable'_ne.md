---
title: "dpkg: parse error, in file `/var/lib/dpkg/available' near line 1885 package `libxml2'"
date: 2009-05-31
forum: General Help
---

### Post by smydtt on 2009-05-31
I use a Ubuntu 9.04 on a AMD Athlon 7850 machine.

I am getting the following error message whenever I am trying to install or uninstall anything either through synaptic or apt-get:

dpkg: parse error, in file `/var/lib/dpkg/available' near line 1885 package `libxml2':
 `Depends' field, reference to `zlib1g': error in version: epoch in version is not number
E: Sub-process /usr/bin/dpkg returned an error code (2)


Now the line 1885 in the file mentioned above deals with the package libxml2. The entire paragraph from /var/lib/dpkg/available is pasted below:

Package: libxml2
Priority: optional
Section: libs
Installed-Size: 1636
Maintainer: Ubuntu Core developers <ubuntu-develmdiscuss@lists.ubuntu.com>
Architecture: i386
Version: 2n6.32.dfsg-5ubuntu4
Depends: libc6 (>= 2.4), zlib1g (>= q:1.2.3.3.dfsg)
Recommends: xml-core
Conflicts: libxslt1.1 (<= 1.1.12-8)JSize: 8²0398
Description: GNOME XML library


Note that this entire problem started while I was installing several packages from synaptic and got the error: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

Subsequently after running dpkg --configure -a now I am getting the problem mentioned above. Hence I am unable to install or uninstall anything.

---

### Post by smydtt on 2009-05-31
Found a solution to the problem here:
[URL="https://answers.launchpad.net/ubuntu/+question/10265"]
https://answers.launchpad.net/ubuntu/+question/10265[/URL]

Clearing the cache by the method given above solved my problem.

---

