---
title: "libfam0 install problem??"
date: 2005-12-18
forum: Desktop Environments
---

### Post by macsimski on 2005-12-18
I want to install Pikdev [http://pikdev.free.fr](http://pikdev.free.fr) but there is a problem with the dependencies.
quote the site:

[INDENT]In order to install PiKdev, you need the following softwares :

KDE 3.0.x or newer
KDE and Qt development packages (headers). These packages are distribution-dependants.
The X11 headers (XFree86-devel package)
The libz, libfam and libpng libraries
(The needed packages are zlib1-devel, libfam0 and libpng3-devel on my Mandrake distribution)
gcc compiler v3.x or v2.96
gputils v0.11.x or newer (gpasm is part of gputils)
The following support must be present within your system :
ppdev, parport, parport_pc.[/INDENT]

The problem is libfam0. If i want to install the package with Adept, it wants to remove kubuntu-desktop:

[INDENT]root@ubuntu:~# apt-get install libfam0
Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  fam
The following packages will be REMOVED:
  adept akode akregator amarok amarok-gstreamer amarok-xine ark artsbuilder
  gamin gtk2-engines-gtk-qt gwenview juk k3b k3blibs kaboodle kaddressbook
  kaffeine kaffeine-gstreamer kaffeine-xine kamera kappfinder karm katapult
  kate kaudiocreator kcontrol kcron kde-guidance kde-style-lipstik
  kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-dev
  kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-bin
  kdelibs4-dev kdelibs4c2 kdemultimedia kdemultimedia-kappfinder-data
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards
  kdeprint kdesktop kdm kfind kghostview khelpcenter kicker kio-apt kio-locate
  klaptopdaemon klipper kmail kmenuedit kmid kmilo kmix knetworkconf knotes
  koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins
  konserve konsole kontact konversation kooka kopete korganizer kpdf kpf kppp
  krdc krec krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksvg
  ksysguard ksystemlog kubuntu-default-settings kubuntu-desktop kubuntu-docs
  kubuntu-konqueror-shortcuts kuser kwalletmanager kwifimanager kwin
  libarts1-mpeglib libarts1-xine libdbus-qt-1-1c2 libgamin-dev libgamin0
  libkcal2a libkcddb1 libkdepim1 libkipi0 libkleopatra0a libkonq4
  libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1
  libmimelib1a libwvstreams4.0c2-extras mpeglib noatun openoffice.org2-kde
  python-kde3 python2.4-kde3 sanekonsole wvdial
The following NEW packages will be installed:
  libfam0
0 upgraded, 1 newly installed, 126 to remove and 0 not upgraded.
Need to get 25.0kB of archives.
After unpacking 345MB disk space will be freed.
Do you want to continue (Y/n)? n[/INDENT]

Why???? the reverse is also the case. If i say yes and all the packages above are removed and libfam0 is installed i have no kde. when i try to install KDE it automatically removes libfam0.

it seems that they cannot live together on one system. so how to install a neat PIC developement enviroment?

---

### Post by GeneralZod on 2005-12-18
fam has been replaced by gamin, and they cannot co-exist, so attempting to install fam will try to remove gamin, which it looks like KDE depends on.

---

