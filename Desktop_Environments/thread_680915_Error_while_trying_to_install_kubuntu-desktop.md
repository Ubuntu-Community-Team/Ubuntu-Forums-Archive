---
title: "Error while trying to install kubuntu-desktop"
date: 2008-01-28
forum: Desktop Environments
---

### Post by Biznarie on 2008-01-28
I started off with the default gnome desktop but now I want to move to KDE (I previously had KDE4 installed but I did not like it and uninstalled). First thing I ran was sudo aptitude update, then sudo aptitude install kubuntu-desktop. Here's what happens.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  kdesktop kdm 
The following packages are unused and will be REMOVED:
  libgtk1.2-common libsdl-net1.2 libswt3.2-gtk-jni 
The following packages have been automatically kept back:
  kdelibs-data kdelibs4c2a 
The following NEW packages will be automatically installed:
  adept adept-batch adept-common adept-installer adept-manager 
  adept-notifier adept-updater akregator amarok-xine debtags dirmngr 
  enscript exiv2 fftw3 gnupg-agent gnupg2 gpgsm ijsgutenprint kaddressbook 
  kaffeine kamera kdebase-data kdemultimedia-kio-plugins kdepim-kio-plugins 
  kdepim-kresources kfind kicker kipi-plugins kleopatra kmail kmplayer-base 
  knode konqueror konsole kooka korganizer kpersonalizer kregexpeditor 
  kscreensaver-xsavers ksysguardd kwin kwin-style-crystal libakode2 
  libarts1-mpeglib libclucene0 libcluceneindex0 libept0 libexiv2-0 
  libfreetype6-dev libgpgme11 libifp4 libijs-0.35 libimlib2 libjpeg-progs 
  libkbluetooth0 libkcal2b libkcddb1 libkdcraw1 libkdepim1a libkexiv2-1 
  libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 
  libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 libmimelib1c2a 
  libmysqlclient15off libnjb5 libofa0 libopenobex1 libpoppler-qt2 libpq5 
  libpth20 libpythonize0 libqt-perl libqt4-core libqt4-gui 
  libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsearchclient0 
  libskim0 libslang2-dev libsmokeqt1 libsqlite0 libstreamanalyzer0 
  libstreams0 libstrigihtmlgui0 libtunepimp5 libungif4g libxapian15 
  libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1 libxine1-doc 
  libxine1-ffmpeg libxvmc1 mpeglib mpg123 mysql-common 
  network-manager-openvpn network-manager-vpnc networkstatus ocrad 
  openoffice.org-style-crystal openvpn perl-suid pinentry-curses 
  pinentry-qt pmount poster procmail psutils pykdeextensions 
  python-elementtree python-kde3 python-pylibacl python-pyxattr python-qt3 
  python-qt4 python-qt4-dbus python-sip4 python2.5-dev qt4-qtconfig 
  rdiff-backup ruby ruby1.8 vpnc zlib1g-dev zoo 
The following NEW packages will be installed:
  adept adept-batch adept-common adept-installer adept-manager 
  adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark 
  arts debtags digikam dirmngr dolphin enscript exiv2 fftw3 
  foomatic-db-gutenprint gdebi-kde gnupg-agent gnupg2 gpgsm gtk-qt-engine 
  gwenview hplip-gui hwdb-client-kde ijsgutenprint kaddressbook kaffeine 
  kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron 
  kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester 
  kde-systemsettings kdeadmin-kfile-plugins kdebase-data 
  kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins 
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins 
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd 
  kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesudo 
  kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate 
  kio-umountwrapper kipi-plugins kleopatra klipper kmag kmail kmailcvt 
  kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins 
  knetworkconf knode knotes konq-plugins konqueror konqueror-nsplugins 
  konsole kontact konversation kooka kopete korganizer kpdf kpersonalizer 
  kpf kppp krdc kregexpeditor krfb kscreensaver kscreensaver-xsavers 
  ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard 
  ksysguardd ksystemlog kubuntu-artwork-usplash kubuntu-default-settings 
  kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd 
  kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 
  libarts1-akode libarts1-mpeglib libclucene0 libcluceneindex0 libept0 
  libexiv2-0 libfreetype6-dev libgpgme11 libifp4 libijs-0.35 libimlib2 
  libjpeg-progs libkbluetooth0 libkcal2b libkcddb1 libkdcraw1 libkdepim1a 
  libkexiv2-1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 
  libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 libmimelib1c2a 
  libmysqlclient15off libnjb5 libofa0 libopenobex1 libpoppler-qt2 libpq5 
  libpth20 libpythonize0 libqt-perl libqt4-core libqt4-gui 
  libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsearchclient0 
  libskim0 libslang2-dev libsmokeqt1 libsqlite0 libstreamanalyzer0 
  libstreams0 libstrigihtmlgui0 libtunepimp5 libungif4g libxapian15 
  libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1 libxine1-doc 
  libxine1-ffmpeg libxvmc1 mpeglib mpg123 mysql-common network-manager-kde 
  network-manager-openvpn network-manager-vpnc networkstatus ocrad 
  openoffice.org-kde openoffice.org-style-crystal openvpn perl-suid 
  pinentry-curses pinentry-qt pmount poster procmail psutils 
  pykdeextensions python-elementtree python-kde3 python-pylibacl 
  python-pyxattr python-qt3 python-qt4 python-qt4-dbus python-sip4 
  python2.5-dev qca-tls qt4-qtconfig rdiff-backup restricted-manager-kde 
  ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch 
  strigi-applet strigi-daemon vpnc zlib1g-dev zoo 
0 packages upgraded, 229 newly installed, 3 to remove and 2 not upgraded.
Need to get 0B/174MB of archives. After unpacking 617MB will be used.
The following packages have unmet dependencies:
  kdm: Depends: kdebase-bin (= 4:3.5.8-0ubuntu2.1) but 4:3.5.8-2ubuntu3~gutsy1~ppa1 is installed.
  kdesktop: Depends: kdebase-bin (= 4:3.5.8-0ubuntu2.1) but 4:3.5.8-2ubuntu3~gutsy1~ppa1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
kdebase-bin [4:3.5.8-2ubuntu3~gutsy1~ppa1 (now) -> 4:3.5.8-0ubuntu2.1
(gutsy-updates)]

Score is 20

Accept this solution? [Y/n/q/?] y
The following packages are unused and will be REMOVED:
  kdebase-bin-kde3 libgtk1.2-common libsdl-net1.2 libswt3.2-gtk-jni 
The following packages have been automatically kept back:
  kdelibs-data kdelibs4c2a 
The following NEW packages will be automatically installed:
  adept adept-batch adept-common adept-installer adept-manager 
  adept-notifier adept-updater akregator amarok-xine debtags dirmngr 
  enscript exiv2 fftw3 gnupg-agent gnupg2 gpgsm ijsgutenprint kaddressbook 
  kaffeine kamera kdebase-data kdemultimedia-kio-plugins kdepim-kio-plugins 
  kdepim-kresources kdesktop kfind kicker kipi-plugins kleopatra kmail 
  kmplayer-base knode konqueror konsole kooka korganizer kpersonalizer 
  kregexpeditor kscreensaver-xsavers ksysguardd kwin kwin-style-crystal 
  libakode2 libarts1-mpeglib libclucene0 libcluceneindex0 libept0 
  libexiv2-0 libfreetype6-dev libgpgme11 libifp4 libijs-0.35 libimlib2 
  libjpeg-progs libkbluetooth0 libkcal2b libkcddb1 libkdcraw1 libkdepim1a 
  libkexiv2-1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 
  libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 libmimelib1c2a 
  libmysqlclient15off libnjb5 libofa0 libopenobex1 libpoppler-qt2 libpq5 
  libpth20 libpythonize0 libqt-perl libqt4-core libqt4-gui 
  libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsearchclient0 
  libskim0 libslang2-dev libsmokeqt1 libsqlite0 libstreamanalyzer0 
  libstreams0 libstrigihtmlgui0 libtunepimp5 libungif4g libxapian15 
  libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1 libxine1-doc 
  libxine1-ffmpeg libxvmc1 mpeglib mpg123 mysql-common 
  network-manager-openvpn network-manager-vpnc networkstatus ocrad 
  openoffice.org-style-crystal openvpn perl-suid pinentry-curses 
  pinentry-qt pmount poster procmail psutils pykdeextensions 
  python-elementtree python-kde3 python-pylibacl python-pyxattr python-qt3 
  python-qt4 python-qt4-dbus python-sip4 python2.5-dev qt4-qtconfig 
  rdiff-backup ruby ruby1.8 vpnc zlib1g-dev zoo 
The following packages will be DOWNGRADED:
  kdebase-bin 
The following NEW packages will be installed:
  adept adept-batch adept-common adept-installer adept-manager 
  adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark 
  arts debtags digikam dirmngr dolphin enscript exiv2 fftw3 
  foomatic-db-gutenprint gdebi-kde gnupg-agent gnupg2 gpgsm gtk-qt-engine 
  gwenview hplip-gui hwdb-client-kde ijsgutenprint kaddressbook kaffeine 
  kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron 
  kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester 
  kde-systemsettings kdeadmin-kfile-plugins kdebase-data 
  kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins 
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins 
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd 
  kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop 
  kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt 
  kio-locate kio-umountwrapper kipi-plugins kleopatra klipper kmag kmail 
  kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base 
  kmplayer-konq-plugins knetworkconf knode knotes konq-plugins konqueror 
  konqueror-nsplugins konsole kontact konversation kooka kopete korganizer 
  kpdf kpersonalizer kpf kppp krdc kregexpeditor krfb kscreensaver 
  kscreensaver-xsavers ksmserver ksnapshot ksplash ksplash-engine-moodin 
  ksvg ksysguard ksysguardd ksystemlog kubuntu-artwork-usplash 
  kubuntu-default-settings kubuntu-desktop kubuntu-docs 
  kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal 
  language-selector-qt libakode2 libarts1-akode libarts1-mpeglib 
  libclucene0 libcluceneindex0 libept0 libexiv2-0 libfreetype6-dev 
  libgpgme11 libifp4 libijs-0.35 libimlib2 libjpeg-progs libkbluetooth0 
  libkcal2b libkcddb1 libkdcraw1 libkdepim1a libkexiv2-1 libkipi0 
  libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 
  libksba8 libkscan1 libksieve0 libktnef1 libmimelib1c2a 
  libmysqlclient15off libnjb5 libofa0 libopenobex1 libpoppler-qt2 libpq5 
  libpth20 libpythonize0 libqt-perl libqt4-core libqt4-gui 
  libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsearchclient0 
  libskim0 libslang2-dev libsmokeqt1 libsqlite0 libstreamanalyzer0 
  libstreams0 libstrigihtmlgui0 libtunepimp5 libungif4g libxapian15 
  libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1 libxine1-doc 
  libxine1-ffmpeg libxvmc1 mpeglib mpg123 mysql-common network-manager-kde 
  network-manager-openvpn network-manager-vpnc networkstatus ocrad 
  openoffice.org-kde openoffice.org-style-crystal openvpn perl-suid 
  pinentry-curses pinentry-qt pmount poster procmail psutils 
  pykdeextensions python-elementtree python-kde3 python-pylibacl 
  python-pyxattr python-qt3 python-qt4 python-qt4-dbus python-sip4 
  python2.5-dev qca-tls qt4-qtconfig rdiff-backup restricted-manager-kde 
  ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch 
  strigi-applet strigi-daemon vpnc zlib1g-dev zoo 
0 packages upgraded, 229 newly installed, 1 downgraded, 4 to remove and 2 not upgraded.
Need to get 0B/176MB of archives. After unpacking 617MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg - warning: downgrading kdebase-bin from 4:3.5.8-2ubuntu3~gutsy1~ppa1 to 4:3.5.8-0ubuntu2.1.
(Reading database ... 107028 files and directories currently installed.)
Preparing to replace kdebase-bin 4:3.5.8-2ubuntu3~gutsy1~ppa1 (using .../kdebase-bin_4%3a3.5.8-0ubuntu2.1_i386.deb) ...
Unpacking replacement kdebase-bin ...
[B]dpkg: error processing /var/cache/apt/archives/kdebase-bin_4%3a3.5.8-0ubuntu2.1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/kdebugdialog', which is also in package kdebase-bin-kde3
dpkg-deb: subprocess paste killed by signal (Broken pipe)
The generated cache was invalid.
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-bin_4%3a3.5.8-0ubuntu2.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:[/B]
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done
```

Thanks in advance.
Barry

---

### Post by scizmeli on 2008-02-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/kubuntu-meta/+bug/51656](https://bugs.launchpad.net/ubuntu/+source/kubuntu-meta/+bug/51656) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hate to come up with no solutions but I have the same problem here...

There is also a similar bug in launchpad (see the submitted URL)

Anybody any ideas?

---

### Post by PmDematagoda on 2008-02-09
Remove the package causing the problem in the first place(in your case kdebase-bin) using:-
```
sudo apt-get remove kdebase-bin
```
Then see if your problem is solved.

---

### Post by firmit on 2008-03-25
Having some install problems myself.
Got some "unresolvable dependencies" on the packages *kaffeine-xine, libcluceneindex0*. 

Solved by deselecting updates from *gutsy proposed, gutsy backports*

---

