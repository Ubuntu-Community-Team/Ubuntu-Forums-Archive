---
title: "pbuilder can't find dependency"
date: 2009-03-15
forum: General Help
---

### Post by cb951303 on 2009-03-15
I'm trying to build monodevelop 1.9.2 for intrepid from jaunty sources.
I'm using this as a guide: [https://wiki.ubuntu.com/PbuilderHowto](https://wiki.ubuntu.com/PbuilderHowto)

after trying to build I get this error
```

nxn@nxn-desktop:~/Desktop/monodevelop$ sudo pbuilder build *.dsc
W: /home/nxn/.pbuilderrc does not exist
I: using fakeroot in build.
Current time: Sun Mar 15 20:54:53 EET 2009
pbuilder-time-stamp: 1237143293
Building the build Environment
 -> extracting base tarball [/var/cache/pbuilder/base.tgz]
 -> creating local configuration
 -> copying local configuration
 -> mounting /proc filesystem
 -> mounting /dev/pts filesystem
 -> policy-rc.d already exists
Obtaining the cached apt archive contents
Installing the build-deps
 -> Attempting to satisfy build-dependencies
 -> Creating pbuilder-satisfydepends-dummy package
Package: pbuilder-satisfydepends-dummy
Version: 0.invalid.0
Architecture: i386
Maintainer: Debian Pbuilder Team <pbuilder-maint@lists.alioth.debian.org>
Description: Dummy package to satisfy dependencies with aptitude - created by pbuilder
 This package was created automatically by pbuilder and should
Depends: debhelper (>= 7), dpatch, cli-common-dev (>= 0.5.7), mono-devel (>= 2.0), libmono-dev (>= 1.1.10), monodoc-base (>= 1.1.9), intltool, autoconf, automake, autotools-dev, gtk-sharp2-gapi (>= 2.8), libgtk2.0-cil (>= 2.8), libglade2.0-cil (>= 2.8), libgnome2.24-cil (>= 2.24), libgconf2.24-cil (>= 2.24), libgtksourceview2.0-cil (>= 0.10), libnunit2.4-cil, libmono-cairo2.0-cil (>= 1.2), libmono-cairo1.0-cil, libmono-winforms2.0-cil, libmono-system-runtime2.0-cil, libmono-cecil0.5-cil, libmono-addins0.2-cil (>= 0.3), libmono-addins-gui0.2-cil (>= 0.3), libmetacity-dev, libsvn-dev, libapr1-dev, libgtkspell-dev, mono-xsp-base, mono-xsp2-base, desktop-file-utils
dpkg-deb: building package `pbuilder-satisfydepends-dummy' in `/tmp/satisfydepends-aptitude/pbuilder-satisfydepends-dummy.deb'.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
aptitude is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Selecting previously deselected package pbuilder-satisfydepends-dummy.
(Reading database ... 10496 files and directories currently installed.)
Unpacking pbuilder-satisfydepends-dummy (from .../pbuilder-satisfydepends-dummy.deb) ...
dpkg: dependency problems prevent configuration of pbuilder-satisfydepends-dummy:
 pbuilder-satisfydepends-dummy depends on debhelper (>= 7); however:
  Package debhelper is not installed.
 pbuilder-satisfydepends-dummy depends on dpatch; however:
  Package dpatch is not installed.
 pbuilder-satisfydepends-dummy depends on cli-common-dev (>= 0.5.7); however:
  Package cli-common-dev is not installed.
 pbuilder-satisfydepends-dummy depends on mono-devel (>= 2.0); however:
  Package mono-devel is not installed.
 pbuilder-satisfydepends-dummy depends on libmono-dev (>= 1.1.10); however:
  Package libmono-dev is not installed.
 pbuilder-satisfydepends-dummy depends on monodoc-base (>= 1.1.9); however:
  Package monodoc-base is not installed.
 pbuilder-satisfydepends-dummy depends on intltool; however:
  Package intltool is not installed.
 pbuilder-satisfydepends-dummy depends on autoconf; however:
  Package autoconf is not installed.
 pbuilder-satisfydepends-dummy depends on automake; however:
  Package automake is not installed.
 pbuilder-satisfydepends-dummy depends on autotools-dev; however:
  Package autotools-dev is not installed.
 pbuilder-satisfydepends-dummy depends on gtk-sharp2-gapi (>= 2.8); however:
  Package gtk-sharp2-gapi is not installed.
 pbuilder-satisfydepends-dummy depends on libgtk2.0-cil (>= 2.8); however:
  Package libgtk2.0-cil is not installed.
 pbuilder-satisfydepends-dummy depends on libglade2.0-cil (>= 2.8); however:
  Package libglade2.0-cil is not installed.
 pbuilder-satisfydepends-dummy depends on libgnome2.24-cil (>= 2.24); however:
  Package libgnome2.24-cil is not installed.
 pbuilder-satisfydepends-dummy depends on libgconf2.24-cil (>= 2.24); however:
  Package libgconf2.24-cil is not installed.
 pbuilder-satisfydepends-dummy depends on libgtksourceview2.0-cil (>= 0.10); however:
  Package libgtksourceview2.0-cil is not installed.
 pbuilder-satisfydepends-dummy depends on libnunit2.4-cil; however:
  Package libnunit2.4-cil is not installed.
 pbuilder-satisfydepends-dummy depends on libmono-cairo2.0-cil (>= 1.2); however:
  Package libmono-cairo2.0-cil is not installed.
 pbuilder-satisfydepends-dummy depends on libmono-cairo1.0-cil; however:
  Package libmono-cairo1.0-cil is not installed.
 pbuilder-satisfydepends-dummy depends on libmono-winforms2.0-cil; however:
  Package libmono-winforms2.0-cil is not installed.
 pbuilder-satisfydepends-dummy depends on libmono-system-runtime2.0-cil; however:
  Package libmono-system-runtime2.0-cil is not installed.
 pbuilder-satisfydepends-dummy depends on libmono-cecil0.5-cil; however:
  Package libmono-cecil0.5-cil is not installed.
 pbuilder-satisfydepends-dummy depends on libmono-addins0.2-cil (>= 0.3); however:
  Package libmono-addins0.2-cil is not installed.
 pbuilder-satisfydepends-dummy depends on libmono-addins-gui0.2-cil (>= 0.3); however:
  Package libmono-addins-gui0.2-cil is not installed.
 pbuilder-satisfydepends-dummy depends on libmetacity-dev; however:
  Package libmetacity-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libsvn-dev; however:
  Package libsvn-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libapr1-dev; however:
  Package libapr1-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libgtkspell-dev; however:
  Package libgtkspell-dev is not installed.
 pbuilder-satisfydepends-dummy depends on mono-xsp-base; however:
  Package mono-xsp-base is not installed.
 pbuilder-satisfydepends-dummy depends on mono-xsp2-base; however:
  Package mono-xsp2-base is not installed.
 pbuilder-satisfydepends-dummy depends on desktop-file-utils; however:
  Package desktop-file-utils is not installed.
dpkg: error processing pbuilder-satisfydepends-dummy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pbuilder-satisfydepends-dummy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  pbuilder-satisfydepends-dummy 
The following NEW packages will be installed:
  adduser{a} autoconf{a} automake{a} autotools-dev{a} bsdmainutils{a} cli-common{a} cli-common-dev{a} comerr-dev{a} consolekit{a} dbus{a} debhelper{a} defoma{a} desktop-file-utils{a} dpatch{a} 
  esound-common{a} file{a} fontconfig{a} fontconfig-config{a} gamin{a} gconf2{a} gconf2-common{a} gettext{a} gettext-base{a} gnome-mime-data{a} groff-base{a} gtk-sharp2-gapi{a} html2text{a} intltool{a} 
  intltool-debian{a} libapr1{a} libapr1-dev{a} libaprutil1{a} libaprutil1-dev{a} libart-2.0-2{a} libart2.24-cil{a} libasound2{a} libaspell15{a} libatk1.0-0{a} libatk1.0-dev{a} libaudiofile0{a} 
  libavahi-client3{a} libavahi-common-data{a} libavahi-common3{a} libavahi-glib1{a} libbonobo2-0{a} libbonobo2-common{a} libbonoboui2-0{a} libbonoboui2-common{a} libcairo2{a} libcairo2-dev{a} 
  libck-connector0{a} libcroco3{a} libcups2{a} libdatrie0{a} libdb4.6-dev{a} libdbus-1-3{a} libdbus-glib-1-2{a} libdirectfb-1.0-0{a} libdirectfb-dev{a} libdirectfb-extra{a} libenchant-dev{a} libenchant1c2a{a} 
  libesd-alsa0{a} libexif12{a} libexpat1{a} libexpat1-dev{a} libfontconfig1{a} libfontconfig1-dev{a} libfreetype6{a} libfreetype6-dev{a} libgail-common{a} libgail18{a} libgamin0{a} libgconf2-4{a} 
  libgconf2.24-cil{a} libgdiplus{a} libgif4{a} libglade2-0{a} libglade2.0-cil{a} libglib2.0-0{a} libglib2.0-cil{a} libglib2.0-dev{a} libgnome-keyring0{a} libgnome-vfs2.24-cil{a} libgnome2-0{a} 
  libgnome2-common{a} libgnome2.24-cil{a} libgnomecanvas2-0{a} libgnomecanvas2-common{a} libgnomeui-0{a} libgnomeui-common{a} libgnomevfs2-0{a} libgnomevfs2-common{a} libgtk2.0-0{a} libgtk2.0-cil{a} 
  libgtk2.0-common{a} libgtk2.0-dev{a} libgtkspell-dev{a} libgtkspell0{a} libhal-storage1{a} libhal1{a} libhtml-parser-perl{a} libhtml-tagset-perl{a} libhtml-tree-perl{a} libhunspell-1.2-0{a} libice-dev{a} 
  libice6{a} libidl0{a} libjasper1{a} libjpeg62{a} libjpeg62-dev{a} libkadm55{a} libkrb5-dev{a} libldap2-dev{a} libmagic1{a} libmetacity-dev{a} libmetacity0{a} libmono-accessibility2.0-cil{a} 
  libmono-addins-gui0.2-cil{a} libmono-addins0.2-cil{a} libmono-cairo2.0-cil{a} libmono-corlib1.0-cil{a} libmono-corlib2.0-cil{a} libmono-data-tds1.0-cil{a} libmono-data-tds2.0-cil{a} libmono-data1.0-cil{a} 
  libmono-data2.0-cil{a} libmono-dev{a} libmono-getoptions1.0-cil{a} libmono-getoptions2.0-cil{a} libmono-peapi2.0-cil{a} libmono-posix1.0-cil{a} libmono-posix2.0-cil{a} libmono-relaxng1.0-cil{a} 
  libmono-security1.0-cil{a} libmono-security2.0-cil{a} libmono-sharpzip0.84-cil{a} libmono-sharpzip2.84-cil{a} libmono-sqlite2.0-cil{a} libmono-system-data1.0-cil{a} libmono-system-data2.0-cil{a} 
  libmono-system-runtime1.0-cil{a} libmono-system-runtime2.0-cil{a} libmono-system-web1.0-cil{a} libmono-system-web2.0-cil{a} libmono-system1.0-cil{a} libmono-system2.0-cil{a} libmono-webbrowser0.5-cil{a} 
  libmono-winforms2.0-cil{a} libmono0{a} libmono1.0-cil{a} libmono2.0-cil{a} libmysqlclient15-dev{a} libmysqlclient15off{a} libneon27-gnutls{a} libnewt0.52{a} libnunit2.4-cil{a} liborbit2{a} libpango1.0-0{a} 
  libpango1.0-common{a} libpango1.0-dev{a} libpcre3-dev{a} libpcrecpp0{a} libpixman-1-0{a} libpixman-1-dev{a} libpng12-0{a} libpng12-dev{a} libpolkit-dbus2{a} libpolkit2{a} libpopt0{a} libpq-dev{a} libpq5{a} 
  libpthread-stubs0{a} libpthread-stubs0-dev{a} libsm-dev{a} libsm6{a} libsmbios2{a} libsqlite0{a} libsqlite3-0{a} libsqlite3-dev{a} libssl-dev{a} libsvn-dev{a} libsvn1{a} libsysfs-dev{a} libsysfs2{a} 
  libthai-data{a} libthai0{a} libtiff4{a} libts-0.0-0{a} liburi-perl{a} libwww-perl{a} libx11-6{a} libx11-data{a} libx11-dev{a} libxau-dev{a} libxau6{a} libxcb-render-util0{a} libxcb-render-util0-dev{a} 
  libxcb-render0{a} libxcb-render0-dev{a} libxcb1{a} libxcb1-dev{a} libxcomposite-dev{a} libxcomposite1{a} libxcursor-dev{a} libxcursor1{a} libxdamage-dev{a} libxdamage1{a} libxdmcp-dev{a} libxdmcp6{a} 
  libxext-dev{a} libxext6{a} libxfixes-dev{a} libxfixes3{a} libxft-dev{a} libxft2{a} libxi-dev{a} libxi6{a} libxinerama-dev{a} libxinerama1{a} libxml-dom-perl{a} libxml-libxml-common-perl{a} 
  libxml-libxml-perl{a} libxml-namespacesupport-perl{a} libxml-parser-perl{a} libxml-perl{a} libxml-regexp-perl{a} libxml-sax-perl{a} libxml2{a} libxml2-utils{a} libxrandr-dev{a} libxrandr2{a} 
  libxrender-dev{a} libxrender1{a} lynx{a} lynx-cur{a} m4{a} man-db{a} metacity-common{a} mime-support{a} mono-2.0-devel{a} mono-2.0-gac{a} mono-2.0-runtime{a} mono-common{a} mono-devel{a} mono-gac{a} 
  mono-gmcs{a} mono-jit{a} mono-runtime{a} mono-utils{a} monodoc-base{a} mysql-common{a} pkg-config{a} po-debconf{a} psmisc{a} python{a} python2.6{a} sgml-base{a} shared-mime-info{a} ttf-dejavu{a} 
  ttf-dejavu-core{a} ttf-dejavu-extra{a} ucf{a} uuid-dev{a} whiptail{a} x11-common{a} x11proto-composite-dev{a} x11proto-core-dev{a} x11proto-damage-dev{a} x11proto-fixes-dev{a} x11proto-input-dev{a} 
  x11proto-kb-dev{a} x11proto-randr-dev{a} x11proto-render-dev{a} x11proto-xext-dev{a} x11proto-xinerama-dev{a} xtrans-dev{a} zlib1g-dev{a} 
The following packages are RECOMMENDED but will NOT be installed:
  aspell-de aspell-de-alt aspell-en aspell-tl binfmt-support dbus-x11 esound-clients fakeroot gnome-keyring gnome-mount gvfs hicolor-icon-theme hunspell-ar hunspell-da hunspell-de-at hunspell-de-ch 
  hunspell-de-de hunspell-en-us hunspell-eu-es hunspell-fr hunspell-hu hunspell-ne hunspell-se hunspell-uz hunspell-vi libatk1.0-data libcompress-zlib-perl libfribidi0 libglib2.0-data libgnomevfs2-extra 
  libgtk2.0-bin libhtml-format-perl libmail-sendmail-perl libmailtools-perl libmono-i18n1.0-cil libmono-i18n2.0-cil libpam-ck-connector libxml-sax-expat-perl myspell-af myspell-bg myspell-ca myspell-cs-cz 
  myspell-de-de-oldspell myspell-en-au myspell-en-gb myspell-en-us myspell-en-za myspell-eo myspell-es myspell-et myspell-fa myspell-fo myspell-fr myspell-ga myspell-gd myspell-gl-es myspell-gv myspell-he 
  myspell-hr myspell-hu myspell-hy myspell-it myspell-ku myspell-lt myspell-lv myspell-nb myspell-nl myspell-nn myspell-pl myspell-pt-br myspell-pt-pt myspell-ru myspell-sk myspell-sv-se myspell-sw myspell-th 
  myspell-uk patchutils x-ttcidfont-conf xml-core 
0 packages upgraded, 278 newly installed, 0 to remove and 0 not upgraded.
Need to get 75.3MB/79.2MB of archives. After unpacking 307MB will be used.
[B]The following packages have unmet dependencies:
  pbuilder-satisfydepends-dummy: Depends: libgtksourceview2.0-cil (>= 0.10) which is a virtual package.
                                 Depends: libmono-cairo1.0-cil which is a virtual package.
                                 Depends: libmono-cecil0.5-cil which is a virtual package.
                                 Depends: mono-xsp-base which is a virtual package.
                                 Depends: mono-xsp2-base which is a virtual package.[/B]
The following actions will resolve these dependencies:

Remove the following packages:
pbuilder-satisfydepends-dummy

Score is -9850

Writing extended state information... Done
debconf: delaying package configuration, since apt-utils is not installed
(Reading database ... 10496 files and directories currently installed.)
Removing pbuilder-satisfydepends-dummy ...
Selecting previously deselected package libmagic1.
(Reading database ... 10496 files and directories currently installed.)
Unpacking libmagic1 (from .../libmagic1_4.26-2ubuntu2_i386.deb) ...
Selecting previously deselected package file.
Unpacking file (from .../file_4.26-2ubuntu2_i386.deb) ...
Selecting previously deselected package libsqlite3-0.
Unpacking libsqlite3-0 (from .../libsqlite3-0_3.6.10-1_i386.deb) ...
Selecting previously deselected package mime-support.
Unpacking mime-support (from .../mime-support_3.44-1_all.deb) ...
Selecting previously deselected package python2.6.
Unpacking python2.6 (from .../python2.6_2.6.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package python.
Unpacking python (from .../python_2.6.1-0ubuntu3_all.deb) ...
Selecting previously deselected package bsdmainutils.
Unpacking bsdmainutils (from .../bsdmainutils_6.1.10ubuntu3_i386.deb) ...
Selecting previously deselected package psmisc.
Unpacking psmisc (from .../psmisc_22.6-1_i386.deb) ...
Selecting previously deselected package libpng12-0.
Unpacking libpng12-0 (from .../libpng12-0_1.2.27-2ubuntu2_i386.deb) ...
Setting up libmagic1 (4.26-2ubuntu2) ...

Setting up file (4.26-2ubuntu2) ...
Setting up libsqlite3-0 (3.6.10-1) ...

Setting up mime-support (3.44-1) ...

Setting up python2.6 (2.6.1-1ubuntu1) ...

Setting up python (2.6.1-0ubuntu3) ...

Setting up bsdmainutils (6.1.10ubuntu3) ...

Setting up psmisc (22.6-1) ...

Setting up libpng12-0 (1.2.27-2ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

Current status: 0 broken [-1].
Aptitude couldn't satisfy the build dependencies
E: pbuilder-satisfydepends failed.
Copying back the cached apt archive contents
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> cleaning the build env 
    -> removing directory /var/cache/pbuilder/build//25764 and its subdirectories

```

Scroll down a little and you will see a highlighted part with 5 packages names. I searched them all in synaptic and I can guarantee that they exist with the appropriate versions.

but still pbuilder can't find them? any ideas?

PS: I have mono 2.0 (major dependency) from PPA, does it have to do anything with it?

thanks

---

### Post by directhex on 2009-03-15
I suspect your pbuilder is not configured to use universe packages

---

### Post by cb951303 on 2009-03-15
ok, I retried with this pbuilder create string

> 
sudo pbuilder create --distribution intrepid --othermirror "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid main restricted universe multiverse | deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-backports main restricted universe multiverse | deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-security main restricted universe multiverse | deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-updates main restricted universe multiverse | deb [http://ppa.launchpad.net/mono-ubuntu/ppa/ubuntu](http://ppa.launchpad.net/mono-ubuntu/ppa/ubuntu) intrepid main"


the last one is the mono 2.0 ppa repo.
this time I got this

> 
The following packages have unmet dependencies:
  pbuilder-satisfydepends-dummy: Depends: libgnome2.24-cil (>= 2.24) which is a virtual package.
                                 Depends: libgconf2.24-cil (>= 2.24) which is a virtual package.


looks like an improvement??

---

### Post by cb951303 on 2009-03-15
I don't know why but apparently these libraries are still on version 2.20. I manually changed the deps to >=2.20. it's compiling now

---

### Post by cb951303 on 2009-03-16
as expected, it didn't work. apparently there is another dep check in the process and it asked for version 2.24 of these 2 libs.

if I backport them too, would it break anything?

---

### Post by directhex on 2009-03-16
> **cb951303 said:**
> as expected, it didn't work. apparently there is another dep check in the process and it asked for version 2.24 of these 2 libs.

if I backport them too, would it break anything?

Yes, about 40 apps.

Use the source package from Sid, not Jaunty.

---

### Post by cb951303 on 2009-03-16
that worked thank you!

although debian sid repo don't have the monodevelop-vala and monodevelop-gdb plugins :(

---

### Post by directhex on 2009-03-16
Then revert the GTK# 2.24 transition. It just involves renaming the deps in debian/control (and the versions too, obviously)

---

