---
title: "Trying to install KDE Plasma"
date: 2015-11-25
forum: Desktop Environments
---

### Post by simone21 on 2015-11-25
Hi all, I just updated my Xubuntu to 15.10, and I want back KDE env.
On the web i found this solution:
```
simone@xb:~$ sudo apt-get install plasma-desktop
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Il pacchetto plasma-desktop non ha versioni disponibili, ma è nominato da un altro
pacchetto. Questo potrebbe indicare che il pacchetto è mancante, obsoleto
oppure è disponibile solo all'interno di un'altra sorgente

E: **Il pacchetto "plasma-desktop" non ha candidati da installare**
```

but there is the error above. What I'm missing?

---

### Post by flocculant on 2015-11-25
I'd apt-get update and check again. It's in universe so make sure that's enabled - Software and Updates - 1st tab.

If you DO manage to install it be aware that installing plasma-desktop will install the following

```
baloo-kf5 bluedevil breeze breeze-cursor-theme breeze-icon-theme catdoc
  debconf-kde-data fonts-oxygen frameworkintegration icoutils kactivities
  kate-data katepart kde-cli-tools kde-cli-tools-data kde-config-gtk-style
  kde-config-sddm kde-runtime kde-runtime-data kde-style-breeze
  kde-style-breeze-qt4 kde-style-oxygen-qt5 kded5 kdelibs-bin kdelibs5-data
  kdelibs5-plugins kdesudo kdoctools kdoctools5 kgamma5 khelpcenter khotkeys
  khotkeys-data kinfocenter kinit kio kio-extras kio-extras-data kmenuedit
  kpackagelauncherqml kpackagetool5 kscreen ksshaskpass ksysguard
  ksysguard-data ksysguardd ktexteditor-data ktexteditor-katepart
  kubuntu-debug-installer kwalletmanager kwayland-data kwayland-integration
  kwin kwin-common kwin-data kwin-style-breeze kwin-x11 kwrited libattica0.4
  libcln6 libdbusmenu-qt2 libdbusmenu-qt5 libdebconf-kde1 libdlrestrictions1
  libdmtx0a libepub0 libexiv2-14 libfam0 libgit2-23 libgps21
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libhttp-parser2.1
  libjs-underscore libkactivities6 libkatepartinterfaces4 libkcmutils4
  libkde3support4 libkdeclarative5 libkdecorations2-5v5
  libkdecorations2private5v5 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5
  libkdnssd4 libkemoticons4 libkf5activities5
  libkf5activitiesexperimentalstats1 libkf5archive5 libkf5attica5
  libkf5auth-data libkf5auth5 libkf5baloo5 libkf5balooengine5
  libkf5bluezqt-data libkf5bluezqt6 libkf5bookmarks-data libkf5bookmarks5
  libkf5codecs-data libkf5codecs5 libkf5completion-data libkf5completion5
  libkf5config-bin libkf5config-data libkf5configcore5 libkf5configgui5
  libkf5configwidgets-data libkf5configwidgets5 libkf5coreaddons-data
  libkf5coreaddons5 libkf5crash5 libkf5dbusaddons-bin libkf5dbusaddons-data
  libkf5dbusaddons5 libkf5declarative-data libkf5declarative5 libkf5dnssd-data
  libkf5dnssd5 libkf5emoticons-bin libkf5emoticons-data libkf5emoticons5
  libkf5filemetadata-bin libkf5filemetadata-data libkf5filemetadata3
  libkf5globalaccel-bin libkf5globalaccel-data libkf5globalaccel5
  libkf5globalaccelprivate5 libkf5guiaddons5 libkf5i18n-data libkf5i18n5
  libkf5iconthemes-bin libkf5iconthemes-data libkf5iconthemes5 libkf5idletime5
  libkf5itemviews-data libkf5itemviews5 libkf5jobwidgets-data
  libkf5jobwidgets5 libkf5js5 libkf5jsembed-data libkf5jsembed5
  libkf5kcmutils-data libkf5kcmutils5 libkf5kdelibs4support-data
  libkf5kdelibs4support5 libkf5kdelibs4support5-bin libkf5khtml-bin
  libkf5khtml-data libkf5khtml5 libkf5kiocore5 libkf5kiofilewidgets5
  libkf5kiontlm5 libkf5kiowidgets5 libkf5networkmanagerqt6 libkf5newstuff-data
  libkf5newstuff5 libkf5notifications-data libkf5notifications5
  libkf5notifyconfig-data libkf5notifyconfig5 libkf5package-data
  libkf5package5 libkf5parts-data libkf5parts-plugins libkf5parts5
  libkf5people-data libkf5people5 libkf5peoplebackend5 libkf5peoplewidgets5
  libkf5plasma5 libkf5plasmaquick5 libkf5prison1 libkf5pty-data libkf5pty5
  libkf5quickaddons5 libkf5runner5 libkf5screen6 libkf5service-bin
  libkf5service-data libkf5service5 libkf5solid5 libkf5solid5-data
  libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5 libkf5style5
  libkf5su-bin libkf5su-data libkf5su5 libkf5sysguard-bin libkf5sysguard-data
  libkf5texteditor5 libkf5texteditor5-libjs-underscore libkf5textwidgets-data
  libkf5textwidgets5 libkf5threadweaver5 libkf5wallet-bin libkf5wallet-data
  libkf5wallet5 libkf5waylandclient5 libkf5waylandserver5 libkf5webkit5
  libkf5widgetsaddons-data libkf5widgetsaddons5 libkf5windowsystem-data
  libkf5windowsystem5 libkf5xmlgui-bin libkf5xmlgui-data libkf5xmlgui5
  libkf5xmlrpcclient-data libkf5xmlrpcclient5 libkfile4 libkfontinst5
  libkfontinstui5 libkhtml5 libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4
  libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpty4
  libkrosscore4 libksgrd7 libksignalplotter7 libktexteditor4
  libkwalletbackend5-5 libkwin4-effect-builtins1 libkwineffects6
  libkwinglutils6 libkwinxrenderutils6 libkworkspace5-5 libkxmlrpcclient4
  liblmdb0 libmuon libntrack-qt4-1 libntrack0 libopenobex1 liboxygenstyle5-5
  liboxygenstyleconfig5-5 libpackagekitqt5-0 libphonon4 libphonon4qt5-4
  libplasma-geolocation-interface5 libplasma3 libpolkit-qt-1-1
  libpolkit-qt5-1-1 libpoppler-qt5-1 libpowerdevilcore2 libpowerdevilui5
  libprocesscore7 libprocessui7 libqalculate5-data libqalculate5v5 libqapt3
  libqapt3-runtime libqca-qt5-2 libqca-qt5-2-plugins libqca2-plugins libqca2v5
  libqgsttools-p1 libqrencode3 libqt4-designer libqt4-qt3support libqt4-svg
  libqt5clucene5 libqt5concurrent5 libqt5designer5 libqt5designercomponents5
  libqt5help5 libqt5multimedia5 libqt5multimedia5-plugins
  libqt5multimediaquick-p5 libqt5multimediawidgets5 libqt5opengl5
  libqt5printsupport5 libqt5quickwidgets5 libqt5script5 libqt5sql5
  libqt5sql5-sqlite libqt5svg5 libqt5test5 libqt5waylandclient5 libqt5webkit5
  libqt5x11extras5 libqt5xml5 libqtwebkit4 libsolid4 libssh-4 libssh2-1
  libstreamanalyzer0v5 libstreams0v5 libtaskmanager5 libthreadweaver4
  libvoikko1 libweather-ion7 libxcb-composite0 libxcb-cursor0 libxcb-damage0
  libxcb-dpms0 libxcb-record0 libzip4 milou muon-common muon-discover
  muon-notifier muon-updater ntrack-module-libnl-0 obex-data-server
  orion-gtk-theme oxygen-icon-theme oxygen-sounds pam-kwallet4 pam-kwallet5
  phonon phonon-backend-gstreamer phonon-backend-gstreamer-common
  plasma-desktop-data plasma-framework plasma-pa
  plasma-scriptengine-javascript plasma-workspace polkit-kde-agent-1
  powerdevil powerdevil-data python-gobject python3-pyqt5 python3-sip
  qapt-batch qdbus-qt5 qml-module-org-kde-activities
  qml-module-org-kde-bluezqt qml-module-org-kde-draganddrop
  qml-module-org-kde-extensionplugin qml-module-org-kde-kcoreaddons
  qml-module-org-kde-kquickcontrols qml-module-org-kde-kquickcontrolsaddons
  qml-module-org-kde-kwindowsystem qml-module-org-kde-runnermodel
  qml-module-org-kde-solid qml-module-qtgraphicaleffects
  qml-module-qtmultimedia qml-module-qtquick-controls-styles-breeze
  qtdeclarative5-kf5declarative qtdeclarative5-kf5solid qttools5-dev-tools
  qtwayland5 sni-qt socat software-properties-kde sonnet-plugins
  systemsettings ttf-dejavu-core ttf-oxygen-font-family
  ubuntu-release-upgrader-qt user-manager
```

```
Need to get 192 MB of archives.
After this operation, 687 MB of additional disk space will be used.
```

Even if you use apt-get install --no-install-recommends to do so you'll get

```
baloo-kf5 breeze breeze-cursor-theme breeze-icon-theme fonts-oxygen
  frameworkintegration kactivities kde-cli-tools kde-cli-tools-data
  kde-style-breeze kde-style-breeze-qt4 kded5 kinit kio ktexteditor-data
  kwayland-data kwin-style-breeze libattica0.4 libcln6 libdbusmenu-qt2
  libdbusmenu-qt5 libdlrestrictions1 libdmtx0a libfam0 libgit2-23 libgps21
  libhttp-parser2.1 libjs-underscore libkdecorations2-5v5
  libkdecorations2private5v5 libkdecore5 libkdeui5 libkf5activities5
  libkf5activitiesexperimentalstats1 libkf5archive5 libkf5attica5
  libkf5auth-data libkf5auth5 libkf5baloo5 libkf5balooengine5
  libkf5bookmarks-data libkf5bookmarks5 libkf5codecs-data libkf5codecs5
  libkf5completion-data libkf5completion5 libkf5config-data libkf5configcore5
  libkf5configgui5 libkf5configwidgets-data libkf5configwidgets5
  libkf5coreaddons-data libkf5coreaddons5 libkf5crash5 libkf5dbusaddons-data
  libkf5dbusaddons5 libkf5declarative-data libkf5declarative5
  libkf5emoticons-data libkf5emoticons5 libkf5filemetadata-data
  libkf5filemetadata3 libkf5globalaccel-bin libkf5globalaccel-data
  libkf5globalaccel5 libkf5globalaccelprivate5 libkf5guiaddons5
  libkf5i18n-data libkf5i18n5 libkf5iconthemes-data libkf5iconthemes5
  libkf5idletime5 libkf5itemviews-data libkf5itemviews5 libkf5jobwidgets-data
  libkf5jobwidgets5 libkf5js5 libkf5jsembed-data libkf5jsembed5
  libkf5kcmutils-data libkf5kcmutils5 libkf5kdelibs4support-data
  libkf5kdelibs4support5 libkf5kiocore5 libkf5kiofilewidgets5 libkf5kiontlm5
  libkf5kiowidgets5 libkf5networkmanagerqt6 libkf5newstuff-data
  libkf5newstuff5 libkf5notifications-data libkf5notifications5
  libkf5notifyconfig-data libkf5notifyconfig5 libkf5package-data
  libkf5package5 libkf5parts-data libkf5parts5 libkf5people-data libkf5people5
  libkf5peoplebackend5 libkf5peoplewidgets5 libkf5plasma5 libkf5plasmaquick5
  libkf5prison1 libkf5pty-data libkf5pty5 libkf5quickaddons5 libkf5runner5
  libkf5screen6 libkf5service-bin libkf5service-data libkf5service5
  libkf5solid5 libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5
  libkf5sonnetui5 libkf5style5 libkf5su-data libkf5su5 libkf5sysguard-data
  libkf5texteditor5 libkf5texteditor5-libjs-underscore libkf5textwidgets-data
  libkf5textwidgets5 libkf5threadweaver5 libkf5wallet-data libkf5wallet5
  libkf5waylandclient5 libkf5waylandserver5 libkf5webkit5
  libkf5widgetsaddons-data libkf5widgetsaddons5 libkf5windowsystem-data
  libkf5windowsystem5 libkf5xmlgui-data libkf5xmlgui5 libkf5xmlrpcclient-data
  libkf5xmlrpcclient5 libkfontinst5 libkfontinstui5 libksgrd7
  libkwalletbackend5-5 libkworkspace5-5 liblmdb0 libpackagekitqt5-0
  libphonon4qt5-4 libplasma-geolocation-interface5 libpolkit-qt5-1-1
  libprocesscore7 libprocessui7 libqalculate5-data libqalculate5v5
  libqrencode3 libqt4-svg libqt5clucene5 libqt5concurrent5 libqt5designer5
  libqt5designercomponents5 libqt5help5 libqt5opengl5 libqt5printsupport5
  libqt5quickwidgets5 libqt5script5 libqt5sql5 libqt5svg5 libqt5webkit5
  libqt5x11extras5 libqt5xml5 libssh2-1 libtaskmanager5 libweather-ion7
  libxcb-composite0 libxcb-damage0 libxcb-record0 milou oxygen-icon-theme
  oxygen-sounds plasma-desktop-data plasma-framework plasma-workspace
  polkit-kde-agent-1 qdbus-qt5 qml-module-org-kde-activities
  qml-module-org-kde-draganddrop qml-module-org-kde-extensionplugin
  qml-module-org-kde-kcoreaddons qml-module-org-kde-kquickcontrols
  qml-module-org-kde-kquickcontrolsaddons qml-module-org-kde-kwindowsystem
  qml-module-org-kde-solid qml-module-qtgraphicaleffects
  qml-module-qtquick-controls-styles-breeze qtdeclarative5-kf5declarative
  qtdeclarative5-kf5solid qttools5-dev-tools ttf-oxygen-font-family
```

```
Need to get 128 MB of archives.
After this operation, 420 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
```

(That's from a 16.04 Xubuntu with PPAs and stuff installed - even some qt)

---

### Post by simone21 on 2015-11-25
Thanks, disabled repository were more than one.
I was trying to activate them by sources.list but without success. Now is working.

---

