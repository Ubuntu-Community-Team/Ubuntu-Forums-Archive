---
title: "Cannot load kde"
date: 2011-12-01
forum: Desktop Environments
---

### Post by mirons on 2011-12-01
Hi everybody. After updating to 11.10 I'm not able to load kde anymore. After I login with kdm the splash shows very slow, then I hear sound of kde starting, two errors and nothing else, the screen freezes and that's it. All other things of the installation seems to be right (I can even start kde software such as ark or okular in openbox), what I'd like is a way of viewing where the error is. I tried
```

xinit
startkde >> start.log

```
but nothing useful is shown. I even deleted .kde folder, still the error is not solved. I'm thinking about remove all kde and dependencies and reinstall just them, is it possible? Could someone provide a recursive list of all kde dependencies? Any more orthodox ideas?

---

### Post by Lampi on 2011-12-01
did you browse the usual logfiles for errors?

/var/log/syslog
/var/log/Xorg.0.log
$HOME/.xsession-errors

Do any of these give you a hint why the screen is freezing up?

---

### Post by kio_http on 2011-12-01
> **mirons said:**
> Hi everybody. After updating to 11.10 I'm not able to load kde anymore. After I login with kdm the splash shows very slow, then I hear sound of kde starting, two errors and nothing else, the screen freezes and that's it. All other things of the installation seems to be right (I can even start kde software such as ark or okular in openbox), what I'd like is a way of viewing where the error is. I tried
```

xinit
startkde >> start.log

```
but nothing useful is shown. I even deleted .kde folder, still the error is not solved. I'm thinking about remove all kde and dependencies and reinstall just them, is it possible? Could someone provide a recursive list of all kde dependencies? Any more orthodox ideas?

Hi, you can solve this with this method (2 commands)

```
sudo apt-get purge acpi-support acpid akonadi-backend-mysql akonadi-server akregator amarok amarok-common amarok-utils app-install-data app-install-data-partner appmenu-gtk appmenu-gtk3 appmenu-qt apport-kde apt-xapian-index apturl-common apturl-kde ark avahi-autoipd bluedevil bluez-alsa bluez-cups brltty c2esp cdparanoia cdrdao cups-bsd dc docbook-xsl dolphin dragonplayer dvd+rw-tools exiv2 foo2zjs freespacenotifier ghostscript-x gnupg-agent gnupg2 gpgsm growisofs gstreamer0.10-alsa gstreamer0.10-pulseaudio gstreamer0.10-qapt gtk2-engines-oxygen gwenview hplip hplip-cups hplip-data ibus-qt4 icoutils im-switch inputattach jockey-kde k3b k3b-data kaccessible kaddressbook kamera kate kate-data katepart kcalc kde-baseapps-bin kde-baseapps-data kde-config-gtk kde-config-touchpad kde-runtime kde-runtime-data kde-wallpapers-default kde-window-manager kde-workspace kde-workspace-bin kde-workspace-data kde-workspace-kgreet-plugins kde-zeroconf kdebase-runtime kdegames-card-data kdegraphics-strigi-analyzer kdelibs-bin kdelibs5-data kdelibs5-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdepasswd kdepim-groupware kdepim-kresources kdepim-runtime kdepim-strigi-plugins kdepim-wizards kdepimlibs-kio-plugins kdesudo kdm kdoctools kerneloops-daemon kfind khelpcenter4 kinfocenter klipper kmag kmail kmix kmousetool knotes konsole kontact kopete kopete-message-indicator korganizer kpat kppp ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-debug-installer kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-firefox-installer kubuntu-netbook-default-settings kubuntu-notification-helper kubuntu-web-shortcuts kvkbd kwalletmanager language-selector-kde lftp libakonadi-calendar4 libakonadi-contact4 libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4 libakonadiprotocolinternals1 libasound2-plugins libassuan0 libattica0 libbluedevil1 libboost-program-options1.46.1 libbrlapi0.5 libcalendarsupport4 libcanberra-pulse libcln6 libclucene0ldbl libcrypt-passwdmd5-perl libdbusmenu-qt2 libdebconf-kde0 libdlrestrictions1 libdmtx0a libepub0 libeventviews4 libexiv2-10 libfile-copy-recursive-perl libflac++6 libgadu3 libgpgme++2 libgps19 libgrantlee-core0 libhyphen0 libibus-qt1 libilmbase6 libincidenceeditorsng4 libindicate-qt1 libiodbc2 libk3b6 libkabc4 libkateinterfaces4 libkatepartinterfaces4 libkblog4 libkcal4 libkcalcore4 libkcalutils4 libkcddb4 libkcmutils4 libkde3support4 libkdecorations4 libkdecore5 libkdegames5a libkdepim4 libkdepimdbusinterfaces4 libkdesu5 libkdeui5 libkdewebkit5 libkdgantt2 libkdnssd4 libkemoticons4 libkephal4abi1 libkexiv2-10 libkexiv2-data libkfile4 libkholidays4 libkhtml5 libkidletime4 libkimap4 libkio5 libkipi-data libkipi8 libkjsapi4 libkjsembed4 libkldap4 libkleo4 libkmanagesieve4 libkmbox4 libkmediaplayer4 libkmime4 libknewstuff2-4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkonq-common libkonq5-templates libkonq5abi1 libkontactinterface4 libkopete4 libkparts4 libkpgp4 libkpimidentities4 libkpimtextedit4 libkpimutils4 libkprintutils4 libkpty4 libkresources4 libkrosscore4 libksba8 libkscreensaver5 libksgrd4 libksieve4 libksieveui4 libksignalplotter4 libktexteditor4 libktnef4 libktorrent-l10n libktorrent3 libkunitconversion4 libkwineffects1abi2 libkworkspace4 libkxmlrpcclient4 liblastfm0 libmailcommon4 libmailtransport4 libmessagecomposer4 libmessagecore4 libmessagelist4 libmessageviewer4 libmicroblog4 libmng1 libmpcdec6 libmsn0.3 libmuonprivate1 libmysqlclient16 libmythes-1.2-0 libnepomuk4 libnepomukquery4a libnepomukutils4 libntrack-qt4-1 libntrack0 libokularcore1 libopenexr6 libotr2 libphonon4 libplasma-geolocation-interface4 libplasma3 libplasmaclock4abi2 libplasmagenericshell4 libpolkit-qt-1-1 libpoppler-qt4-3 libprison0 libprocesscore4abi1 libprocessui4a libpulse-mainloop-glib0 libqalculate5 libqapt-runtime libqapt1 libqca2 libqca2-plugin-ossl libqgpgme1 libqimageblitz4 libqjson0 libqrencode3 libqt4-dbus libqt4-declarative libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns libqtassistantclient4 libqtcore4 libqtglib-2.0-0 libqtgstreamer-0.10-0 libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml libqtwebkit4 libraptor2-0 librasqal3 librdf0 libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge libreoffice-impress libreoffice-kde libreoffice-math libreoffice-style-human libreoffice-style-oxygen libreoffice-writer libsane-hpaio libsolid4 libsolidcontrol4abi2 libsolidcontrolifaces4abi2 libsoprano4 libspeechd2 libspeexdsp1 libssh-4 libstlport4.6ldbl libstreamanalyzer0 libstreams0 libsyndication4 libtag-extras1 libtaskmanager4abi2 libtemplateparser4 libtextcat-data libtextcat0 libthreadweaver4 libutempter0 libvirtodbc0 libweather-ion6 libxml2-utils libxp6 libyajl1 libzip1 mscompress muon muon-installer muon-notifier muon-updater mysql-client-core-5.1 mysql-common mysql-server-core-5.1 ntrack-module-libnl-0 odbcinst odbcinst1debian2 okular okular-extra-backends openprinting-ppds oxygen-cursor-theme oxygen-icon-theme oxygen-icon-theme-complete partitionmanager phonon phonon-backend-gstreamer pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-desktop plasma-netbook plasma-scriptengine-javascript plasma-scriptengine-python plasma-widget-facebook plasma-widget-folderview plasma-widget-kimpanel plasma-widget-kimpanel-backend-ibus plasma-widget-menubar plasma-widget-message-indicator plasma-widget-networkmanagement plasma-widgets-addons plasma-widgets-workspace plymouth-theme-kubuntu-logo plymouth-theme-kubuntu-text printer-applet ptouch-driver pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-x11 pulseaudio-utils pxljr python-imaging python-kde4 python-pexpect python-pyudev python-qt4 python-qt4-dbus python-sip python-uno qapt-batch qapt-deb-installer qdbus quassel quassel-data radeontool rastertosag-gdi rekonq rfkill rtkit sane-utils shared-desktop-ontologies software-properties-kde soprano-daemon splix syslinux syslinux-common system-config-printer-kde systemsettings toshset ttf-opensymbol uno-libs3 update-inetd update-manager-kde ure usb-creator-common usb-creator-kde userconfig virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common wodim xcursor-themes xfonts-mathml

```

Optional if you want the latest stable version of KDE see [this]("http://www.kubuntu.org/news/kde-sc-473")beofre the next step.

then do
```
sudo apt-get install kubuntu-desktop
```

---

