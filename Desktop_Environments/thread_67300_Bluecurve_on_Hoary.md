---
title: "Bluecurve on Hoary"
date: 2005-09-19
forum: Desktop Environments
---

### Post by Indigo2 on 2005-09-19
I ran into this problem installing the Redhat Artwork 0.128.  Has anyone attempted to install this?

yourname@yourmachine: alien -i redhat-artwork*
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
xargs -0 -r -i cp -a {} debian/redhat-artwork
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dpkg-gencontrol: error: current build architecture i386 does not appear in package's list (amd64)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: redhat-artwork-0.128: No such file or directory

---

### Post by Xian on 2005-09-19
Have you read into this thread: [Bluecurve on Ubuntu](http://ubuntuforums.org/showthread.php?t=2696&highlight=bluecurve)?

---

### Post by Indigo2 on 2005-09-19
[QUOTE=Xian]Have you read into this thread: [Bluecurve on Ubuntu](http://ubuntuforums.org/showthread.php?t=2696&highlight=bluecurve)?[/QUOTE]

Ohhhhh.......ok Thank you very much for your help.

---

