---
title: "Uninstalling all of kde"
date: 2009-06-18
forum: Desktop Environments
---

### Post by penguinchrissy on 2009-06-18
I recently wanted to try the kde desktop environment so I installed kubuntu. Well in short kde isn't quite for me so I was wondering if there is an easy way to uninstall it with all the apps that are installed with it? 

Can the same process be used to remove enlightenment?

As always thanks for you help!

---

### Post by dE_logics on 2009-06-18
Search for KDE in synaptic.

Just remove one of the main installed packages...like KDE common, that should do.

---

### Post by cherva on 2009-06-18
You can open a terminal ( Applications->Accessories->Terminal ) and type:
```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts bogofilter bogofilter-bdb bogofilter-common debtags digikam enscript fftw3 gtk-qt-engine gwenview hwdb-client-kde k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kexi kfind kghostview khelpcenter kicker kio-apt kio-locate kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knetworkmanager knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libavahi-compat-libdnssd1 libavahi-qt3-1 libcurl3-gnutls libdbus-qt-1-1c2 libexiv2-0.12 libflac++5c2 libgmp3c2 libgpgme11 libgsl0 libid3tag0 libifp4 libimlib2 libjasper-runtime libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkexiv2-0 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 liblua50 liblualib50 libmeanwhile1 libmimelib1c2a libmodplug0c2 libmpcdec3 libmtp5 libmysqlclient15off libnjb5 libofa0 liboggflac3 libopenexr2c2a libopenobex1 libpcre3 libpoppler1-qt libpq5 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsamplerate0 libskim0 libsmokeqt1 libsqlite0 libtdb1 libtunepimp5 libxine1 libxvmc1 mysql-common networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pmount poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-sip4 python2.5-dev qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch vorbis-tools 
``` I belive that this will uninstall every kde package from your machine. This will uninstall the QT libraries too, so if you use Skype you will have to install them again.

---

### Post by penguinchrissy on 2009-06-18
Sorry for not doing my homework it was just early in the morning and I wasn't thinking right. Cherva I found what you posted doesn't quite work because everything there wasn't installed this seems to have worked

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

It removes everything plus some but I think the install ubuntu-desktop will reinstall everything that was uninstalled. 

Running it now will let you know how it goes.

---

### Post by penguinchrissy on 2009-06-18
Well the install ubuntu-desktop didn't work as planed but this does
sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop

So here are the steps to go form a GNOME desktop that was running and then had KDE installed on it back to a pure GNOME in ubuntu 9.04

1) go here [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) to remove all the kde programs

2)Do sudo apt-get remove ubuntu-dekstop then sudo apt-get install ubuntu-desktop to get all the programs the previous uninstall program had uninstalled.


WARNING:
After the reinstall of ubuntu-desktop you might still have packages missing like virtual box and wine. Ubuntu-desktop only installs the programs that come with a fresh install, so some programs may still need to be reinstalled.




Hope this helps.

---

