---
title: "how to install kde with gnome?"
date: 2019-05-01
forum: Desktop Environments
---

### Post by jape258 on 2019-05-01
Is there going to be any errors with getting the kde environment that will break gnome. 
I want to get kde is to try it out. it seems it may take time to get set up but i would like to see how long it might take me to do that for my self. is it also a good idea to do this in the first place?
and also how i would get it.

would one of the commands work? I just want the kde no other file manager, terminal or software center installed.

sudo aptitude install kubuntu-desktop

sudo apt-get install kde-minimal

thank you in advance for your help!

I currently have the default Ubuntu 18.04

---

### Post by DuckHook on 2019-05-01
Welcome to the forums, jape258.

Not at all recommended. When the time comes, you will find it impossible to unscramble that egg.

You might find [this sticky]("https://ubuntuforums.org/showthread.php?t=2415676") of interest. Skip down to the part where it explains why mixing DEs is **not** recommended.

If you nonetheless want to experiment with doing so, I recommend that you do so within a VM. Take a known good snapshot of the pristine default install first. Then you can roll back to it when (not if) you break your system.

---

### Post by jape258 on 2019-05-01
is it hard to set up the kde environment?

---

### Post by DuckHook on 2019-05-01
Not at all. You should read the sticky I linked to. It in turn links to how a bare KDE environment can be installed, where to find the Kubuntu ISO, or installing from a minimal ISO and adding only the KDE stuff you want.

Kubuntu is a nice DE. There isn't much to set up. If you are new to Linux, there will be something of a learning curve, but it's a shallow and&#8212;dare I say&#8212;friendly enough one. I would recommend that you run Kubuntu as a LiveUSB. Play with it until you feel comfortable and familiar with it. You don't need to actually overwrite your Gnome DE until you are completely satisfied that you truly like it better. There is also the previously mentioned option of running a full-fledged Kubuntu inside a VM, which also boxes it within its own jail and doesn't mix it with your bare-metal Gnome environment. Both ways work.

Remember to backup your important data!

---

### Post by DuckHook on 2019-05-01
In case you are still tempted to install Kubuntu on top of Gnome, my simulated install in a Gnome VM showed the following:```
The following NEW packages will be installed:
  accountwizard acpi-support acpid akonadi-backend-mysql akonadi-server akregator apport-kde
  apt-config-icons-hidpi apt-config-icons-large apt-config-icons-large-hidpi apt-xapian-index ark
  avahi-autoipd avahi-utils baloo-kf5 bluedevil bluez-cups breeze breeze-cursor-theme breeze-gtk-theme
  breeze-icon-theme ca-certificates-java cantata catdoc cdparanoia cdrdao cdrskin cryfs cryptsetup
  cryptsetup-bin cups cups-browsed cups-bsd cups-client cups-common cups-core-drivers cups-daemon
  cups-filters cups-filters-core-drivers cups-ipp-utils cups-ppdc cups-server-common dc debconf-kde-data
  default-jre default-jre-headless docbook-xml docbook-xsl dolphin drkonqi dvd+rw-tools efibootmgr
  ffmpegthumbs fonts-beng fonts-beng-extra fonts-dejavu fonts-dejavu-extra fonts-deva fonts-deva-extra
  fonts-font-awesome fonts-gargi fonts-gubbi fonts-gujr fonts-gujr-extra fonts-guru fonts-guru-extra
  fonts-hack fonts-hack-ttf fonts-indic fonts-kacst fonts-kacst-one fonts-kalapi fonts-khmeros-core
  fonts-knda fonts-lao fonts-lato fonts-liberation fonts-liberation2 fonts-lklug-sinhala
  fonts-lohit-beng-assamese fonts-lohit-beng-bengali fonts-lohit-deva fonts-lohit-gujr fonts-lohit-guru
  fonts-lohit-knda fonts-lohit-mlym fonts-lohit-orya fonts-lohit-taml fonts-lohit-taml-classical
  fonts-lohit-telu fonts-mlym fonts-nakula fonts-navilu fonts-noto fonts-noto-cjk fonts-noto-unhinted
  fonts-opensymbol fonts-orya fonts-orya-extra fonts-oxygen fonts-pagul fonts-sahadeva fonts-samyak-deva
  fonts-samyak-gujr fonts-samyak-mlym fonts-samyak-taml fonts-sarai fonts-sil-abyssinica fonts-sil-padauk
  fonts-smc fonts-smc-anjalioldlipi fonts-smc-chilanka fonts-smc-dyuthi fonts-smc-karumbi
  fonts-smc-keraleeyam fonts-smc-manjari fonts-smc-meera fonts-smc-rachana fonts-smc-raghumalayalamsans
  fonts-smc-suruma fonts-smc-uroob fonts-taml fonts-telu fonts-telu-extra fonts-thai-tlwg
  fonts-tibetan-machine fonts-tlwg-garuda fonts-tlwg-garuda-ttf fonts-tlwg-kinnari fonts-tlwg-kinnari-ttf
  fonts-tlwg-laksaman fonts-tlwg-laksaman-ttf fonts-tlwg-loma fonts-tlwg-loma-ttf fonts-tlwg-mono
  fonts-tlwg-mono-ttf fonts-tlwg-norasi fonts-tlwg-norasi-ttf fonts-tlwg-purisa fonts-tlwg-purisa-ttf
  fonts-tlwg-sawasdee fonts-tlwg-sawasdee-ttf fonts-tlwg-typewriter fonts-tlwg-typewriter-ttf
  fonts-tlwg-typist fonts-tlwg-typist-ttf fonts-tlwg-typo fonts-tlwg-typo-ttf fonts-tlwg-umpush
  fonts-tlwg-umpush-ttf fonts-tlwg-waree fonts-tlwg-waree-ttf frameworkintegration freepats freerdp-x11
  fwupd fwupdate fwupdate-signed gconf-service gconf-service-backend gconf2-common gdb gdbserver gnupg2
  go-mtpfs growisofs gstreamer-qapt gwenview hplip hplip-data icoutils ieee-data java-common
  javascript-common k3b k3b-data kaccounts-integration kaccounts-providers kactivities-bin kactivitymanagerd
  kaddressbook kamera kate kate5-data kcalc kde-cli-tools kde-cli-tools-data kde-config-gtk-style
  kde-config-gtk-style-preview kde-config-mailtransport kde-config-screenlocker kde-config-sddm
  kde-config-whoopsie kde-runtime kde-runtime-data kde-spectacle kde-style-breeze kde-style-breeze-qt4
  kde-style-oxygen-qt5 kdeconnect kded5 kdegraphics-thumbnailers kdelibs-bin kdelibs5-data kdelibs5-plugins
  kdenetwork-filesharing kdepim-addons kdepim-runtime kdepim-themeeditors kdeplasma-addons-data kdialog
  kdoctools kdoctools5 kerneloops kf5-kdepim-apps-libs-data kf5-messagelib-data kgamma5 khelpcenter khotkeys
  khotkeys-data kimageformat-plugins kinfocenter kinit kio kio-audiocd kio-extras kio-extras-data kio-gdrive
  kio-ldap kio-sieve kleopatra kmail kmenuedit knotes konsole konsole-kpart kontact konversation
  konversation-data korganizer kpackagelauncherqml kpackagetool5 krdc kross kscreen ksshaskpass ksysguard
  ksysguard-data ksysguardd ksystemlog ktexteditor-data ktexteditor-katepart ktnef ktorrent ktorrent-data
  kubuntu-desktop kubuntu-driver-manager kubuntu-notification-helper kubuntu-settings-desktop
  kubuntu-wallpapers-bionic kubuntu-web-shortcuts kwalletmanager kwayland-data kwayland-integration kwin
  kwin-addons kwin-common kwin-data kwin-style-breeze kwin-x11 kwrited liba52-0.7.4 libabw-0.1-1
  libaccounts-glib0 libaccounts-qt5-1 libadplug-2.2.1-0v5 libaio1 libao-common libao4 libappstreamqt2
  libaribb24-0 libart-2.0-2 libatk-wrapper-java libatk-wrapper-java-jni libattica0.4 libaudio2 libaudiofile1
  libbabeltrace1 libbasicusageenvironment1 libbinio1v5 libboost-date-time1.65.1 libboost-filesystem1.65.1
  libboost-iostreams1.65.1 libboost-locale1.65.1 libburn4 libc-ares2 libc6-dbg libcc1-0 libcddb2
  libcdr-0.1-1 libcfitsio5 libchm1 libcln6 libclucene-contribs1v5 libclucene-core1v5 libcmis-0.5-5v5
  libcolamd2 libcolorcorrect5 libcrypto++6 libcupscgi1 libcupsmime1 libcupsppdc1 libcurl4 libdbusmenu-qt2
  libdbusmenu-qt5-2 libdc1394-22 libdca0 libdebconf-kde1 libdlrestrictions1 libdmtx0a libdolphinvcs5
  libdvbpsi10 libdvdnav4 libdvdread4 libdw1 libe-book-0.1-1 libebml4v5 libebur128-1 libeditorconfig0
  libefiboot1 libefivar1 libel-api-java libeot0 libepub0 libepubgen-0.1-1 libetonyek-0.1-1 libevent-2.1-6
  libexttextcat-2.0-0 libexttextcat-data libfaad2 libfakekey0 libfam0 libflac++6v5 libfluidsynth1
  libfontembed1 libfreehand-0.1-1 libfreerdp-cache1.1 libfreerdp-client1.1 libfreerdp-codec1.1
  libfreerdp-common1.1.0 libfreerdp-core1.1 libfreerdp-crypto1.1 libfreerdp-gdi1.1 libfreerdp-locale1.1
  libfreerdp-plugins-standard libfreerdp-primitives1.1 libfreerdp-rail1.1 libfreerdp-utils1.1 libfwup1
  libgconf-2-4 libgit2-26 libgpgme++2v5 libgpgmepp6 libgps23 libgrantlee-templates5
  libgrantlee-textdocument5 libgroupsock8 libgutenprint2 libhfstospell9 libhpmud0 libhsqldb1.8.0-java
  libhttp-parser2.7.1 libical2 libid3tag0 libiso9660-10 libjs-jquery libjs-underscore libjsp-api-java
  libk3b7 libk3b7-extracodecs libkaccounts1 libkactivities6 libkate1 libkcmutils4 libkde3support4
  libkdeclarative5 libkdecorations2-5v5 libkdecorations2private5v5 libkdecore5 libkdesu5 libkdeui5
  libkdewebkit5 libkdnssd4 libkemoticons4 libkf5activities5 libkf5activitiesstats1 libkf5akonadiagentbase5
  libkf5akonadicalendar-data libkf5akonadicalendar5abi2 libkf5akonadicontact-data libkf5akonadicontact5abi1
  libkf5akonadicore-bin libkf5akonadicore5abi1 libkf5akonadimime-data libkf5akonadimime5
  libkf5akonadinotes-data libkf5akonadinotes5 libkf5akonadiprivate5 libkf5akonadisearch-bin
  libkf5akonadisearch-data libkf5akonadisearch-plugins libkf5akonadisearchcore5 libkf5akonadisearchdebug5
  libkf5akonadisearchpim5 libkf5akonadisearchxapian5 libkf5akonadiwidgets5 libkf5alarmcalendar-data
  libkf5alarmcalendar5abi1 libkf5archive5 libkf5attica5 libkf5auth-data libkf5auth5 libkf5baloo5
  libkf5balooengine5 libkf5baloowidgets-bin libkf5baloowidgets-data libkf5baloowidgets5 libkf5bluezqt-data
  libkf5bluezqt6 libkf5bookmarks-data libkf5bookmarks5 libkf5calendarcore5abi1 libkf5calendarevents5
  libkf5calendarsupport-data libkf5calendarsupport5abi1 libkf5calendarutils-bin libkf5calendarutils-data
  libkf5calendarutils5abi1 libkf5cddb-data libkf5cddb5 libkf5codecs-data libkf5codecs5
  libkf5compactdisc-data libkf5compactdisc5 libkf5completion-data libkf5completion5 libkf5config-bin
  libkf5config-data libkf5configcore5 libkf5configgui5 libkf5configwidgets-data libkf5configwidgets5
  libkf5contacteditor-data libkf5contacteditor5 libkf5contacts-data libkf5contacts5 libkf5coreaddons-data
  libkf5coreaddons5 libkf5crash5 libkf5dbusaddons-bin libkf5dbusaddons-data libkf5dbusaddons5
  libkf5declarative-data libkf5declarative5 libkf5dnssd-data libkf5dnssd5 libkf5doctools5
  libkf5emoticons-bin libkf5emoticons-data libkf5emoticons5 libkf5eventviews-data libkf5eventviews5
  libkf5filemetadata-bin libkf5filemetadata-data libkf5filemetadata3 libkf5followupreminder5
  libkf5globalaccel-bin libkf5globalaccel-data libkf5globalaccel5 libkf5globalaccelprivate5
  libkf5grantleetheme-data libkf5grantleetheme-plugins libkf5grantleetheme5 libkf5gravatar-data
  libkf5gravatar5 libkf5guiaddons5 libkf5holidays-data libkf5holidays5 libkf5i18n-data libkf5i18n5
  libkf5iconthemes-bin libkf5iconthemes-data libkf5iconthemes5 libkf5identitymanagement-data
  libkf5identitymanagement5abi1 libkf5idletime5 libkf5imap-data libkf5imap5 libkf5incidenceeditor-bin
  libkf5incidenceeditor-data libkf5incidenceeditor5abi2 libkf5itemmodels5 libkf5itemviews-data
  libkf5itemviews5 libkf5jobwidgets-data libkf5jobwidgets5 libkf5js5 libkf5jsapi5 libkf5jsembed-data
  libkf5jsembed5 libkf5kaddressbookgrantlee5 libkf5kaddressbookimportexport5 libkf5kcmutils-data
  libkf5kcmutils5 libkf5kdcraw5 libkf5kdelibs4support-data libkf5kdelibs4support5 libkf5kdelibs4support5-bin
  libkf5kdepimdbusinterfaces5 libkf5kexiv2-15.0.0 libkf5khtml-bin libkf5khtml-data libkf5khtml5
  libkf5kiocore5 libkf5kiofilewidgets5 libkf5kiogui5 libkf5kiontlm5 libkf5kiowidgets5 libkf5kipi-data
  libkf5kipi32.0.0 libkf5kirigami2-5 libkf5kmanagesieve5 libkf5kontactinterface-data libkf5kontactinterface5
  libkf5krosscore5 libkf5krossui5 libkf5ksieve-data libkf5ksieve5 libkf5ksieveui5 libkf5ldap-data
  libkf5ldap5 libkf5libkdepim-data libkf5libkdepim-plugins libkf5libkdepim5abi2 libkf5libkdepimakonadi5
  libkf5libkleo5abi1 libkf5mailcommon-plugins libkf5mailcommon5abi4 libkf5mailimporter-data
  libkf5mailimporter5abi1 libkf5mailimporterakonadi5 libkf5mailtransport-data libkf5mailtransport5abi2
  libkf5mailtransportakonadi5 libkf5mbox5 libkf5messagecomposer5abi2 libkf5messagecore5abi2
  libkf5messagelist5abi1 libkf5messageviewer-plugins libkf5messageviewer5abi4 libkf5mime-data
  libkf5mime5abi2 libkf5mimetreeparser5abi2 libkf5modemmanagerqt6 libkf5networkmanagerqt6
  libkf5newstuff-data libkf5newstuff5 libkf5newstuffcore5 libkf5notifications-data libkf5notifications5
  libkf5notifyconfig-data libkf5notifyconfig5 libkf5package-data libkf5package5 libkf5parts-data
  libkf5parts-plugins libkf5parts5 libkf5people-data libkf5people5 libkf5peoplebackend5 libkf5peoplewidgets5
  libkf5pimcommon-plugins libkf5pimcommon5abi3 libkf5pimcommonakonadi5 libkf5pimtextedit-data
  libkf5pimtextedit5abi2 libkf5plasma5 libkf5plasmaquick5 libkf5plotting5 libkf5prison5 libkf5pty-data
  libkf5pty5 libkf5purpose-bin libkf5purpose5 libkf5quickaddons5 libkf5runner5 libkf5sane-data libkf5sane5
  libkf5screen-bin libkf5screen7 libkf5sendlater5 libkf5service-bin libkf5service-data libkf5service5
  libkf5solid5 libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5 libkf5style5
  libkf5su-bin libkf5su-data libkf5su5 libkf5syndication5 libkf5syntaxhighlighting-data
  libkf5syntaxhighlighting5 libkf5sysguard-bin libkf5sysguard-data libkf5templateparser5abi2
  libkf5texteditor5 libkf5texteditor5-libjs-underscore libkf5textwidgets-data libkf5textwidgets5
  libkf5threadweaver5 libkf5tnef-data libkf5tnef5 libkf5unitconversion-data libkf5unitconversion5
  libkf5wallet-bin libkf5wallet-data libkf5wallet5 libkf5waylandclient5 libkf5waylandserver5
  libkf5webengineviewer5abi3 libkf5webkit5 libkf5widgetsaddons-data libkf5widgetsaddons5
  libkf5windowsystem-data libkf5windowsystem5 libkf5xmlgui-bin libkf5xmlgui-data libkf5xmlgui5
  libkf5xmlrpcclient-data libkf5xmlrpcclient5 libkfile4 libkfontinst5 libkfontinstui5 libkgantt2
  libkgantt2-l10n libkhtml5 libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4 libknewstuff3-4
  libknotifyconfig4 libkntlm4 libkolabxml1v5 libkonq-common libkonq5-templates libkparts4 libkpimgapi-data
  libkpimgapicalendar5 libkpimgapicontacts5 libkpimgapicore5 libkpimgapidrive5 libkpimgapitasks5
  libkpimimportwizard5 libkpimkdav-data libkpimkdav5 libkpimsmtp5 libkpmcore7 libkpty4 libkrosscore4
  libkscreenlocker5 libksgrd7 libksignalplotter7 libktexteditor4 libktorrent-l10n libktorrent6 libkubuntu1
  libkwalletbackend5-5 libkwin4-effect-builtins1 libkwineffects11 libkwinglutils11 libkwinxrenderutils11
  libkworkspace5-5 libkxmlrpcclient4 liblangtag-common liblangtag1 liblcms2-utils liblivemedia62 liblmdb0
  liblouis-data liblouis14 liblouisutdml-bin liblouisutdml-data liblouisutdml8 libmad0 libmarkdown2
  libmatroska6v5 libmhash2 libmicrodns0 libmikmod3 libminizip1 libmjpegutils-2.1-0 libmms0 libmng2
  libmodplug1 libmpcdec6 libmpdclient2 libmpeg2-4 libmspub-0.1-1 libmwaw-0.3-3 libmysqlclient20
  libmythes-1.2-0 libnfs11 libnl-route-3-200 libntrack-qt4-1 libntrack0 libodfgen-0.1-1 libokular5core8
  libopenal-data libopenal1 libopenconnect5 libopencore-amrnb0 libopencore-amrwb0 libopenmpt-modplug1
  liborcus-0.13-0 liboxygenstyle5-5 liboxygenstyleconfig5-5 libpackagekitqt5-1 libpagemaker-0.0-0
  libpam-kwallet-common libpam-kwallet4 libpam-kwallet5 libperl4-corelibs-perl libphonon4 libphonon4qt5-4
  libplacebo4 libplasma-geolocation-interface5 libplasma3 libpolkit-qt-1-1 libpolkit-qt5-1-1
  libpoppler-qt5-1 libpowerdevilcore2 libpowerdevilui5 libprocesscore7 libprocessui7 libprotobuf-lite10
  libproxy-tools libqalculate6 libqalculate6-data libqapt3 libqapt3-runtime libqca-qt5-2
  libqca-qt5-2-plugins libqca2 libqca2-plugins libqgpgme7 libqgsttools-p1 libqmobipocket2 libqpdf21
  libqrencode3 libqt4-dbus libqt4-declarative libqt4-designer libqt4-network libqt4-opengl libqt4-qt3support
  libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-xml libqt4-xmlpatterns libqt5concurrent5
  libqt5designer5 libqt5help5 libqt5multimedia5 libqt5multimedia5-plugins libqt5multimediaquick-p5
  libqt5multimediawidgets5 libqt5opengl5 libqt5positioning5 libqt5printsupport5 libqt5qml5 libqt5quick5
  libqt5quickcontrols2-5 libqt5quicktemplates2-5 libqt5quickwidgets5 libqt5script5 libqt5sensors5 libqt5sql5
  libqt5sql5-mysql libqt5sql5-sqlite libqt5test5 libqt5texttospeech5 libqt5waylandclient5
  libqt5waylandcompositor5 libqt5webchannel5 libqt5webengine-data libqt5webengine5 libqt5webenginecore5
  libqt5webenginewidgets5 libqt5webkit5 libqt5x11extras5 libqt5xml5 libqt5xmlpatterns5 libqtcore4 libqtdbus4
  libqtgui4 libqtwebkit4 libquicktime2 libraptor2-0 librasqal3 libraw16 librdf0 libre2-4
  libreoffice-avmedia-backend-gstreamer libreoffice-base libreoffice-base-core libreoffice-base-drivers
  libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-impress
  libreoffice-java-common libreoffice-kde libreoffice-kde4 libreoffice-math libreoffice-sdbc-hsqldb
  libreoffice-style-breeze libreoffice-style-galaxy libreoffice-style-oxygen libreoffice-style-tango
  libreoffice-writer libresid-builder0c2a librevenge-0.0-0 libroar2 libruby2.5 libsane-hpaio libscim8v5
  libsdl-image1.2 libsdl1.2debian libsdl2-2.0-0 libservlet-api-java libservlet3.1-java libsidplay2
  libsidplayfp4 libsignon-extension1 libsignon-plugins-common1 libsignon-qt5-1 libsmbios-c2 libsndio6.1
  libsnmp-base libsnmp30 libsolid4 libsox-fmt-alsa libsox-fmt-base libsox3 libssh-4 libssh2-1 libstoken1
  libstreamanalyzer0v5 libstreams0v5 libsuitesparseconfig5 libtag-extras1 libtaskmanager6 libthreadweaver4
  libtomcrypt1 libtommath1 libupnp6 libusageenvironment3 libuv1 libva-wayland2 libvcdinfo0 libvisio-0.1-1
  libvlc-bin libvlc5 libvlccore9 libvncclient1 libvoikko1 libvulkan1 libweather-ion7 libwebsocket-api-java
  libwildmidi-config libwildmidi2 libwinpr-crt0.1 libwinpr-dsparse0.1 libwinpr-environment0.1
  libwinpr-file0.1 libwinpr-handle0.1 libwinpr-heap0.1 libwinpr-input0.1 libwinpr-interlocked0.1
  libwinpr-library0.1 libwinpr-path0.1 libwinpr-pool0.1 libwinpr-registry0.1 libwinpr-rpc0.1
  libwinpr-sspi0.1 libwinpr-synch0.1 libwinpr-sysinfo0.1 libwinpr-thread0.1 libwinpr-utils0.1 libwpd-0.10-10
  libwpg-0.3-3 libwps-0.4-4 libxcb-composite0 libxcb-cursor0 libxcb-damage0 libxcb-dpms0 libxcb-record0
  libxerces-c3.2 libxfreerdp-client1.1 libxml2-utils libxmlsec1 libxmlsec1-nss libyajl2 libzip4 libzzip-0-13
  lp-solve mbox-importer media-player-info memtest86+ milou mpd mscompress muon mysql-client-core-5.7
  mysql-common mysql-server-core-5.7 nodejs nodejs-doc ntrack-module-libnl-0 okular okular-extra-backends
  openjdk-11-jre openjdk-11-jre-headless oxygen-icon-theme oxygen-sounds oxygen5-icon-theme paperkey
  partitionmanager pastebinit pavucontrol-qt pavucontrol-qt-l10n pcmciautils phonon phonon-backend-gstreamer
  phonon-backend-gstreamer-common phonon4qt5 phonon4qt5-backend-gstreamer phonon4qt5-backend-vlc
  pim-data-exporter pim-sieve-editor pinentry-qt plasma-dataengines-addons plasma-desktop
  plasma-desktop-data plasma-discover plasma-discover-common plasma-framework plasma-integration
  plasma-look-and-feel-org-kde-breezedark-desktop plasma-nm plasma-pa plasma-runners-addons
  plasma-scriptengine-javascript plasma-vault plasma-wallpapers-addons plasma-widgets-addons
  plasma-workspace plymouth-theme-kubuntu-logo plymouth-theme-kubuntu-text policykit-desktop-privileges
  polkit-kde-agent-1 poppler-utils powerdevil powerdevil-data print-manager printer-driver-brlaser
  printer-driver-c2esp printer-driver-foo2zjs printer-driver-foo2zjs-common printer-driver-gutenprint
  printer-driver-hpcups printer-driver-m2300w printer-driver-min12xxw printer-driver-postscript-hp
  printer-driver-ptouch printer-driver-pxljr printer-driver-sag-gdi printer-driver-splix
  pulseaudio-module-gconf python-dbus python-gi python-qt4-dbus python3-dbus.mainloop.pyqt5 python3-olefile
  python3-pexpect python3-pil python3-ptyprocess python3-pyqt5 python3-renderpm python3-reportlab
  python3-reportlab-accel python3-sip python3-uno python3-xapian qapt-batch qapt-deb-installer qdbus
  qdbus-qt5 qml-module-org-kde-activities qml-module-org-kde-bluezqt qml-module-org-kde-draganddrop
  qml-module-org-kde-extensionplugin qml-module-org-kde-kcm qml-module-org-kde-kconfig
  qml-module-org-kde-kcoreaddons qml-module-org-kde-kholidays qml-module-org-kde-kio
  qml-module-org-kde-kirigami2 qml-module-org-kde-kquickcontrols qml-module-org-kde-kquickcontrolsaddons
  qml-module-org-kde-kwindowsystem qml-module-org-kde-newstuff qml-module-org-kde-purpose
  qml-module-org-kde-qqc2desktopstyle qml-module-org-kde-runnermodel qml-module-org-kde-solid
  qml-module-qt-labs-folderlistmodel qml-module-qt-labs-settings qml-module-qtgraphicaleffects
  qml-module-qtmultimedia qml-module-qtqml-models2 qml-module-qtquick-controls
  qml-module-qtquick-controls-styles-breeze qml-module-qtquick-controls2 qml-module-qtquick-dialogs
  qml-module-qtquick-layouts qml-module-qtquick-privatewidgets qml-module-qtquick-templates2
  qml-module-qtquick-virtualkeyboard qml-module-qtquick-window2 qml-module-qtquick-xmllistmodel
  qml-module-qtquick2 qml-module-qtwebengine qml-module-qtwebkit qml-module-ubuntu-onlineaccounts qpdf
  qt-at-spi qt5-image-formats-plugins qtchooser qtcore4-l10n qtdeclarative5-qtquick2-plugin
  qtspeech5-flite-plugin qtvirtualkeyboard-plugin qtwayland5 rake ruby ruby-did-you-mean ruby-minitest
  ruby-net-telnet ruby-power-assert ruby-test-unit ruby2.5 rubygems-integration sbsigntool sddm
  sddm-theme-breeze secureboot-db sgml-base sgml-data signon-kwallet-extension signon-plugin-oauth2
  signon-plugin-password signon-ui-service signon-ui-x11 signond skanlite sni-qt socat
  software-properties-kde sonnet-plugins sox sshfs ssl-cert system-config-printer systemsettings transcode
  transcode-doc ttf-ubuntu-font-family twolame ubuntu-release-upgrader-qt uno-libs3 ure user-manager
  vcdimager vlc vlc-bin vlc-data vlc-l10n vlc-plugin-base vlc-plugin-notify vlc-plugin-qt vlc-plugin-samba
  vlc-plugin-skins2 vlc-plugin-video-output vlc-plugin-video-splitter vlc-plugin-visualization whoopsie
  wodim xdg-desktop-portal-kde xml-core

``````
0 upgraded, **[COLOR="#B22222"]1118 newly installed[/COLOR]**, 0 to remove and 0 not upgraded.

```
It will drag in **over a thousand** dependencies.

That is a mess that you simply *do **not** want* on your system.

---

### Post by jape258 on 2019-05-02
thank you for your help

---

### Post by SeijiSensei on 2019-05-02
I second the advice of running Kubuntu in a virtual machine.  I suggest installing VirtualBox from the repositories 

```
sudo apt update && sudo apt install virtualbox
```

Next download an [ISO image of Kubuntu 18.04]("http://cdimage.ubuntu.com/kubuntu/bionic/daily-live/current/bionic-desktop-amd64.iso") (or, if you want, [19.04]("http://cdimage.ubuntu.com/kubuntu/releases/disco/release/kubuntu-19.04-desktop-amd64.iso") which runs fine here)

Now open the VirtualBox manager and create a new virtual machine. You'll be asked some basic questions that should have pretty obvious answers.  Accept the defaults for now.

When VB asks for the installation medium, point to the downloaded ISO file.  When you're finished, you'll have an brand-new Kubuntu desktop running on top of your existing Ubuntu 18.04 desktop.

If you find you like using VirtualBox, I suggest [following the instructions here]("https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions") to download the software from Oracle's repository and keep it up-to-date.  Following this procedure will automatically replace the version installed from the Ubuntu repositories with the version at Oracle.

---

### Post by jape258 on 2019-05-02
is there a kubuntu guide on how to set up the environment to fit me? also i have put kubuntu in virtual box but the resolution is messed up. is there a setting in virtual box or in the kubuntu its self to fix it? windows shows the monitor i have virtual box set to as being 1440 x 900.

---

### Post by DuckHook on 2019-05-02
There are few Kubuntu guides but lots of general Linux guides. A good place to start is the link in my sig: Resources for Newcomers.

More significantly, now that you have Kubuntu in your VM, take a snapshot of it so that you can always roll back to it, and then go exploring. Discover those settings for yourself. It's pretty cool. You can break Kubuntu all you want and always get back to your pristine install. There are very few tickets in life that invite us on a journey where we can go nuts. This is one of them.

[LIST]
[*]This is [Kubuntu's home page]("https://kubuntu.org/"). You can link to their Feature Tour from there.
[*]This is the [Kubuntu Wiki]("https://wiki.kubuntu.org/KubuntuDesktopGuide"). Explore.
[*]This is the ancient [Kubuntu Desktop guide]("https://help.ubuntu.com/kubuntu/desktopguide/C/index.html"). It is woefully out of date, but the basics haven't changed although the DE most certainly has.
[/LIST]
Your restricted VM resolution is likely the result of you not installing VirtualBox's Guest Additions. [Instructions for doing so are here]("https://askubuntu.com/questions/22743/how-do-i-install-guest-additions-in-a-virtualbox-vm").

If you still have problems getting VBox properly configured, post a separate thread in the Virtualisation subforum asking for help there.

---

