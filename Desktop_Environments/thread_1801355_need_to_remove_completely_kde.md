---
title: "need to remove completely kde"
date: 2011-07-10
forum: Desktop Environments
---

### Post by nos09 on 2011-07-10
okay i know its been asked a million times .. but believe me i tried !!! lol 
anyway, to begin with i downloaded Kubuntu-dvd.11.04 a week ago and as its turned out i dont like kde anymore .. so i installed ubuntu-desktop and so far it feels like home again ! 

now, when i installed the kde form dvd i installed much more package i actually required like languages (too many of them !) so i dont need any kde package because i m using gnome and i m quite happy with gnome apps ! 

now the question is how can i completely remove kde ?!? i tried apt-get remove kubuntu-desktop from gnome session but it only removed 553kb package - which doesnt seem right ?!?! so anyone help me please ?!

thanks

---

### Post by koleoptero on 2011-07-10
In a terminal:

```
sudo apt-get remove akonadi-server akregator amarok amarok-common amarok-utils appmenu-gtk appmenu-qt apport-kde apturl-kde ark bluedevil cdparanoia cdrdao docbook-xsl dolphin dragonplayer dvd+rw-tools exiv2 freespacenotifier gdebi-core gdebi-kde gnupg-agent gnupg2 gpgsm growisofs gtk2-engines-oxygen gwenview ibus-qt4 icoutils jockey-kde k3b k3b-data kaddressbook kamera kate kcalc kde-config-gtk kde-config-touchpad kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-runtime kdebase-runtime-data kdebase-workspace kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdegames-card-data kdegraphics-libs-data kdegraphics-strigi-plugins kdelibs-bin kdelibs5-data kdelibs5-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdepasswd kdepim-groupware kdepim-kresources kdepim-runtime kdepim-strigi-plugins kdepim-wizards kdepimlibs-kio-plugins kdesudo kdm kdoctools kfind khelpcenter4 kinfocenter klipper kmag kmail kmix kmousetool knm-runtime knotes konsole kontact kopete kopete-message-indicator korganizer kpackagekit kpat kppp krdc krfb krosspython ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-debug-installer kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-firefox-installer kubuntu-konqueror-shortcuts kubuntu-netbook-default-settings kubuntu-notification-helper kvkbd kwalletmanager language-selector-kde libakonadi-contact4 libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4 libakonadiprotocolinternals1 libattica0 libaudio2 libbluedevil1 libboost-program-options1.42.0 libcln6 libclucene0ldbl libdbusmenu-qt2 libdebconf-kde0 libdiscid0 libdmtx0a libepub0 libexiv2-10 libflac++6 libgif4 libgpgme++2 libgpgme11 libgpod-common libgpod4 libgps19 libgraphite3 libhyphen0 libibus-qt1 libindicate-qt1 libiodbc2 libk3b6 libkabc4 libkatepartinterfaces4 libkblog4 libkcal4 libkcalcore4 libkcalutils4 libkcddb4 libkcmutils4 libkdcraw9 libkde3support4 libkdecorations4 libkdecore5 libkdegames5 libkdepim4 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4 libkemoticons4 libkephal4a libkexiv2-9 libkfile4 libkholidays4 libkhtml5 libkidletime4 libkimap4 libkimproxy4 libkio5 libkipi8 libkjsapi4 libkjsembed4 libkldap4 libkleo4 libkmediaplayer4 libkmime4 libknewstuff2-4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkonq5-templates libkonq5a libkontactinterface4 libkopete4 libkparts4 libkpgp4 libkpimidentities4 libkpimtextedit4 libkpimutils4 libkprintutils4 libkpty4 libkresources4 libkrosscore4 libksba8 libkscreensaver5 libksgrd4 libksieve4 libksignalplotter4 libktexteditor4 libktnef4 libktorrent-l10n libktorrent2 libkunitconversion4 libkutils4 libkwineffects1a libkworkspace4 libkxmlrpcclient4 liblastfm0 libmailtransport4 libmessagecore4 libmessagelist4 libmicroblog4 libmimelib4 libmpcdec6 libmsn0.3 libmtp8 libmusicbrainz3-6 libmysqlclient16 libmythes-1.2-0 libneon27-gnutls libnepomuk4 libnepomukquery4a libnepomukutils4 libntrack-qt4-1 libntrack0 libokularcore1 libpackagekit-glib2-14 libpackagekit-qt14 libphonon4 libplasma-geolocation-interface4 libplasma3 libplasmaclock4b libplasmagenericshell4 libpolkit-qt-1-1 libpoppler-qt4-3 libpowerdevilcore0 libprocesscore4b libprocessui4a libpth20 libqalculate5 libqapt-runtime libqapt1 libqca2 libqca2-plugin-ossl libqgpgme1 libqimageblitz4 libqjson0 libqt4-dbus libqt4-declarative libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns libqtassistantclient4 libqtcore4 libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml libqtwebkit4 libraptor1 librasqal2 librdf0 libreadline5 libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge libreoffice-impress libreoffice-kde libreoffice-math libreoffice-style-human libreoffice-style-oxygen libreoffice-writer libsolid4 libsolidcontrol4a libsolidcontrolifaces4a libsoprano4 libssh-4 libstlport4.6ldbl libstreamanalyzer0 libstreams0 libsyndication4 libtag-extras1 libtaskmanager4b libtextcat-data libtextcat0 libthreadweaver4 libvirtodbc0 libvncserver0 libweather-ion6 libzip1 mysql-client-core-5.1 mysql-common mysql-server-core-5.1 nepomukcontroller network-manager-pptp-kde ntrack-module-libnl-0 obexd-client odbcinst odbcinst1debian2 okular okular-extra-backends oxygen-cursor-theme oxygen-icon-theme oxygen-icon-theme-complete packagekit packagekit-backend-aptcc partitionmanager phonon phonon-backend-gstreamer pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-desktop plasma-netbook plasma-scriptengine-declarative plasma-scriptengine-javascript plasma-scriptengine-python plasma-widget-facebook plasma-widget-folderview plasma-widget-kimpanel plasma-widget-kimpanel-backend-ibus plasma-widget-menubar plasma-widget-message-indicator plasma-widget-networkmanagement plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace plymouth-theme-kubuntu-logo plymouth-theme-kubuntu-text polkit-kde-1 printer-applet pulseaudio-module-bluetooth python-kde4 python-packagekit python-pyudev python-qt4 python-qt4-dbus python-sip python-uno qapt-batch quassel quassel-data rdesktop rekonq shared-desktop-ontologies software-properties-kde soprano-daemon system-config-printer-kde systemsettings uno-libs3 update-manager-kde ure usb-creator-kde userconfig virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common wodim xfonts-mathml && sudo apt-get install ubuntu-desktop
```

---

### Post by nos09 on 2011-07-10
> **koleoptero said:**
> In a terminal:

```
sudo apt-get remove akonadi-server akregator amarok amarok-common amarok-utils appmenu-gtk appmenu-qt apport-kde apturl-kde ark bluedevil cdparanoia cdrdao docbook-xsl dolphin dragonplayer dvd+rw-tools exiv2 freespacenotifier gdebi-core gdebi-kde gnupg-agent gnupg2 gpgsm growisofs gtk2-engines-oxygen gwenview ibus-qt4 icoutils jockey-kde k3b k3b-data kaddressbook kamera kate kcalc kde-config-gtk kde-config-touchpad kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-runtime kdebase-runtime-data kdebase-workspace kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdegames-card-data kdegraphics-libs-data kdegraphics-strigi-plugins kdelibs-bin kdelibs5-data kdelibs5-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdepasswd kdepim-groupware kdepim-kresources kdepim-runtime kdepim-strigi-plugins kdepim-wizards kdepimlibs-kio-plugins kdesudo kdm kdoctools kfind khelpcenter4 kinfocenter klipper kmag kmail kmix kmousetool knm-runtime knotes konsole kontact kopete kopete-message-indicator korganizer kpackagekit kpat kppp krdc krfb krosspython ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-debug-installer kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-firefox-installer kubuntu-konqueror-shortcuts kubuntu-netbook-default-settings kubuntu-notification-helper kvkbd kwalletmanager language-selector-kde libakonadi-contact4 libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4 libakonadiprotocolinternals1 libattica0 libaudio2 libbluedevil1 libboost-program-options1.42.0 libcln6 libclucene0ldbl libdbusmenu-qt2 libdebconf-kde0 libdiscid0 libdmtx0a libepub0 libexiv2-10 libflac++6 libgif4 libgpgme++2 libgpgme11 libgpod-common libgpod4 libgps19 libgraphite3 libhyphen0 libibus-qt1 libindicate-qt1 libiodbc2 libk3b6 libkabc4 libkatepartinterfaces4 libkblog4 libkcal4 libkcalcore4 libkcalutils4 libkcddb4 libkcmutils4 libkdcraw9 libkde3support4 libkdecorations4 libkdecore5 libkdegames5 libkdepim4 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4 libkemoticons4 libkephal4a libkexiv2-9 libkfile4 libkholidays4 libkhtml5 libkidletime4 libkimap4 libkimproxy4 libkio5 libkipi8 libkjsapi4 libkjsembed4 libkldap4 libkleo4 libkmediaplayer4 libkmime4 libknewstuff2-4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkonq5-templates libkonq5a libkontactinterface4 libkopete4 libkparts4 libkpgp4 libkpimidentities4 libkpimtextedit4 libkpimutils4 libkprintutils4 libkpty4 libkresources4 libkrosscore4 libksba8 libkscreensaver5 libksgrd4 libksieve4 libksignalplotter4 libktexteditor4 libktnef4 libktorrent-l10n libktorrent2 libkunitconversion4 libkutils4 libkwineffects1a libkworkspace4 libkxmlrpcclient4 liblastfm0 libmailtransport4 libmessagecore4 libmessagelist4 libmicroblog4 libmimelib4 libmpcdec6 libmsn0.3 libmtp8 libmusicbrainz3-6 libmysqlclient16 libmythes-1.2-0 libneon27-gnutls libnepomuk4 libnepomukquery4a libnepomukutils4 libntrack-qt4-1 libntrack0 libokularcore1 libpackagekit-glib2-14 libpackagekit-qt14 libphonon4 libplasma-geolocation-interface4 libplasma3 libplasmaclock4b libplasmagenericshell4 libpolkit-qt-1-1 libpoppler-qt4-3 libpowerdevilcore0 libprocesscore4b libprocessui4a libpth20 libqalculate5 libqapt-runtime libqapt1 libqca2 libqca2-plugin-ossl libqgpgme1 libqimageblitz4 libqjson0 libqt4-dbus libqt4-declarative libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns libqtassistantclient4 libqtcore4 libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml libqtwebkit4 libraptor1 librasqal2 librdf0 libreadline5 libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge libreoffice-impress libreoffice-kde libreoffice-math libreoffice-style-human libreoffice-style-oxygen libreoffice-writer libsolid4 libsolidcontrol4a libsolidcontrolifaces4a libsoprano4 libssh-4 libstlport4.6ldbl libstreamanalyzer0 libstreams0 libsyndication4 libtag-extras1 libtaskmanager4b libtextcat-data libtextcat0 libthreadweaver4 libvirtodbc0 libvncserver0 libweather-ion6 libzip1 mysql-client-core-5.1 mysql-common mysql-server-core-5.1 nepomukcontroller network-manager-pptp-kde ntrack-module-libnl-0 obexd-client odbcinst odbcinst1debian2 okular okular-extra-backends oxygen-cursor-theme oxygen-icon-theme oxygen-icon-theme-complete packagekit packagekit-backend-aptcc partitionmanager phonon phonon-backend-gstreamer pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-desktop plasma-netbook plasma-scriptengine-declarative plasma-scriptengine-javascript plasma-scriptengine-python plasma-widget-facebook plasma-widget-folderview plasma-widget-kimpanel plasma-widget-kimpanel-backend-ibus plasma-widget-menubar plasma-widget-message-indicator plasma-widget-networkmanagement plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace plymouth-theme-kubuntu-logo plymouth-theme-kubuntu-text polkit-kde-1 printer-applet pulseaudio-module-bluetooth python-kde4 python-packagekit python-pyudev python-qt4 python-qt4-dbus python-sip python-uno qapt-batch quassel quassel-data rdesktop rekonq shared-desktop-ontologies software-properties-kde soprano-daemon system-config-printer-kde systemsettings uno-libs3 update-manager-kde ure usb-creator-kde userconfig virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common wodim xfonts-mathml && sudo apt-get install ubuntu-desktop
```
output : ```
sudo] password for nos: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gdebi-kde is not installed, so not removed
Package jockey-kde is not installed, so not removed
Package kdepim-wizards is not installed, so not removed
Package pinentry-gtk2 is not installed, so not removed
Package kubuntu-desktop is not installed, so not removed
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libaccess-bridge-java : Depends: default-jre but it is not going to be installed or
                                  openjdk-6-jre but it is not going to be installed or
                                  sun-java6-jre but it is not going to be installed
E: Broken packages

```

---

### Post by Bucky Ball on 2011-07-10
Also, search Synaptics for kubuntu-desktop. That should remove plenty. Also search for 'kde' and remove what you find. 

Try running 'sudo apt-get autoremove', this may fix some of the broken packages (by removing the conflicting bits).

---

### Post by koleoptero on 2011-07-10
Well if a package has unmet dependencies then remove it, don't be afraid to.

EDIT: You shouldn't be afraid because the command I gave you will afterwards install ubuntu-desktop again if it was somehow removed, therefore the whole galore of packages ubuntu needs to work.

---

