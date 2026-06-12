---
title: "Remove KDE?"
date: 2013-01-02
forum: Desktop Environments
---

### Post by Benjamindaines on 2013-01-02
I installed KDE by installing kde-standard, but how do I remove it now?  Is there a way to do it without manually finding out every package included in kde-standard and removing them one by one?

---

### Post by ibjsb4 on 2013-01-02
I know of this

[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

---

### Post by Benjamindaines on 2013-01-02
> **ibjsb4 said:**
> I know of this

[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

Tried that, finds some packages, but not others and just exists.  Doesn't prompt me to uninstall what it did find.

---

### Post by ibjsb4 on 2013-01-02
Up to some reverse engineering?

```
host@host:~$ sudo apt-get install kde-standard
[sudo] password for host: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  akonadi-backend-mysql akonadi-server akregator alsa-base alsa-utils ark
  docbook-xsl dolphin dragonplayer freespacenotifier gnupg-agent gnupg2 gpsd
  gstreamer0.10-alsa gstreamer0.10-plugins-good gstreamer0.10-x gwenview
  icoutils juk kaddressbook kate kate-data katepart kcalc kde-baseapps
  kde-baseapps-bin kde-baseapps-data kde-plasma-desktop kde-runtime
  kde-runtime-data kde-style-oxygen kde-wallpapers kde-wallpapers-default
  kde-window-manager kde-window-manager-common kde-workspace kde-workspace-bin
  kde-workspace-data kde-workspace-kgreet-plugins kdelibs-bin kdelibs5-data
  kdelibs5-plugins kdepasswd kdepim-runtime kdepimlibs-kio-plugins
  kdeplasma-addons kdm kdoctools kfind khelpcenter4 kinfocenter klipper kmail
  kmenuedit kmix knotes konq-plugins konqueror konqueror-nsplugins konsole
  kopete kopete-message-indicator korganizer kscreensaver kscreensaver-xsavers
  ksnapshot ksysguard ksysguardd kubuntu-debug-installer kwalletmanager kwrite
  libakonadi-calendar4 libakonadi-contact4 libakonadi-kabc4 libakonadi-kcal4
  libakonadi-kde4 libakonadi-kmime4 libakonadi-notes4
  libakonadiprotocolinternals1 libassuan0 libattica0.3 libavc1394-0
  libboost-program-options1.46.1 libcalendarsupport4 libcln6 libclucene0ldbl
  libdbusmenu-qt2 libdlrestrictions1 libdmtx0a libencode-locale-perl
  libeventviews4 libexiv2-11 libfile-basedir-perl libfile-desktopentry-perl
  libfile-listing-perl libfile-mimeinfo-perl libfont-afm-perl libgadu3 libgif4
  libgpgme++2 libgps20 libgrantlee-core0 libhtml-form-perl libhtml-format-perl
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl
  libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libiec61883-0
  libincidenceeditorsng4 libindicate-qt1 libio-socket-inet6-perl
  libio-socket-ssl-perl libjpeg-progs libjpeg-turbo-progs libkabc4
  libkactivities-bin libkactivities6 libkalarmcal2 libkateinterfaces4
  libkatepartinterfaces4 libkcal4 libkcalcore4 libkcalutils4 libkcmutils4
  libkde3support4 libkdeclarative5 libkdecorations4 libkdecore5 libkdepim4
  libkdepimdbusinterfaces4 libkdesu5 libkdeui5 libkdewebkit5 libkdgantt2
  libkdnssd4 libkemoticons4 libkephal4abi1 libkexiv2-10 libkexiv2-data
  libkfile4 libkholidays4 libkhtml5 libkidletime4 libkimap4 libkio5
  libkipi-data libkipi8 libkjsapi4 libkjsembed4 libkldap4 libkleo4
  libkmanagesieve4 libkmbox4 libkmediaplayer4 libkmime4 libknewstuff2-4
  libknewstuff3-4 libknotifyconfig4 libkntlm4 libkonq-common
  libkonq5-templates libkonq5abi1 libkonqsidebarplugin4a libkontactinterface4
  libkopete4 libkparts4 libkpgp4 libkpimidentities4 libkpimtextedit4
  libkpimutils4 libkprintutils4 libkpty4 libkresources4 libkrosscore4 libksba8
  libkscreensaver5 libksgrd4 libksieve4 libksieveui4 libksignalplotter4
  libktexteditor4 libktnef4 libkunitconversion4 libkwineffects1abi3
  libkwinglutils1 libkwinnvidiahack4 libkworkspace4abi1 liblwp-mediatypes-perl
  liblwp-protocol-https-perl libmailcommon4 libmailtools-perl
  libmailtransport4 libmarblewidget13 libmeanwhile1 libmessagecomposer4
  libmessagecore4 libmessagelist4 libmessageviewer4 libmicroblog4 libmsn0.3
  libnepomuk4 libnepomukdatamanagement4 libnepomukquery4a libnepomuksync4
  libnepomukutils4 libnet-http-perl libnet-ssleay-perl libntrack-qt4-1
  libntrack0 libokularcore1abi1 libotr2 libphonon4
  libplasma-geolocation-interface4 libplasma3 libplasmaclock4abi3
  libplasmagenericshell4 libpolkit-qt-1-1 libpoppler-qt4-3 libprison0
  libprocesscore4abi1 libprocessui4a libqalculate5 libqapt-runtime libqapt1
  libqca2 libqca2-plugin-ossl libqgpgme1 libqimageblitz4 libqrencode3
  libqt4-designer libqt4-qt3support libqt4-sql-sqlite libqt4-svg libqtwebkit4
  libsensors4 libshout3 libsocket6-perl libsolid4 libsolidcontrol4abi2
  libsolidcontrolifaces4abi2 libsoprano4 libspectre1 libssh-4
  libstreamanalyzer0 libstreams0 libsyndication4 libtag1-vanilla libtag1c2a
  libtaskmanager4abi3 libtemplateparser4 libthreadweaver4 libtidy-0.99-0
  libutempter0 libvirtodbc0 libwavpack1 libweather-ion6 libwww-perl
  libwww-robotrules-perl libxml2-utils libxss1 linux-sound-base marble-data
  marble-plugins mysql-client-core-5.5 mysql-server-core-5.5
  ntrack-module-libnl-0 odbcinst odbcinst1debian2 okular oxygen-cursor-theme
  oxygen-icon-theme phonon phonon-backend-gstreamer pinentry-gtk2 pinentry-qt4
  plasma-containments-addons plasma-dataengines-addons
  plasma-dataengines-workspace plasma-desktop plasma-desktopthemes-artwork
  plasma-runners-addons plasma-scriptengine-javascript
  plasma-wallpapers-addons plasma-widget-folderview plasma-widget-lancelot
  plasma-widget-message-indicator plasma-widget-networkmanagement
  plasma-widgets-addons plasma-widgets-workspace polkit-kde-1 qapt-batch
  shared-desktop-ontologies soprano-daemon sweeper systemsettings
  virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
  x11-xserver-utils xdg-utils xscreensaver-data xscreensaver-gl
Suggested packages:
  akonadi-backend-sqlite akonadi-backend-postgresql apmd alsa-oss oss-compat
  rar p7zip-full docbook-xsl-doc-html docbook-xsl-doc-pdf docbook-xsl-doc-text
  docbook-xsl-doc libsaxon-java libxalan2-java libxslthl-java
  docbook-xsl-saxon fop xalan dbtoepub kdesdk-dolphin-plugins ruby kompare
  gnupg-doc xloadimage gpsd-clients svgpart libterm-readline-gnu-perl
  libterm-readline-perl-perl k3b kdepim-kresources djvulibre-bin finger
  kde-plasma-netbook skanlite plasma-scriptengines kleopatra spamassassin
  bogofilter spambayes bsfilter crm114 clamav procmail kdeartwork-emoticons
  texlive-latex-base pi exiv2 libdata-dump-perl hspell libcrypt-ssleay-perl
  libotr2-bin libqca2-plugin-cyrus-sasl libqca2-plugin-gnupg libqt4-dev
  lm-sensors libspectre1-dbg libauthen-ntlm-perl okular-extra-backends
  texlive-binaries poppler-data jovie phonon-backend-vlc phonon-backend-xine
  phonon-backend-mplayer pinentry-doc network-manager-vpnc
  network-manager-openvpn nickle cairo-5c xorg-docs-core gvfs-bin xscreensaver
```

---

### Post by Benjamindaines on 2013-01-02
> **ibjsb4 said:**
> Up to some reverse engineering?

```
host@host:~$ sudo apt-get install kde-standard
[sudo] password for host: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  akonadi-backend-mysql akonadi-server akregator alsa-base alsa-utils ark
  docbook-xsl dolphin dragonplayer freespacenotifier gnupg-agent gnupg2 gpsd
  gstreamer0.10-alsa gstreamer0.10-plugins-good gstreamer0.10-x gwenview
  icoutils juk kaddressbook kate kate-data katepart kcalc kde-baseapps
  kde-baseapps-bin kde-baseapps-data kde-plasma-desktop kde-runtime
  kde-runtime-data kde-style-oxygen kde-wallpapers kde-wallpapers-default
  kde-window-manager kde-window-manager-common kde-workspace kde-workspace-bin
  kde-workspace-data kde-workspace-kgreet-plugins kdelibs-bin kdelibs5-data
  kdelibs5-plugins kdepasswd kdepim-runtime kdepimlibs-kio-plugins
  kdeplasma-addons kdm kdoctools kfind khelpcenter4 kinfocenter klipper kmail
  kmenuedit kmix knotes konq-plugins konqueror konqueror-nsplugins konsole
  kopete kopete-message-indicator korganizer kscreensaver kscreensaver-xsavers
  ksnapshot ksysguard ksysguardd kubuntu-debug-installer kwalletmanager kwrite
  libakonadi-calendar4 libakonadi-contact4 libakonadi-kabc4 libakonadi-kcal4
  libakonadi-kde4 libakonadi-kmime4 libakonadi-notes4
  libakonadiprotocolinternals1 libassuan0 libattica0.3 libavc1394-0
  libboost-program-options1.46.1 libcalendarsupport4 libcln6 libclucene0ldbl
  libdbusmenu-qt2 libdlrestrictions1 libdmtx0a libencode-locale-perl
  libeventviews4 libexiv2-11 libfile-basedir-perl libfile-desktopentry-perl
  libfile-listing-perl libfile-mimeinfo-perl libfont-afm-perl libgadu3 libgif4
  libgpgme++2 libgps20 libgrantlee-core0 libhtml-form-perl libhtml-format-perl
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl
  libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libiec61883-0
  libincidenceeditorsng4 libindicate-qt1 libio-socket-inet6-perl
  libio-socket-ssl-perl libjpeg-progs libjpeg-turbo-progs libkabc4
  libkactivities-bin libkactivities6 libkalarmcal2 libkateinterfaces4
  libkatepartinterfaces4 libkcal4 libkcalcore4 libkcalutils4 libkcmutils4
  libkde3support4 libkdeclarative5 libkdecorations4 libkdecore5 libkdepim4
  libkdepimdbusinterfaces4 libkdesu5 libkdeui5 libkdewebkit5 libkdgantt2
  libkdnssd4 libkemoticons4 libkephal4abi1 libkexiv2-10 libkexiv2-data
  libkfile4 libkholidays4 libkhtml5 libkidletime4 libkimap4 libkio5
  libkipi-data libkipi8 libkjsapi4 libkjsembed4 libkldap4 libkleo4
  libkmanagesieve4 libkmbox4 libkmediaplayer4 libkmime4 libknewstuff2-4
  libknewstuff3-4 libknotifyconfig4 libkntlm4 libkonq-common
  libkonq5-templates libkonq5abi1 libkonqsidebarplugin4a libkontactinterface4
  libkopete4 libkparts4 libkpgp4 libkpimidentities4 libkpimtextedit4
  libkpimutils4 libkprintutils4 libkpty4 libkresources4 libkrosscore4 libksba8
  libkscreensaver5 libksgrd4 libksieve4 libksieveui4 libksignalplotter4
  libktexteditor4 libktnef4 libkunitconversion4 libkwineffects1abi3
  libkwinglutils1 libkwinnvidiahack4 libkworkspace4abi1 liblwp-mediatypes-perl
  liblwp-protocol-https-perl libmailcommon4 libmailtools-perl
  libmailtransport4 libmarblewidget13 libmeanwhile1 libmessagecomposer4
  libmessagecore4 libmessagelist4 libmessageviewer4 libmicroblog4 libmsn0.3
  libnepomuk4 libnepomukdatamanagement4 libnepomukquery4a libnepomuksync4
  libnepomukutils4 libnet-http-perl libnet-ssleay-perl libntrack-qt4-1
  libntrack0 libokularcore1abi1 libotr2 libphonon4
  libplasma-geolocation-interface4 libplasma3 libplasmaclock4abi3
  libplasmagenericshell4 libpolkit-qt-1-1 libpoppler-qt4-3 libprison0
  libprocesscore4abi1 libprocessui4a libqalculate5 libqapt-runtime libqapt1
  libqca2 libqca2-plugin-ossl libqgpgme1 libqimageblitz4 libqrencode3
  libqt4-designer libqt4-qt3support libqt4-sql-sqlite libqt4-svg libqtwebkit4
  libsensors4 libshout3 libsocket6-perl libsolid4 libsolidcontrol4abi2
  libsolidcontrolifaces4abi2 libsoprano4 libspectre1 libssh-4
  libstreamanalyzer0 libstreams0 libsyndication4 libtag1-vanilla libtag1c2a
  libtaskmanager4abi3 libtemplateparser4 libthreadweaver4 libtidy-0.99-0
  libutempter0 libvirtodbc0 libwavpack1 libweather-ion6 libwww-perl
  libwww-robotrules-perl libxml2-utils libxss1 linux-sound-base marble-data
  marble-plugins mysql-client-core-5.5 mysql-server-core-5.5
  ntrack-module-libnl-0 odbcinst odbcinst1debian2 okular oxygen-cursor-theme
  oxygen-icon-theme phonon phonon-backend-gstreamer pinentry-gtk2 pinentry-qt4
  plasma-containments-addons plasma-dataengines-addons
  plasma-dataengines-workspace plasma-desktop plasma-desktopthemes-artwork
  plasma-runners-addons plasma-scriptengine-javascript
  plasma-wallpapers-addons plasma-widget-folderview plasma-widget-lancelot
  plasma-widget-message-indicator plasma-widget-networkmanagement
  plasma-widgets-addons plasma-widgets-workspace polkit-kde-1 qapt-batch
  shared-desktop-ontologies soprano-daemon sweeper systemsettings
  virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
  x11-xserver-utils xdg-utils xscreensaver-data xscreensaver-gl
Suggested packages:
  akonadi-backend-sqlite akonadi-backend-postgresql apmd alsa-oss oss-compat
  rar p7zip-full docbook-xsl-doc-html docbook-xsl-doc-pdf docbook-xsl-doc-text
  docbook-xsl-doc libsaxon-java libxalan2-java libxslthl-java
  docbook-xsl-saxon fop xalan dbtoepub kdesdk-dolphin-plugins ruby kompare
  gnupg-doc xloadimage gpsd-clients svgpart libterm-readline-gnu-perl
  libterm-readline-perl-perl k3b kdepim-kresources djvulibre-bin finger
  kde-plasma-netbook skanlite plasma-scriptengines kleopatra spamassassin
  bogofilter spambayes bsfilter crm114 clamav procmail kdeartwork-emoticons
  texlive-latex-base pi exiv2 libdata-dump-perl hspell libcrypt-ssleay-perl
  libotr2-bin libqca2-plugin-cyrus-sasl libqca2-plugin-gnupg libqt4-dev
  lm-sensors libspectre1-dbg libauthen-ntlm-perl okular-extra-backends
  texlive-binaries poppler-data jovie phonon-backend-vlc phonon-backend-xine
  phonon-backend-mplayer pinentry-doc network-manager-vpnc
  network-manager-openvpn nickle cairo-5c xorg-docs-core gvfs-bin xscreensaver
```

That's exactly what I don't want to do.

---

### Post by bellygrevios on 2013-01-03
I wouldn't be suprised if you already tried this but 
```
 sudo apt-get autoremove kde-standard 
```
would be the easiest way...

---

### Post by Benjamindaines on 2013-01-03
> **bellygrevios said:**
> I wouldn't be suprised if you already tried this but 
```
 sudo apt-get autoremove kde-standard 
```
would be the easiest way...

oh damn, that's exactly what I wanted.  Thanks.  I knew there had to be a way to uninstall a group, but I'm more familiar with yum then apt.

---

### Post by Benjamindaines on 2013-01-03
> **Benjamindaines said:**
> oh damn, that's exactly what I wanted.  Thanks.  I knew there had to be a way to uninstall a group, but I'm more familiar with yum then apt.

Actually, that's a lie.  It removes more than I want, including some gnome stuff and kernel headers :confused:

```
calligra-l10n-engb ekiga fonts-cantarell fuse-utils fuseiso gdebi gdebi-core
  glchess glines gnect gnibbles gnobots2 gnome-backgrounds gnome-core
  gnome-dictionary gnome-games gnome-icon-theme-extras gnome-nettool
  gnome-search-tool gnotravex gnotski gnuchess gnuchess-book gtali
  hamster-applet hamster-indicator iagno icedax inkscape k3b-data kde-standard
  kdevelop-l10n kdevelop-php-docs-l10n kdevelop-php-l10n lib32gcc1
  libbonoboui2-0 libbonoboui2-common libboost-iostreams1.49.0
  libboost-signals1.49.0 libc6-i386 libcapi20-3 libflac++6 libgc1c2
  libgdict-1.0-6 libgdict-common libgfortran3 libgnomecanvas2-0
  libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgpds0 libgsl0ldbl
  libgtkmm-2.4-1c2a liblapack3 liblapack3gf libmagick++5 libopal3.10.4
  libpt2.10.4 libqt4-webkit libunique-1.0-0 liferea liferea-data lightsoff
  linux-headers-3.5.0-17 menu-xdg perlmagick python-gnome2 python-numpy
  python-pyorbit python-uniconvertor python-wnck quadrapassel sound-juicer
  swell-foop

```

---

### Post by bellygrevios on 2013-01-04
> **Benjamindaines said:**
> Actually, that's a lie.  It removes more than I want, including some gnome stuff and kernel headers :confused:

```
calligra-l10n-engb ekiga fonts-cantarell fuse-utils fuseiso gdebi gdebi-core
  glchess glines gnect gnibbles gnobots2 gnome-backgrounds gnome-core
  gnome-dictionary gnome-games gnome-icon-theme-extras gnome-nettool
  gnome-search-tool gnotravex gnotski gnuchess gnuchess-book gtali
  hamster-applet hamster-indicator iagno icedax inkscape k3b-data kde-standard
  kdevelop-l10n kdevelop-php-docs-l10n kdevelop-php-l10n lib32gcc1
  libbonoboui2-0 libbonoboui2-common libboost-iostreams1.49.0
  libboost-signals1.49.0 libc6-i386 libcapi20-3 libflac++6 libgc1c2
  libgdict-1.0-6 libgdict-common libgfortran3 libgnomecanvas2-0
  libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgpds0 libgsl0ldbl
  libgtkmm-2.4-1c2a liblapack3 liblapack3gf libmagick++5 libopal3.10.4
  libpt2.10.4 libqt4-webkit libunique-1.0-0 liferea liferea-data lightsoff
  linux-headers-3.5.0-17 menu-xdg perlmagick python-gnome2 python-numpy
  python-pyorbit python-uniconvertor python-wnck quadrapassel sound-juicer
  swell-foop

```

alright reinstall KDE then do 
```
sudo apt-get remove KDE
```
instead of autoremove

---

