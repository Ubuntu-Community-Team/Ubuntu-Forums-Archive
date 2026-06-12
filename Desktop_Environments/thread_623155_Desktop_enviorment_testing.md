---
title: "Desktop enviorment testing"
date: 2007-11-25
forum: Desktop Environments
---

### Post by MONODA on 2007-11-25
Hi i am currently using ubuntu gutsy and have decided I want to try some otherdesktop enviorments and windows managers such as KDE konquerer and enlightement. I may want to remove it later. how can i do this without damaging my system.  thanky ou in adavance

---

### Post by aysiu on 2007-11-25
You won't damage your system, but you may well clutter up your system.

The absolute cleanest way to try out a desktop environment or window manager is to keep track of all the packages that get installed when you install it.

For example, right now, all I have installed is IceWM. 

If I wanted to install and try out KDE, I'd type ```
sudo apt-get install kubuntu-desktop
``` and then I'd see that *apt-get* wants to install ```
 sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
[b]  adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport apport-qt ark arts bluez-cups bluez-utils bogofilter bogofilter-bdb
  bogofilter-common debtags digikam dolphin enscript fftw3 foomatic-db-gutenprint foomatic-db-hpijs gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hpijs hplip hplip-data hplip-gui hwdb-client-kde
  ijsgutenprint kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings
  kdeadmin-kfile-plugins kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt
  kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb
  kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts kvkbd
  kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libclucene0 libept0 libexiv2-0 libgmp3c2 libgpgme11 libgsl0 libifp4 libijs-0.35 libimlib2 libjpeg-progs libkbluetooth0
  libkcal2b libkcddb1 libkdcraw1 libkdepim1a libkexiv2-1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 libmimelib1c2a libmysqlclient15off
  libnjb5 libofa0 libopenobex1 libpoppler-qt2 libpth20 libpythonize0 libqt-perl libqt4-core libqt4-gui librsync1 libruby1.8 libsamplerate0 libsearchclient0 libskim0 libsmokeqt1 libsnmp10 libstreamanalyzer0
  libstreams0 libstrigihtmlgui0 libtunepimp5 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1 libxine1-console libxine1-ffmpeg libxine1-gnome libxine1-misc-plugins libxine1-plugins libxine1-x
  mysql-common network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-qt4-dbus
  python-sip4 python2.5-dev qca-tls rdiff-backup restricted-manager-kde ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon vorbis-tools[/b]
Suggested packages:
  libvisual-0.4-plugins libqt0-ruby1.8 amarok-engines rar unrar unrar-free bluez-firmware pax db4.5-util tagcoll digikam-doc kfloppy fftw3-dev hpijs-ppds hplip-doc kate-plugins mtools lame egroupware efax
  hylafax-client mgetty-fax menu htdig kicker-applets gallery kipi-plugins-doc clamav f-prot-installer kdeaddons-doc-html gij-4.1 libgcj7-awt libjessie-java kpilot knewsticker kweather gnokii libsoap-lite-perl
  kdeartwork-emoticons gnomemeeting php5-cli kpager sword-frontend gsl-ref-psdoc gsl-doc-pdf gsl-ref-html xapian-tools gxine xine-ui kde-icons-crystal crystalcursors pinentry-doc gv python-kde3-dbg
  python-qt3-gl python-qt3-doc libqt3-mt-mysql libqt3-mt-odbc libqt3-mt-psql python-qt3-dbg python-qt4-dbg python-sip4-dbg ruby1.8-examples rdoc1.8 ri1.8 scim-m17n scim-tables-ja scim-tables-ko scim-uim
  strigi-plugins
Recommended packages:
  ncompress zoo p7zip-full bluez-gnome pinentry-curses pinentry python-reportlab kregexpeditor pmount graphicsmagick-imagemagick-compat imagemagick sane-utils mpg123 kleopatra procmail libarts1-mpeglib knode
  ocrad gocr kscreensaver-xsavers kpersonalizer exiv2 qt4-qtconfig libxine1-doc libxine-doc network-manager-vpnc network-manager-openvpn python-elementtree python-pylibacl python-pyxattr
The following NEW packages will be installed:
  adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport apport-qt ark arts bluez-cups bluez-utils bogofilter bogofilter-bdb
  bogofilter-common debtags digikam dolphin enscript fftw3 foomatic-db-gutenprint foomatic-db-hpijs gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hpijs hplip hplip-data hplip-gui hwdb-client-kde
  ijsgutenprint kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings
  kdeadmin-kfile-plugins kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt
  kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb
  kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs
  kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libclucene0 libept0 libexiv2-0 libgmp3c2 libgpgme11 libgsl0 libifp4 libijs-0.35 libimlib2
  libjpeg-progs libkbluetooth0 libkcal2b libkcddb1 libkdcraw1 libkdepim1a libkexiv2-1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1
  libmimelib1c2a libmysqlclient15off libnjb5 libofa0 libopenobex1 libpoppler-qt2 libpth20 libpythonize0 libqt-perl libqt4-core libqt4-gui librsync1 libruby1.8 libsamplerate0 libsearchclient0 libskim0
  libsmokeqt1 libsnmp10 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1 libxine1-console libxine1-ffmpeg libxine1-gnome
  libxine1-misc-plugins libxine1-plugins libxine1-x mysql-common network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions
  python-kde3 python-qt3 python-qt4 python-qt4-dbus python-sip4 python2.5-dev qca-tls rdiff-backup restricted-manager-kde ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch strigi-applet
  strigi-daemon vorbis-tools
0 upgraded, 215 newly installed, 0 to remove and 0 not upgraded.
Need to get 181MB of archives.
After unpacking 631MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

``` So then I would paste the additional packages into a text file. When I wanted to remove KDE later, I'd do ```
sudo apt-get remove [b]adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport apport-qt ark arts bluez-cups bluez-utils bogofilter bogofilter-bdb
  bogofilter-common debtags digikam dolphin enscript fftw3 foomatic-db-gutenprint foomatic-db-hpijs gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hpijs hplip hplip-data hplip-gui hwdb-client-kde
  ijsgutenprint kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings
  kdeadmin-kfile-plugins kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt
  kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb
  kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts kvkbd
  kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libclucene0 libept0 libexiv2-0 libgmp3c2 libgpgme11 libgsl0 libifp4 libijs-0.35 libimlib2 libjpeg-progs libkbluetooth0
  libkcal2b libkcddb1 libkdcraw1 libkdepim1a libkexiv2-1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 libmimelib1c2a libmysqlclient15off
  libnjb5 libofa0 libopenobex1 libpoppler-qt2 libpth20 libpythonize0 libqt-perl libqt4-core libqt4-gui librsync1 libruby1.8 libsamplerate0 libsearchclient0 libskim0 libsmokeqt1 libsnmp10 libstreamanalyzer0
  libstreams0 libstrigihtmlgui0 libtunepimp5 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1 libxine1-console libxine1-ffmpeg libxine1-gnome libxine1-misc-plugins libxine1-plugins libxine1-x
  mysql-common network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-qt4-dbus
  python-sip4 python2.5-dev qca-tls rdiff-backup restricted-manager-kde ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon vorbis-tools[/b]
``` Installing and trying out desktop environments and window managers will **not** damage your system, but if you don't keep careful track of all the packages you installed, you may have some lingering packages when you remove the DE or WM later.

---

### Post by MONODA on 2007-11-26
Ok thanks but i remember on my last install of gutsy I had installed gOS with a similar command except I used aptitude. When I removed it and restarted, i got errors with the gnome setting daemon and such.

---

