---
title: "Please read if you use Seveas repository: DON'T update libwxgtk2.6-0"
date: 2006-08-27
forum: Desktop Environments
---

### Post by hexion on 2006-08-27
Some weeks ago I had continuos system hungs.
I first thought it was a kernel problem, and still think it because the fact is that kernel hungs with this, but at the end I found the issue.

It's seveas' repository version of package "libwxgtk2.6-0"

If you have this repository set,
> deb [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) dapper-seveas all
do NOT upgrade to its "libwxgtk2.6-0" version.

When "umounting user filesystems" at shutdown, or while accesing to a vfat partition in a SATA drive, system may hung.

Version affected is:
>      2.6.3.2.1.1ubuntu2~dapper1 0
        500 [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) dapper-seveas/all Packages


With this version (ubuntu official) there's no problem at all:
>      2.6.1.2ubuntu2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages


Seveas' version won't install with "sudo aptitude upgrade", but with "sudo aptitude dist-upgrade".


**P.D.: It's possible this bug don't affect if you don't have a SATA drive, but I recommend don't upgrading anyway**

---

### Post by simonn on 2006-08-27
This is why 3rd party repositories (3PRs) which provide packages of software which already exists, even if it is a newer version, in the distro's repository are bad.

Their prevalence of 3PRs in the Red Hat world is what causes "rpm hell", not the rpm package manager itself (which does exactly the same thing as dpkg i.e. manages files, just in a different way).

Moving to ubuntu where 99.9% of what most people need is in the distro's repositories was a breath of fresh air after spending a few years in the Red Hat world.

---

