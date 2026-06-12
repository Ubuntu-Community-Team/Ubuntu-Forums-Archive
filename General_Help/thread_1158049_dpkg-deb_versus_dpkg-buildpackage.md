---
title: "dpkg-deb versus dpkg-buildpackage"
date: 2009-05-13
forum: General Help
---

### Post by meastwood on 2009-05-13
I'm a bit confused about the above and hoped someone could help me out.

what is the difference between the two - 'dpkg-deb' and 'dpkg-buildpackage'?

Am I right in saying ... 'dpkg-buildpackage' uses debhelper i.e. debian/rules and 'dpkg-deb' does not?

Also where does 'debuild' fit into all of this?

---

### Post by mb_webguy on 2009-05-13
dpkg-buildpackage is a script that helps automate the process of building a package. 

dpkg-deb can create a package from a directory containing Debian control information, but can do other things besides such as display information about a deb package or extract its contents.

I don't have a lot of experience with packaging, but as I understand it you can create a package either by creating the Debian control information and the proper directory structure and then running dpkg-deb, or you can run dpkg-buildpackage and supply the information in the command.

---

### Post by meastwood on 2009-05-14
thanks - so .. is the following correct?
assuming the source build tree has been created

'dpkg-buildpackage' script requires a debian/rules file

'dpkg-deb' does not use debian/rules (dbhelper)

I understand now - needed to play with it a bit - debuild is a wrapper for dpkg-buildpackage, lintian and linda

---

