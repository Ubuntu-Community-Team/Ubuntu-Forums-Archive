---
title: "Problems switching to Kubuntu after package update"
date: 2006-08-13
forum: Desktop Environments
---

### Post by helmut_hed on 2006-08-13
I'd like to use Kmail and Kontact instead of Evolution, so I'm trying to install kubuntu-desktop from Synaptic. Kubuntu-desktop depends (perhaps indirectly) on language-selector-qt, which requires the 0.1.20 version of language-selector.  However, I have already updated to the 0.1.20.1 version of language-selector, which creates a conflict and is preventing me from switching to kubuntu-desktop.

I've tried to update to the 0.1.20.1 version of language-selector-qt, but I can't find it anywhere, and Synaptic tells me that 0.1.20 is the latest.  I also looked at downgrading language-selector back to 0.1.20, but Synaptic wants to remove "ubuntu-desktop" when I do that :)

Any ideas?

Thanks,
Jeff

---

### Post by helmut_hed on 2006-08-13
I managed to get going again with a really gross hack.  I'm sure there's a "right" way to do this.  Anyway, you can do this:

1) get the language-selector-qt .deb file from this web page:

[http://packages.ubuntulinux.org/dapper/admin/language-selector-qt](http://packages.ubuntulinux.org/dapper/admin/language-selector-qt)

2) unpack the .deb into a directory:

mkdir test
dpkg -x language-selector-qt_0.1.20_all.deb test
mkdir test/DEBIAN
dpkg -e language-selector-qt_0.1.20_all.deb test/DEBIAN

3) modify the control file to require the 0.1.20.1 version of language-selector instead:

vi test/DEBIAN/control
and change this line:

Depends: language-selector-common (= 0.1.20), python, python2.4-qt3, adept (>= 1.91)

to this:

Depends: language-selector-common (= 0.1.20.1), python, python2.4-qt3, adept (>= 1.91)

4) rebuild the package

dpkg -b test ~/bogus_pkg.deb

5) install it!

dpkg -i bogus_pkg.deb

This allowed me to successfully switch to kubuntu-desktop.  Unfortunately, it's generated some sort of inconsistency in the package system, and Adept  complains about it, but everything seems to work OK anyway.

If you know what the correct way of handling this is, let me know.

Jeff

---

### Post by iamhugeinjapan on 2006-08-13
ubuntu-desktop package can be safely removed without breaking anything. It's just a package that causes other default ubuntu packages to be installed.

Similarily, if you install kubuntu-desktop or xubuntu-desktop, they too can be removed without badness.

Also, before installing kubuntu-desktop, I recommend configuring a repository for the latest version of KDE (currently 3.5.4). You can find links on  [http://www.kubuntu.org](http://www.kubuntu.org). This will save time updating later and can help with versioning issues.

---

### Post by helmut_hed on 2006-08-20
Update: I managed to find the 0.1.20.1 version of language-selector-qt [here]("https://launchpad.net/distros/ubuntu/dapper/i386/language-selector-qt/0.1.20.1") but it seems very silly to go through such efforts.  I've had several other situations lately where updated versions of some packages are available, but other packages that work with them are not.  In particular I am thinking of development headers for programming, like the KDE headers.  The libs themselves were there, but the development headers were still the old versions.  I worked around this by manually downloading what I needed from the launchpad link.  Does anyone know why they don't appear in the repositories?  Here's my sources.list:
```

deb http://packages.freecontrib.org/plf/ dapper free non-free

deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted


```
Thanks,
Jeff

---

### Post by pikkio on 2006-09-07
Unfortunately, I've got the same problem with the Italian repositories as well. I could solve it manually, but it could be a buggy solution.
Anyway, it should not happen that an update creates such a problem.

Anyone can help?
thanks ;)

---

### Post by pikkio on 2006-09-22
I've temporarily solved this problem by downgrading the language-selector and language-selector-common packages (you can find them on the Ubuntu Package Search website).

I hope all these packages will be fixed soon...

---

### Post by edward2910 on 2006-09-23
This worked for me too. Thanks for posting your solution.
I prefer KDE so much to Gnome :rolleyes:

---

