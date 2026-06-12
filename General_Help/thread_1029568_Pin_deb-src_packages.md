---
title: "Pin deb-src packages"
date: 2009-01-03
forum: General Help
---

### Post by ibuclaw on 2009-01-03
Hi

I was wondering if there is some way to pin the deb-src' packages.

This is what my preferences file looks like:
```

Package: *
Pin: release a=hardy-backports
Pin-Priority: 10

Package: gufw
Pin: release a=hardy-backports
Pin-Priority: 800

Package: *
Pin: release a=hardy-security
Pin-Priority: 800

```

And, obviously, it works when pulling binaries from the repository:
```

sudo apt-get -s install pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libhesiod0 libmeanwhile1 libpurple0 libzephyr3 pidgin-data
Suggested packages:
  tk8.4
Recommended packages:
  libpurple-bin
The following NEW packages will be installed
  libhesiod0 libmeanwhile1 libpurple0 libzephyr3 pidgin pidgin-data
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Inst libmeanwhile1 (1.0.2-3 Ubuntu:8.04/**hardy**)
Inst libhesiod0 (3.0.2-18.1 Ubuntu:8.04/**hardy**)
Inst libzephyr3 (2.1.20070719.SNAPSHOT-1 Ubuntu:8.04/**hardy**)
Inst pidgin-data (1:2.4.1-1ubuntu2.2 Ubuntu:8.04/**hardy-security**)
Inst libpurple0 (1:2.4.1-1ubuntu2.2 Ubuntu:8.04/**hardy-security**)
Inst pidgin (1:2.4.1-1ubuntu2.2 Ubuntu:8.04/**hardy-security**)
Conf libmeanwhile1 (1.0.2-3 Ubuntu:8.04/**hardy**)
Conf libhesiod0 (3.0.2-18.1 Ubuntu:8.04/**hardy**)
Conf libzephyr3 (2.1.20070719.SNAPSHOT-1 Ubuntu:8.04/**hardy**)
Conf pidgin-data (1:2.4.1-1ubuntu2.2 Ubuntu:8.04/**hardy-security**)
Conf libpurple0 (1:2.4.1-1ubuntu2.2 Ubuntu:8.04/**hardy-security**)
Conf pidgin (1:2.4.1-1ubuntu2.2 Ubuntu:8.04/**hardy-security**)

```
(NOTE, I this is a dry-run install, it is just simulating what it does, but I can confirm that it downloads these packages in the real installation also).

But when I pull the sourcecode from the repository, it instead gets the newest release.
```

sudo apt-get source pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
NOTICE: 'pidgin' packaging is maintained in the 'Svn' version control system at:
svn://svn.debian.org/svn/collab-maint/deb-maint/pidgin/
Need to get 11.7MB of source archives.
Get: 1 http://gb.archive.ubuntu.com **hardy-backports**/main pidgin 1:2.5.2-0ubuntu1~hardy1 (dsc) [1364B]
Get: 2 http://gb.archive.ubuntu.com **hardy-backports**/main pidgin 1:2.5.2-0ubuntu1~hardy1 (tar) [11.6MB]
Get: 3 http://gb.archive.ubuntu.com **hardy-backports**/main pidgin 1:2.5.2-0ubuntu1~hardy1 (diff) [57.5kB]                                                     
Fetched 11.7MB in 12s (907kB/s)                                                                                                                             
dpkg-source: warning: extracting unsigned source package (./pidgin_2.5.2-0ubuntu1~hardy1.dsc)
dpkg-source: extracting pidgin in pidgin-2.5.2
dpkg-source: unpacking pidgin_2.5.2.orig.tar.gz
dpkg-source: applying ./pidgin_2.5.2-0ubuntu1~hardy1.diff.gz

```

Any ideas how to setup the preferences file for sources to enforce the same criteria I currently have on the binaries ?

Regards
Iain

---

