---
title: "speed up kubuntu..."
date: 2007-03-21
forum: Desktop Environments
---

### Post by qiemem on 2007-03-21
I've been floating between different the different DEs (and straight WMs) for a while and have finally settled on KDE; I've got it customized exactly the way I want it, etc. Thing is, it's a touch on the slow side, especially considering this is a rather older laptop. I'm wondering if anyone knows how I might speed it up. Thanks!

---

### Post by pay on 2007-03-21
Try this ```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator apt-index-watcher bogofilter bogofilter-bdb bogofilter-common dcraw debtags digikam digikamimageplugins flac gtk2-engines-gtk-qt gwenview hwdb-client-kde imagemagick kaddressbook kaffeine kaffeine-xine karm katapult kaudiocreator kbstate kcron kde-guidance-powermanager kde-icons-mono kde-systemsettings kdeadmin-kfile-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepim-kio-plugins kdepim-kresources kdepim-wizards kdnssd keep kghostview kio-apt kio-locate kipi-plugins kitchensync kmag kmail kmailcvt kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knode knotes koffice-data koffice-libs konq-plugins kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita krita-data kscd kscreensaver kscreensaver-xsavers ksnapshot ksplash-engine-moodin ksvg ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin-style-crystal language-selector-qt latex-xft-fonts libc6-dev libexif-dev libgmp3c2 libgpgme11 libgphoto2-2-dev libgsl0 libifp4 libimlib2 libjasper-runtime libjpeg-progs libk3b2 libkcal2b libkdepim1a libkexif1 libkipi0 libkleopatra1 libkmime2 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 libmagick++9c2a libmimelib1c2a libmysqlclient15off libnjb5 libpoppler1-qt libpq4 libpythonize0 libqt-perl libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librsync1 libruby1.8 libskim0 libsmokeqt1 libsqlite0 libtdb1 libtunepimp3 libxine-extracodecs libxine1 linux-libc-dev mysql-common ncompress ocrad openoffice.org-kde openoffice.org-style-crystal p7zip p7zip-full postfix procmail pykdeextensions python-elementtree python-kde3 python-qt3 python-qt4 python-sip4 python2.4-dev qca-tls qobex qt4-qtconfig rdiff-backup ruby ruby1.8 sane-utils scim-qtimm skim speedcrunch vcdimager wlassistant zoo && sudo aptitude update && sudo aptitude install kde-core
```[http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)

---

### Post by qiemem on 2007-03-21
A touch drastic, but working quite well. Thanks.

Oh, I used aptitude to install kubuntu-desktop, so instead of removing all the packages like that, I did "aptitude remove kubuntu-desktop". I assume that won't make a difference.

---

