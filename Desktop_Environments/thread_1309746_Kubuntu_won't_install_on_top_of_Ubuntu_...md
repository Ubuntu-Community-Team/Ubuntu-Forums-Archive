---
title: "Kubuntu won't install on top of Ubuntu ..?"
date: 2009-11-01
forum: Desktop Environments
---

### Post by mickie.kext on 2009-11-01
I tryed to install kubuntu on top of Ubntu 9.10 AMD64, but it says that some packages are broken:

> $ sudo aptitude install  kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  jockey-kde language-selector-qt openoffice.org-core openoffice.org-kde 
  openoffice.org-style-oxygen usb-creator-kde 
The following NEW packages will be installed:
  akonadi-server{a} akregator amarok amarok-common{a} amarok-utils{a} 
  apport-kde apturl-kde ark cdrdao dolphin exiv2{a} foomatic-db-gutenprint 
  gdebi-kde{a} gnupg-agent graphicsmagick{a} 
  graphicsmagick-imagemagick-compat{a} gtk2-engines-qtcurve gwenview 
  hpijs-ppds ibus-qt4 ijsgutenprint{a} install-package{a} k3b k3b-data{a} 
  kaddressbook kaffeine kamera kate kcm-gtk kde-icons-oxygen{a} 
  kde-style-qtcurve{a} kde-window-manager kde-zeroconf kdebase-bin{a} 
  kdebase-data{a} kdebase-plasma kdebase-runtime{a} 
  kdebase-runtime-bin-kde4{a} kdebase-runtime-data{a} 
  kdebase-runtime-data-common{a} kdebase-workspace-bin 
  kdebase-workspace-data{a} kdebase-workspace-kgreet-plugins{a} 
  kdebase-workspace-libs4+5{a} kdebluetooth kdegraphics-strigi-plugins 
  kdelibs-bin{a} kdelibs5{a} kdelibs5-data{a} kdemultimedia-kio-plugins 
  kdepasswd kdepim-groupware{a} kdepim-kresources kdepim-runtime{a} 
  kdepim-runtime-data{a} kdepim-runtime-libs4{a} kdepim-strigi-plugins 
  kdepim-wizards kdepimlibs-data{a} kdepimlibs5{a} kdesudo{a} kdm kfind{a} 
  khelpcenter4{a} kipi-plugins klipper kmag kmail kmix kmousetool knotes 
  konq-plugins{a} konq-plugins-l10n{a} konqueror{a} konqueror-nsplugins{a} 
  konqueror-plugin-searchbar konqueror-plugins{a} konsole kontact kopete 
  kopete-facebook korganizer{a} kpackagekit{a} kppp krdc krfb ksnapshot 
  ksysguard ksysguardd{a} ksystemlog ktimetracker ktorrent ktorrent-data{a} 
  kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop 
  kubuntu-docs kubuntu-firefox-installer kubuntu-konqueror-shortcuts kvkbd 
  kwalletmanager kwin-style-qtcurve{a} libakonadiprivate1{a} libao2{a} 
  libboost-program-options1.38.0{a} libclucene0ldbl{a} libepub0{a} 
  libexiv2-5{a} libflac++6{a} libgraphicsmagick3{a} libindicate-qt0{a} 
  libjpeg-progs{a} libk3b6{a} libkabcommon4{a} libkcddb4{a} libkdcraw7{a} 
  libkdecorations4{a} libkdepim4{a} libkexiv2-7{a} libkipi6{a} libkleo4{a} 
  libknotificationitem1{a} libkonq5{a} libkonq5-templates{a} 
  libkonqsidebarplugin4{a} libkontactinterfaces4{a} libkopete4{a} 
  libkorundum4-ruby1.8{a} libkpgp4{a} libksane0{a} libksieve4{a} 
  libkwineffects1{a} liblancelot0{a} liblastfm0{a} liblzma0{a} 
  libmimelib4{a} libmsn0.1{a} libokularcore1{a} libotr2{a} 
  libpackagekit-glib11{a} libpackagekit-qt11{a} libplasma3{a} 
  libpolkit-grant2{a} libpolkit-qt0{a} libpoppler-qt4-3{a} libqca2{a} 
  libqca2-plugin-ossl{a} libqimageblitz4{a} libqjson0{a} 
  libqscintilla2-5{a} libqt4-assistant{a} libqt4-dbus{a} libqt4-designer{a} 
  libqt4-help{a} libqt4-opengl{a} libqt4-phonon{a} libqt4-qt3support{a} 
  libqt4-ruby1.8{a} libqt4-script{a} libqt4-scripttools{a} libqt4-sql{a} 
  libqt4-sql-mysql{a} libqt4-sql-sqlite{a} libqt4-test{a} libqt4-webkit{a} 
  libqt4-xml{a} libqt4-xmlpatterns{a} libqtscript4-core{a} 
  libqtscript4-gui{a} libqtscript4-network{a} libqtscript4-sql{a} 
  libqtscript4-uitools{a} libqtscript4-xml{a} libruby1.8{a} libscim8c2a{a} 
  libsmokekde4-2{a} libsmokeqt4-2{a} libsoprano4{a} libstreamanalyzer0{a} 
  libstreams0{a} libstrigiqtdbusclient0{a} libtag-extras1{a} 
  libvncserver0{a} libxcb-shape0{a} libxcb-shm0{a} libxcb-xv0{a} 
  libxine1{a} libxine1-bin{a} libxine1-console{a} libxine1-misc-plugins{a} 
  libxine1-x{a} libzip1{a} mysql-server-core-5.1{a} okular 
  okular-extra-backends oxygen-cursor-theme packagekit{a} 
  packagekit-backend-apt{a} phonon-backend-xine{a} pinentry-gtk2{a} 
  pinentry-qt4 plasma-dataengines-addons{a} plasma-dataengines-workspace{a} 
  plasma-scriptengine-python{a} plasma-widget-facebook 
  plasma-widget-folderview{a} plasma-widget-googlecalendar 
  plasma-widget-indicatordisplay plasma-widget-kimpanel 
  plasma-widget-kubuntu-qa-feedback plasma-widget-lancelot{a} 
  plasma-widget-networkmanagement plasma-widget-quickaccess 
  plasma-widgets-addons plasma-widgets-workspace{a} printer-applet 
  python-kde4{a} python-packagekit{a} python-qt4{a} python-qt4-dbus{a} 
  python-sip4{a} quassel quassel-data{a} ruby{a} ruby1.8{a} 
  software-properties-kde soprano-daemon{a} speedcrunch 
  system-config-printer-kde systemsettings ttf-arphic-uming 
  update-manager-kde{a} update-notifier-kde{a} userconfig 
The following packages will be REMOVED:
  avant-window-navigator-data{u} awn-manager{u} libawn-extras0{u} 
  libawn0{u} python-alsaaudio{u} python-awn{u} python-awn-extras{u} 
  python-awnlib{u} python-chardet{u} python-dateutil{u} 
  python-feedparser{u} python-gnomedesktop{u} python-sqlalchemy{u} 
  python-utidylib{u} python-wnck{u} sqlite3{u} 
0 packages upgraded, 239 newly installed, 16 to remove and 0 not upgraded.
Need to get 175MB of archives. After unpacking 708MB will be used.
The following packages have unmet dependencies:
  language-selector-qt: Depends: language-selector-common (= 0.4.11) but 0.4.18 is installed.
  usb-creator-kde: Depends: usb-creator-common (= 0.2.7) but 0.2.12 is installed.
  openoffice.org-kde: Depends: openoffice.org-core (= 1:3.1.1-2ubuntu3) but 1:3.1.1-5ubuntu1 is installed.
  openoffice.org-style-oxygen: Depends: openoffice.org-common (= 1:3.1.1-2ubuntu3) but 1:3.1.1-5ubuntu1 is installed.
  jockey-kde: Depends: jockey-common (= 0.5.4-0ubuntu1) but 0.5.5-0ubuntu2 is installed.
  openoffice.org-core: Conflicts: openoffice.org-kde (< 1:3.1.1-5ubuntu1) but 1:3.1.1-2ubuntu3 is to be installed.
The following actions will resolve these dependencies:

Keep the following packages at their current version:
openoffice.org-kde [Not Installed]
usb-creator-kde [Not Installed]

Downgrade the following packages:
jockey-common [0.5.5-0ubuntu2 (now) -> 0.5.4-0ubuntu1 (karmic)]
jockey-gtk [0.5.5-0ubuntu2 (now) -> 0.5.4-0ubuntu1 (karmic)]
language-selector [0.4.18 (now) -> 0.4.11 (karmic)]
language-selector-common [0.4.18 (now) -> 0.4.11 (karmic)]
openoffice.org-common [1:3.1.1-5ubuntu1 (now) -> 1:3.1.1-2ubuntu3 (karmic)]

Leave the following dependencies unresolved:
kubuntu-desktop recommends openoffice.org-kde
kubuntu-desktop recommends usb-creator-kde
Score is -62

Accept this solution? [Y/n/q/?] q

I chosen q to quit since I do not want to break installation I just installed. I just waned to ask if is someon having same problem, and is it safe to ignore that warning? 

Sorry for my bad english and thanks in advance:p.

EDIT: I forgat to say... I changed server in software sources and now is OK.

---

