---
title: "Prevu fails"
date: 2009-06-25
forum: General Help
---

### Post by iain.dalton on 2009-06-25
I'm trying to install gnumeric 1.9.9 from Ubuntu 9.10 on my 9.04 installation using [Prevu]("https://wiki.ubuntu.com/Prevu"). Running "prevu gnumeric/karmic" fails like this:

```
dpkg-source: extracting gnumeric in gnumeric-1.9.9
dpkg-source: info: unpacking gnumeric_1.9.9.orig.tar.gz
dpkg-source: info: applying gnumeric_1.9.9-1ubuntu1.diff.gz
W: /home/iain/.pbuilderrc does not exist
Building the build Environment
 -> extracting base tarball [/var/cache/prevu/jaunty.tgz]
 -> creating local configuration
 -> copying local configuration
 -> mounting /proc filesystem
 -> mounting /dev/pts filesystem
-> Mounting /var/cache/prevu/jaunty-debs
-> Mounting /var/cache/prevu/src/19916
 -> policy-rc.d already exists
Obtaining the cached apt archive contents
Reading package lists...
Building dependency tree...
Reading state information...
passwd is already the newest version.
The following extra packages will be installed:
  debootstrap wget
Suggested packages:
  pbuilder-uml cowdancer gdebi
Recommended packages:
  fakeroot sudo devscripts
The following NEW packages will be installed:
  debootstrap pbuilder wget
debconf: delaying package configuration, since apt-utils is not installed
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/622kB of archives.
After this operation, 3383kB of additional disk space will be used.
Selecting previously deselected package wget.

(Reading database ... 10502 files and directories currently installed.)

Unpacking wget (from .../wget_1.11.4-2ubuntu1_i386.deb) ...

Selecting previously deselected package debootstrap.

Unpacking debootstrap (from .../debootstrap_1.0.13~jaunty1_all.deb) ...

Selecting previously deselected package pbuilder.

Unpacking pbuilder (from .../pbuilder_0.183ubuntu1_all.deb) ...

Setting up wget (1.11.4-2ubuntu1) ...



Setting up debootstrap (1.0.13~jaunty1) ...

Setting up pbuilder (0.183ubuntu1) ...



Setting DEBBUILDOPTS=
 -> Attempting to satisfy build-dependencies
 -> Creating pbuilder-satisfydepends-dummy package
Package: pbuilder-satisfydepends-dummy
Version: 0.invalid.0
Architecture: i386
Maintainer: Debian Pbuilder Team <pbuilder-maint@lists.alioth.debian.org>
Description: Dummy package to satisfy dependencies with aptitude - created by pbuilder
 This package was created automatically by pbuilder and should
Depends: debhelper (>= 7.0.0), python-central (>= 0.5), dh-buildinfo, po-debconf, gettext, bison, flex, rarian-compat | scrollkeeper, intltool (>= 0.29), libxml-parser-perl, zlib1g-dev, libglib2.0-dev (>= 2.12.0), libgsf-1-dev (>= 1.14.15), libgoffice-0-8-dev (>= 0.7.8), libxml2-dev (>= 2.6.10-2), libpango1.0-dev (>= 1.12.0), libgtk2.0-dev (>= 2.12.0), libglade2-dev (>= 1:2.4.0), libart-2.0-dev (>= 2.3.16-5), pxlib-dev (>= 0.5.1-2+b1), libperl-dev, python-dev, python-gtk2-dev
dpkg-deb: building package `pbuilder-satisfydepends-dummy' in `/tmp/satisfydepends-aptitude/pbuilder-satisfydepends-dummy.deb'.
Reading package lists...
Building dependency tree...
Reading state information...
aptitude is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Selecting previously deselected package pbuilder-satisfydepends-dummy.
(Reading database ... 10642 files and directories currently installed.)
Unpacking pbuilder-satisfydepends-dummy (from .../pbuilder-satisfydepends-dummy.deb) ...
dpkg: dependency problems prevent configuration of pbuilder-satisfydepends-dummy:
 pbuilder-satisfydepends-dummy depends on debhelper (>= 7.0.0); however:
  Package debhelper is not installed.
 pbuilder-satisfydepends-dummy depends on python-central (>= 0.5); however:
  Package python-central is not installed.
 pbuilder-satisfydepends-dummy depends on dh-buildinfo; however:
  Package dh-buildinfo is not installed.
 pbuilder-satisfydepends-dummy depends on po-debconf; however:
  Package po-debconf is not installed.
 pbuilder-satisfydepends-dummy depends on gettext; however:
  Package gettext is not installed.
 pbuilder-satisfydepends-dummy depends on bison; however:
  Package bison is not installed.
 pbuilder-satisfydepends-dummy depends on flex; however:
  Package flex is not installed.
 pbuilder-satisfydepends-dummy depends on rarian-compat | scrollkeeper; however:
  Package rarian-compat is not installed.
  Package scrollkeeper is not installed.
 pbuilder-satisfydepends-dummy depends on intltool (>= 0.29); however:
  Package intltool is not installed.
 pbuilder-satisfydepends-dummy depends on libxml-parser-perl; however:
  Package libxml-parser-perl is not installed.
 pbuilder-satisfydepends-dummy depends on zlib1g-dev; however:
  Package zlib1g-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libglib2.0-dev (>= 2.12.0); however:
  Package libglib2.0-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libgsf-1-dev (>= 1.14.15); however:
  Package libgsf-1-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libgoffice-0-8-dev (>= 0.7.8); however:
  Package libgoffice-0-8-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libxml2-dev (>= 2.6.10-2); however:
  Package libxml2-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libpango1.0-dev (>= 1.12.0); however:
  Package libpango1.0-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libgtk2.0-dev (>= 2.12.0); however:
  Package libgtk2.0-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libglade2-dev (>= 1:2.4.0); however:
  Package libglade2-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libart-2.0-dev (>= 2.3.16-5); however:
  Package libart-2.0-dev is not installed.
 pbuilder-satisfydepends-dummy depends on pxlib-dev (>= 0.5.1-2+b1); however:
  Package pxlib-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libperl-dev; however:
  Package libperl-dev is not installed.
 pbuilder-satisfydepends-dummy depends on python-dev; however:
  Package python-dev is not installed.
 pbuilder-satisfydepends-dummy depends on python-gtk2-dev; however:
  Package python-gtk2-dev is not installed.
dpkg: error processing pbuilder-satisfydepends-dummy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pbuilder-satisfydepends-dummy
Reading package lists...
Building dependency tree...
Reading state information...
Initializing package states...
Writing extended state information...
The following packages are BROKEN:
  pbuilder-satisfydepends-dummy 
The following NEW packages will be installed:
  autoconf{a} automake{a} autotools-dev{a} bison{a} bsdmainutils{a} 
  debhelper{a} defoma{a} dh-buildinfo{a} docbook-xml{a} file{a} flex{a} 
  fontconfig{a} fontconfig-config{a} gettext{a} gettext-base{a} 
  groff-base{a} html2text{a} intltool{a} intltool-debian{a} libart-2.0-2{a} 
  libart-2.0-dev{a} libatk1.0-0{a} libatk1.0-dev{a} libbz2-dev{a} 
  libcairo2{a} libcairo2-dev{a} libcroco3{a} libcups2{a} libdatrie0{a} 
  libdirectfb-1.0-0{a} libdirectfb-dev{a} libdirectfb-extra{a} libexpat1{a} 
  libexpat1-dev{a} libffi-dev{a} libffi5{a} libfontconfig1{a} 
  libfontconfig1-dev{a} libfreetype6{a} libfreetype6-dev{a} libglade2-0{a} 
  libglade2-dev{a} libglib2.0-0{a} libglib2.0-dev{a} libgsf-1-114{a} 
  libgsf-1-common{a} libgsf-1-dev{a} libgtk2.0-0{a} libgtk2.0-common{a} 
  libgtk2.0-dev{a} libhtml-parser-perl{a} libhtml-tagset-perl{a} 
  libhtml-tree-perl{a} libice-dev{a} libice6{a} libjasper1{a} libjpeg62{a} 
  libjpeg62-dev{a} libmagic1{a} libnewt0.52{a} libpango1.0-0{a} 
  libpango1.0-common{a} libpango1.0-dev{a} libperl-dev{a} libperl5.10{a} 
  libpixman-1-0{a} libpixman-1-dev{a} libpng12-0{a} libpng12-dev{a} 
  libpopt0{a} libpthread-stubs0{a} libpthread-stubs0-dev{a} libpython2.6{a} 
  librarian0{a} libsm-dev{a} libsm6{a} libsqlite3-0{a} libsysfs-dev{a} 
  libsysfs2{a} libthai-data{a} libthai0{a} libtiff4{a} libts-0.0-0{a} 
  liburi-perl{a} libwww-perl{a} libx11-6{a} libx11-data{a} libx11-dev{a} 
  libxau-dev{a} libxau6{a} libxcb-render-util0{a} 
  libxcb-render-util0-dev{a} libxcb-render0{a} libxcb-render0-dev{a} 
  libxcb1{a} libxcb1-dev{a} libxcomposite-dev{a} libxcomposite1{a} 
  libxcursor-dev{a} libxcursor1{a} libxdamage-dev{a} libxdamage1{a} 
  libxdmcp-dev{a} libxdmcp6{a} libxext-dev{a} libxext6{a} libxfixes-dev{a} 
  libxfixes3{a} libxft-dev{a} libxft2{a} libxi-dev{a} libxi6{a} 
  libxinerama-dev{a} libxinerama1{a} libxml-parser-perl{a} libxml2{a} 
  libxml2-dev{a} libxml2-utils{a} libxrandr-dev{a} libxrandr2{a} 
  libxrender-dev{a} libxrender1{a} m4{a} man-db{a} mime-support{a} 
  pkg-config{a} po-debconf{a} pxlib-dev{a} pxlib1{a} python{a} 
  python-cairo{a} python-central{a} python-dev{a} python-gobject{a} 
  python-gobject-dev{a} python-gtk2{a} python-gtk2-dev{a} python-support{a} 
  python2.6{a} python2.6-dev{a} rarian-compat{a} sgml-base{a} sgml-data{a} 
  shared-mime-info{a} ttf-dejavu{a} ttf-dejavu-core{a} ttf-dejavu-extra{a} 
  ucf{a} whiptail{a} x11-common{a} x11proto-composite-dev{a} 
  x11proto-core-dev{a} x11proto-damage-dev{a} x11proto-fixes-dev{a} 
  x11proto-input-dev{a} x11proto-kb-dev{a} x11proto-randr-dev{a} 
  x11proto-render-dev{a} x11proto-xext-dev{a} x11proto-xinerama-dev{a} 
  xml-core{a} xtrans-dev{a} zlib1g-dev{a} 
0 packages upgraded, 163 newly installed, 0 to remove and 0 not upgraded.
Need to get 45.3MB/49.0MB of archives. After unpacking 178MB will be used.
The following packages have unmet dependencies:
  pbuilder-satisfydepends-dummy: Depends: libgsf-1-dev (>= 1.14.15) but 1.14.11-2ubuntu1 is to be installed.
                                 Depends: libgoffice-0-8-dev (>= 0.7.8) which is a virtual package.
The following actions will resolve these dependencies:

Remove the following packages:
pbuilder-satisfydepends-dummy

Score is -9850

Writing extended state information...
debconf: delaying package configuration, since apt-utils is not installed
(Reading database ... 10642 files and directories currently installed.)

Removing pbuilder-satisfydepends-dummy ...

Selecting previously deselected package libmagic1.

(Reading database ... 10642 files and directories currently installed.)

Unpacking libmagic1 (from .../libmagic1_4.26-2ubuntu4_i386.deb) ...

Selecting previously deselected package file.

Unpacking file (from .../file_4.26-2ubuntu4_i386.deb) ...

Selecting previously deselected package libsqlite3-0.

Unpacking libsqlite3-0 (from .../libsqlite3-0_3.6.10-1ubuntu0.2_i386.deb) ...

Selecting previously deselected package mime-support.

Unpacking mime-support (from .../mime-support_3.44-1_all.deb) ...

Selecting previously deselected package python2.6.

Unpacking python2.6 (from .../python2.6_2.6.2-0ubuntu1_i386.deb) ...

Selecting previously deselected package python.

Unpacking python (from .../python_2.6.2-0ubuntu1_all.deb) ...

Selecting previously deselected package bsdmainutils.

Unpacking bsdmainutils (from .../bsdmainutils_6.1.10ubuntu3_i386.deb) ...

Selecting previously deselected package libpng12-0.

Unpacking libpng12-0 (from .../libpng12-0_1.2.27-2ubuntu2_i386.deb) ...

Setting up libmagic1 (4.26-2ubuntu4) ...



Setting up file (4.26-2ubuntu4) ...

Setting up libsqlite3-0 (3.6.10-1ubuntu0.2) ...



Setting up mime-support (3.44-1) ...



Setting up python2.6 (2.6.2-0ubuntu1) ...



Setting up python (2.6.2-0ubuntu1) ...



Setting up bsdmainutils (6.1.10ubuntu3) ...



Setting up libpng12-0 (1.2.27-2ubuntu2) ...



Processing triggers for libc6 ...

ldconfig deferred processing now taking place

Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Writing extended state information...
Aptitude couldn't satisfy the build dependencies
Copying back the cached apt archive contents
 -> unmounting /var/cache/prevu/src/19916 filesystem
 -> unmounting /var/cache/prevu/jaunty-debs filesystem
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> cleaning the build env 
    -> removing directory /var/cache/prevu/builds/20265 and its subdirectories
========================
Prevu Error: Build failed.
Prevu encountered an error performing your build. The actual
error message may be further up in the scrollback before pbuilder
exited. Please look for a failed dependency or compile error in
the full output.
```

How can I fix this?

---

