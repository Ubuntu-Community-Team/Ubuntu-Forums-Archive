---
title: "Not able to install - No partitions shown"
date: 2008-12-17
forum: General Help
---

### Post by shadows123 on 2008-12-17
Okay i saw a lot of issues like this, but couldn't really find an answer, sorry for the double post.
Look i have ubuntu installed ( i'm able to install it like always )
and now. i've just received kubuntu ( and i really like it better than ubuntu )
and when i'm trying to install kubuntu it does not show up any partition..
i prefer kubuntu to ubuntu..
Hmm..
i'm thinking, as i already have Ubuntu installed, maybe i could just use a package to transform it into kubuntu?
As it seems i can't see any partition of my hdd in kubuntu :( ( sadly )..
Can you guys help me out?
Thank you,
- Shadows123.
- It may be a problem from my hdd? idk but it's true that i now have like 30 GB left, and it says: UNUSABLE. i just can't use it?
That's also a weird thing..

Thank you!
- Shadows123.

---

### Post by gazj on 2008-12-17
apt-get install kubuntu-desktop

---

### Post by gazj on 2008-12-17
also try partitioning the good old fashioned way using cfdisk of fdisk from the command line, results may be better :)

---

### Post by shadows123 on 2008-12-17
i see.
thanks.
It's sad i can't use it via cd.. lol that way i don't spend GB's from my internet bandwidth quota xD..
Do you have an idea how many GB that is?
Thanks :).
btw, i partition using the installers partitoner, is there a way to install it without using it? but then you'd have to install through the terminal right?
- Shadows123.

---

### Post by Bucky Ball on 2008-12-17
> **gazj said:**
> apt-get install kubuntu-desktop

+1

Definitely the way to go if you want the KDE environment inside Ubuntu. You will then find KDE and Gnome in the selections when you click 'Session' at the login window, and you can take your pick. I actually haven't used Ubuntu for awhile but, it is not there already is it? If you log out then back in again, hit 'Session' and see if there is a listing for KDE (this is on your Ubuntu kernel incidentally, not logging into Kubuntu).

To get you experimenting, I am running Xubuntu with the multimedia packages from Ubuntu Studio and the low latency kernel pulled into that on my desktop workhorse and it rocks. Also, you can install OpenBox, regardless of KDE or Gnome and select 'Gnome/Openbox' or 'KDE/Openbox' in Sessions at login. This will speed things up a little.

---

### Post by shadows123 on 2008-12-17
```
shadows@Shadows-PC:~$ sudo su
[sudo] password for shadows: 
root@Shadows-PC:/home/shadows# apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  adept akregator amarok amarok-common amarok-engine-xine apport-qt ark
  dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent
  gtk-qt-engine guidance-power-manager gwenview hpijs-ppds hplip-gui
  ijsgutenprint imagemagick install-package jockey-common jockey-gtk
  jockey-kde k3b k3b-data kaddressbook kamera kate kde-printer-applet
  kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma
  kdebase-workspace-bin kdebase-workspace-data kdebluetooth
  kdegraphics-strigi-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5
  kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-kresources
  kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5
  kdeplasma-addons kdeplasma-addons-data kdeplasma-addons-libs4 kdesudo kdm
  kfind kgrubeditor klipper kmag kmail kmix kmousetool konqueror
  konqueror-nsplugins konqueror-plugin-searchbar konsole kontact konversation
  kopete korganizer krdc krfb ksnapshot ksysguard ksysguardd ksystemlog
  ktimetracker ktorrent kubuntu-artwork-usplash kubuntu-default-settings
  kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager
  language-selector-qt libarts1c2a libartsc0 libavahi-qt3-1 libcapseo0
  libcaptury0 libdbus-1-qt3 libdbus-qt-1-1c2 libexiv2-4 libfftw3-3 libflac++6
  libgeoip1 libifp4 libk3b3 libkcddb4 libkdecorations4 libkholidays4
  libkipi-common libkipi5 libkleo4 libkonq5 libkonq5-templates libkpgp4
  libksieve4 libkwineffects1 liblua50 liblualib50 libmimelib4 libmodplug0c2
  libmpcdec3 libnjb5 libofa0 libokularcore1 libplasma2 libpoppler-qt4-3
  libqca2 libqca2-plugin-ossl libqimageblitz4 libqt4-core libsearchclient0
  libstrigihtmlgui0 libtunepimp5 libvncserver0 libxcb-shape0 libxcb-shm0
  libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins
  libxine1-x libxvmc1 libzip1 mediamanager network-manager-kde okular
  okular-extra-backends openoffice.org-base-core openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-kde openoffice.org-math openoffice.org-style-crystal
  openoffice.org-style-human openoffice.org-writer oxygen-cursor-theme
  phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasmoid-quickaccess
  python-kde4 python-qt3 python-qt4 python-qt4-common python-qt4-dbus
  python-reportlab python-sip4 python-uno software-properties-kde speedcrunch
  strigi-client strigi-daemon system-config-printer-kde systemsettings
  ttf-dustin update-manager-kde update-notifier-kde
Suggested packages:
  amarok-engines moodbar libqt0-ruby1.8 ncompress zoo p7zip-full k3b-i18n
  normalize-audio toolame sox movixmaker-2 vcdimager kdebase-kio-plugins
  kcontrol libk3b3-extracodecs transcode perl-suid egroupware procmail clamav
  f-prot-installer knewsticker kweather gnokii kitchensync knode
  libsoap-lite-perl kdeartwork-emoticons php5-cli ktorrent-dbg libarts1-akode
  libfftw3-dev geoip-bin libqca2-plugin-cyrus-sasl libqca2-plugin-gnupg
  libqca2-plugin-pkcs11 libvncserver0-dbg gxine xine-ui libxine1-doc
  libxine-doc libxine1-ffmpeg openoffice.org-base
  openoffice.org-style-industrial openoffice.org-style-hicontrast
  openoffice.org-evolution gstreamer0.10-plugins-bad kde-icons-crystal
  crystalcursors openoffice.org-gcj openoffice.org-filter-binfilter
  openoffice.org-java-common openoffice.org-writer2latex pinentry-doc
  python-kde4-dbg libqt3-mt-mysql libqt3-mt-odbc libqt3-mt-psql python-qt3-doc
  python-qt3-gl python-qt4-dbg python-egenix-mxtexttools python-reportlab-doc
  strigi-plugins
Recommended packages:
  python-renderpm
The following NEW packages will be installed:
  adept akregator amarok amarok-common amarok-engine-xine apport-qt ark
  dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent
  gtk-qt-engine guidance-power-manager gwenview hpijs-ppds hplip-gui
  ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data
  kaddressbook kamera kate kde-printer-applet kde-window-manager kde-zeroconf
  kdebase-bin kdebase-data kdebase-plasma kdebase-workspace-bin kdebluetooth
  kdegraphics-strigi-plugins kdelibs-data kdelibs4c2a
  kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins
  kdepim-wizards kdeplasma-addons kdeplasma-addons-data kdeplasma-addons-libs4
  kdesudo kdm kfind kgrubeditor klipper kmag kmail kmix kmousetool konqueror
  konqueror-nsplugins konqueror-plugin-searchbar konsole kontact konversation
  kopete korganizer krdc krfb ksnapshot ksysguard ksysguardd ksystemlog
  ktimetracker ktorrent kubuntu-artwork-usplash kubuntu-default-settings
  kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd
  kwalletmanager language-selector-qt libarts1c2a libartsc0 libavahi-qt3-1
  libcapseo0 libcaptury0 libdbus-1-qt3 libdbus-qt-1-1c2 libexiv2-4 libfftw3-3
  libflac++6 libgeoip1 libifp4 libk3b3 libkcddb4 libkdecorations4
  libkholidays4 libkipi-common libkipi5 libkleo4 libkonq5 libkonq5-templates
  libkpgp4 libksieve4 libkwineffects1 liblua50 liblualib50 libmimelib4
  libmodplug0c2 libmpcdec3 libnjb5 libofa0 libokularcore1 libpoppler-qt4-3
  libqca2 libqca2-plugin-ossl libqimageblitz4 libqt4-core libsearchclient0
  libstrigihtmlgui0 libtunepimp5 libvncserver0 libxcb-shape0 libxcb-shm0
  libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins
  libxine1-x libxvmc1 libzip1 mediamanager network-manager-kde okular
  okular-extra-backends openoffice.org-kde openoffice.org-style-crystal
  oxygen-cursor-theme phonon-backend-xine pinentry-gtk2 pinentry-qt4
  plasmoid-quickaccess python-kde4 python-qt3 python-qt4 python-qt4-common
  python-qt4-dbus python-reportlab python-sip4 software-properties-kde
  speedcrunch strigi-client strigi-daemon system-config-printer-kde
  systemsettings ttf-dustin update-manager-kde update-notifier-kde
The following packages will be upgraded:
  jockey-common jockey-gtk kdebase-workspace-data kdelibs-bin kdelibs5
  kdelibs5-data kdepimlibs-data kdepimlibs5 libplasma2
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-math
  openoffice.org-style-human openoffice.org-writer python-uno
21 upgraded, 158 newly installed, 0 to remove and 152 not upgraded.
Need to get 190MB of archives.
After this operation, 446MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://be.archive.ubuntu.com intrepid-updates/main openoffice.org-calc 1:2.4.1-11ubuntu2.1 [4113kB]
Get:2 http://be.archive.ubuntu.com intrepid-updates/main openoffice.org-impress 1:2.4.1-11ubuntu2.1 [451kB]
Get:3 http://be.archive.ubuntu.com intrepid-updates/main openoffice.org-draw 1:2.4.1-11ubuntu2.1 [1908kB]
Get:4 http://be.archive.ubuntu.com intrepid-updates/main openoffice.org-style-crystal 1:2.4.1-11ubuntu2.1 [3484kB]
Get:5 http://be.archive.ubuntu.com intrepid-updates/main openoffice.org-style-human 1:2.4.1-11ubuntu2.1 [3928kB]
Get:6 http://be.archive.ubuntu.com intrepid-updates/main openoffice.org-common 1:2.4.1-11ubuntu2.1 [9700kB]
Get:7 http://be.archive.ubuntu.com intrepid-updates/main openoffice.org-gtk 1:2.4.1-11ubuntu2.1 [148kB]
Get:8 http://be.archive.ubuntu.com intrepid-updates/main openoffice.org-gnome 1:2.4.1-11ubuntu2.1 [64.1kB]
Get:9 http://be.archive.ubuntu.com intrepid-updates/main python-uno 1:2.4.1-11ubuntu2.1 [91.0kB]
Get:10 http://be.archive.ubuntu.com intrepid-updates/main openoffice.org-math 1:2.4.1-11ubuntu2.1 [241kB]
Get:11 http://be.archive.ubuntu.com intrepid-updates/main openoffice.org-writer 1:2.4.1-11ubuntu2.1 [5094kB]
Get:12 http://be.archive.ubuntu.com intrepid-updates/main openoffice.org-core 1:2.4.1-11ubuntu2.1 [26.1MB]
Get:13 http://be.archive.ubuntu.com intrepid-updates/main openoffice.org-base-core 1:2.4.1-11ubuntu2.1 [501kB]
Get:14 http://be.archive.ubuntu.com intrepid/main libartsc0 1.5.10-0ubuntu1 [16.7kB]
Get:15 http://be.archive.ubuntu.com intrepid/main libarts1c2a 1.5.10-0ubuntu1 [1060kB]
Get:16 http://be.archive.ubuntu.com intrepid/main libavahi-qt3-1 0.6.23-2ubuntu2 [33.5kB]
Get:17 http://be.archive.ubuntu.com intrepid/main liblua50 5.0.3-3 [48.7kB]    
Get:18 http://be.archive.ubuntu.com intrepid/main liblualib50 5.0.3-3 [35.1kB] 
Get:19 http://be.archive.ubuntu.com intrepid/main kdelibs-data 4:3.5.10-0ubuntu6 [7321kB]
Get:20 http://be.archive.ubuntu.com intrepid/main kdelibs4c2a 4:3.5.10-0ubuntu6 [10.1MB]
Get:21 http://be.archive.ubuntu.com intrepid-updates/main openoffice.org-kde 1:2.4.1-11ubuntu2.1 [156kB]
Get:22 http://be.archive.ubuntu.com intrepid-updates/main kdelibs-bin 4:4.1.3-0ubuntu1~intrepid4 [372kB]
Get:23 http://be.archive.ubuntu.com intrepid-updates/main kdelibs5-data 4:4.1.3-0ubuntu1~intrepid4 [3110kB]
Get:24 http://be.archive.ubuntu.com intrepid-updates/main kdelibs5 4:4.1.3-0ubuntu1~intrepid4 [9518kB]
Get:25 http://be.archive.ubuntu.com intrepid/main adept 3.0~beta4ubuntu5 [377kB]
Get:26 http://be.archive.ubuntu.com intrepid-updates/main kdepimlibs-data 4:4.1.3-0ubuntu1~intrepid2 [158kB]
Get:27 http://be.archive.ubuntu.com intrepid-updates/main kdepimlibs5 4:4.1.3-0ubuntu1~intrepid2 [2482kB]
Get:28 http://be.archive.ubuntu.com intrepid-updates/main akregator 4:4.1.3-0ubuntu1~intrepid2 [686kB]
Get:29 http://be.archive.ubuntu.com intrepid/main amarok-common 2:1.4.10-0ubuntu3 [7188kB]
Get:30 http://be.archive.ubuntu.com intrepid/main libmodplug0c2 1:0.7-7 [122kB]
Get:31 http://be.archive.ubuntu.com intrepid/main libmpcdec3 1.2.2-1build1 [27.4kB]
Get:32 http://be.archive.ubuntu.com intrepid/main libxine1-bin 1.1.15-0ubuntu3 [1343kB]
Get:33 http://be.archive.ubuntu.com intrepid/main libxine1-misc-plugins 1.1.15-0ubuntu3 [929kB]
Get:34 http://be.archive.ubuntu.com intrepid/main libxcb-shape0 1.1-1.1 [5552B]
Get:35 http://be.archive.ubuntu.com intrepid/main libxcb-shm0 1.1-1.1 [5110B]  
Get:36 http://be.archive.ubuntu.com intrepid/main libxcb-xv0 1.1-1.1 [8408B]   
Get:37 http://be.archive.ubuntu.com intrepid/main libxvmc1 2:1.0.4-2ubuntu1 [19.2kB]
Get:38 http://be.archive.ubuntu.com intrepid/main libxine1-x 1.1.15-0ubuntu3 [212kB]
Get:39 http://be.archive.ubuntu.com intrepid/main libxine1-console 1.1.15-0ubuntu3 [61.4kB]
Get:40 http://be.archive.ubuntu.com intrepid/main libxine1 1.1.15-0ubuntu3 [1302B]
Get:41 http://be.archive.ubuntu.com intrepid/main amarok-engine-xine 2:1.4.10-0ubuntu3 [72.7kB]
Get:42 http://be.archive.ubuntu.com intrepid/main libifp4 1.0.0.2-3 [32.0kB]   
Get:43 http://be.archive.ubuntu.com intrepid/main libnjb5 2.2.5-4.2ubuntu1 [96.3kB]
Get:44 http://be.archive.ubuntu.com intrepid/main libfftw3-3 3.1.2-3.1ubuntu1 [1071kB]
Get:45 http://be.archive.ubuntu.com intrepid/main libofa0 0.9.3-3 [56.7kB]     
Get:46 http://be.archive.ubuntu.com intrepid/main libtunepimp5 0.5.3-7ubuntu3 [319kB]
Get:47 http://be.archive.ubuntu.com intrepid/main amarok 2:1.4.10-0ubuntu3 [2454kB]
Get:48 http://be.archive.ubuntu.com intrepid/main python-sip4 4.7.7-1 [111kB]  
Get:49 http://be.archive.ubuntu.com intrepid/main python-qt4-common 4.4.3-1ubuntu1 [62.0kB]
Get:50 http://be.archive.ubuntu.com intrepid/main python-qt4 4.4.3-1ubuntu1 [4885kB]
Get:51 http://be.archive.ubuntu.com intrepid/main apport-qt 0.119 [56.1kB]     
Get:52 http://be.archive.ubuntu.com intrepid/main libzip1 0.8-1 [22.1kB]       
Get:53 http://be.archive.ubuntu.com intrepid-updates/main ark 4:4.1.3-0ubuntu1~intrepid1 [226kB]
Get:54 http://be.archive.ubuntu.com intrepid-updates/main libkonq5-templates 4:4.1.3-0ubuntu1~intrepid1 [88.6kB]
Get:55 http://be.archive.ubuntu.com intrepid-updates/main libkonq5 4:4.1.3-0ubuntu1~intrepid1 [102kB]
Get:56 http://be.archive.ubuntu.com intrepid-updates/main dolphin 4:4.1.3-0ubuntu1~intrepid1 [1204kB]
Get:57 http://be.archive.ubuntu.com intrepid-updates/main dragonplayer 4:4.1.3-0ubuntu1~intrepid1 [458kB]
Get:58 http://be.archive.ubuntu.com intrepid/main libexiv2-4 0.17-1ubuntu1 [606kB]
Get:59 http://be.archive.ubuntu.com intrepid/main exiv2 0.17-1ubuntu1 [78.4kB] 
Get:60 http://be.archive.ubuntu.com intrepid/main ijsgutenprint 5.2.0~rc1-0ubuntu1 [49.3kB]
Get:61 http://be.archive.ubuntu.com intrepid/main foomatic-db-gutenprint 5.2.0~rc1-0ubuntu1 [4332kB]
Get:62 http://be.archive.ubuntu.com intrepid-updates/main python-kde4 4:4.1.3-0ubuntu1~intrepid1 [3502kB]
Get:63 http://be.archive.ubuntu.com intrepid/main kdesudo 3.3.1-0ubuntu1 [41.9kB]
Get:64 http://be.archive.ubuntu.com intrepid/main gdebi-kde 0.3.13 [20.6kB]    
Get:65 http://be.archive.ubuntu.com intrepid/main pinentry-gtk2 0.7.5-2ubuntu1 [48.4kB]
Get:66 http://be.archive.ubuntu.com intrepid/main pinentry-qt4 0.7.3+svn799201-1ubuntu1 [30.2kB]
Get:67 http://be.archive.ubuntu.com intrepid/main gnupg-agent 2.0.9-3.1 [289kB]
Get:68 http://be.archive.ubuntu.com intrepid/main gtk-qt-engine 1:1.1+svn20080816-0ubuntu5 [96.7kB]
Get:69 http://be.archive.ubuntu.com intrepid/main guidance-power-manager 4:4.1.2-0ubuntu5 [32.2kB]
Get:70 http://be.archive.ubuntu.com intrepid/main hpijs-ppds 2.8.7-0ubuntu6 [1675kB]
Get:71 http://be.archive.ubuntu.com intrepid/main python-qt3 3.17.4-1ubuntu4 [4798kB]
Get:72 http://be.archive.ubuntu.com intrepid/main python-reportlab 2.1dfsg-2 [643kB]
Get:73 http://be.archive.ubuntu.com intrepid-updates/main kdebase-data 4:4.1.3-0ubuntu1~intrepid1 [1144kB]
Get:74 http://be.archive.ubuntu.com intrepid-updates/main kdebase-bin 4:4.1.3-0ubuntu1~intrepid1 [689kB]
Get:75 http://be.archive.ubuntu.com intrepid/main hplip-gui 2.8.7-0ubuntu6 [54.2kB]
Get:76 http://be.archive.ubuntu.com intrepid/main imagemagick 7:6.3.7.9.dfsg1-2ubuntu3 [1421kB]
Get:77 http://be.archive.ubuntu.com intrepid/main install-package 0.3 [5780B]  
Err http://be.archive.ubuntu.com intrepid-updates/main jockey-gtk 0.5~beta3-0ubuntu6
  404 Not Found
Err http://be.archive.ubuntu.com intrepid-updates/main jockey-common 0.5~beta3-0ubuntu6
  404 Not Found
Err http://be.archive.ubuntu.com intrepid-updates/main jockey-kde 0.5~beta3-0ubuntu6
  404 Not Found
Get:78 http://be.archive.ubuntu.com intrepid/main libdbus-qt-1-1c2 0.62.git.20060814-2build1 [181kB]
Get:79 http://be.archive.ubuntu.com intrepid/main libflac++6 1.2.1-1.2 [39.7kB]
Get:80 http://be.archive.ubuntu.com intrepid/main libk3b3 1.0.5-1ubuntu6 [1058kB]
Get:81 http://be.archive.ubuntu.com intrepid/main k3b-data 1.0.5-1ubuntu6 [4342kB]
Get:82 http://be.archive.ubuntu.com intrepid/main k3b 1.0.5-1ubuntu6 [736kB]   
Get:83 http://be.archive.ubuntu.com intrepid-updates/main kdepim-kresources 4:4.1.3-0ubuntu1~intrepid2 [221kB]
Get:84 http://be.archive.ubuntu.com intrepid-updates/main libkleo4 4:4.1.3-0ubuntu1~intrepid2 [464kB]
Get:85 http://be.archive.ubuntu.com intrepid-updates/main kaddressbook 4:4.1.3-0ubuntu1~intrepid2 [1187kB]
Get:86 http://be.archive.ubuntu.com intrepid-updates/main libplasma2 4:4.1.3-0ubuntu1~intrepid1 [1546kB]
Get:87 http://be.archive.ubuntu.com intrepid-updates/main kdebase-workspace-data 4:4.1.3-0ubuntu1~intrepid1 [5685kB]
Get:88 http://be.archive.ubuntu.com intrepid-updates/main kate 4:4.1.3-0ubuntu1~intrepid1 [898kB]
Get:89 http://be.archive.ubuntu.com intrepid/main python-qt4-dbus 4.4.3-1ubuntu1 [71.8kB]
Get:90 http://be.archive.ubuntu.com intrepid-updates/main kde-printer-applet 4:4.1.3-0ubuntu1~intrepid1 [51.1kB]
Get:91 http://be.archive.ubuntu.com intrepid/main libcapseo0 0.3.0+svn20070725-0ubuntu1 [11.6kB]
Get:92 http://be.archive.ubuntu.com intrepid/main libcaptury0 0.3.0+svn20070725-0ubuntu3 [12.3kB]
Get:93 http://be.archive.ubuntu.com intrepid-updates/main libkdecorations4 4:4.1.3-0ubuntu1~intrepid1 [76.2kB]
Get:94 http://be.archive.ubuntu.com intrepid-updates/main libkwineffects1 4:4.1.3-0ubuntu1~intrepid1 [87.8kB]
Get:95 http://be.archive.ubuntu.com intrepid-updates/main kde-window-manager 4:4.1.3-0ubuntu1~intrepid1 [1445kB]
Get:96 http://be.archive.ubuntu.com intrepid-updates/main kdebase-plasma 4:4.1.3-0ubuntu1~intrepid1 [113kB]
Get:97 http://be.archive.ubuntu.com intrepid/main libqimageblitz4 1:0.0.4-4 [60.5kB]
Get:98 http://be.archive.ubuntu.com intrepid-updates/main kdebase-workspace-bin 4:4.1.3-0ubuntu1~intrepid1 [2621kB]
Get:99 http://be.archive.ubuntu.com intrepid/main kdebluetooth 1:0.2-0ubuntu2 [147kB]
Get:100 http://be.archive.ubuntu.com intrepid-updates/main libkcddb4 4:4.1.3-0ubuntu1~intrepid1 [190kB]
Get:101 http://be.archive.ubuntu.com intrepid-updates/main kdemultimedia-kio-plugins 4:4.1.3-0ubuntu1~intrepid1 [115kB]
Get:102 http://be.archive.ubuntu.com intrepid-updates/main kdepasswd 4:4.1.3-0ubuntu1~intrepid1 [190kB]
Get:103 http://be.archive.ubuntu.com intrepid-updates/main kdepim-strigi-plugins 4:4.1.3-0ubuntu1~intrepid2 [43.0kB]
Get:104 http://be.archive.ubuntu.com intrepid-updates/main libkholidays4 4:4.1.3-0ubuntu1~intrepid2 [91.0kB]
Get:105 http://be.archive.ubuntu.com intrepid-updates/main korganizer 4:4.1.3-0ubuntu1~intrepid2 [1713kB]
Get:106 http://be.archive.ubuntu.com intrepid-updates/main kdepim-wizards 4:4.1.3-0ubuntu1~intrepid2 [226kB]
Get:107 http://be.archive.ubuntu.com intrepid-updates/main kdeplasma-addons-libs4 4:4.1.3-0ubuntu1~intrepid1 [11.6kB]
Get:108 http://be.archive.ubuntu.com intrepid-updates/main kdeplasma-addons-data 4:4.1.3-0ubuntu1~intrepid1 [671kB]
Get:109 http://be.archive.ubuntu.com intrepid-updates/main kdeplasma-addons 4:4.1.3-0ubuntu1~intrepid1 [406kB]
Get:110 http://be.archive.ubuntu.com intrepid-updates/main kdm 4:4.1.3-0ubuntu1~intrepid1 [868kB]
Get:111 http://be.archive.ubuntu.com intrepid-updates/main kfind 4:4.1.3-0ubuntu1~intrepid1 [212kB]
Get:112 http://be.archive.ubuntu.com intrepid/main kgrubeditor 0.8.5-0ubuntu3 [257kB]
Get:113 http://be.archive.ubuntu.com intrepid-updates/main klipper 4:4.1.3-0ubuntu1~intrepid1 [129kB]
Get:114 http://be.archive.ubuntu.com intrepid-updates/main kmag 4:4.1.3-0ubuntu1~intrepid1 [260kB]
Get:115 http://be.archive.ubuntu.com intrepid-updates/main libkpgp4 4:4.1.3-0ubuntu1~intrepid2 [146kB]
Get:116 http://be.archive.ubuntu.com intrepid-updates/main libksieve4 4:4.1.3-0ubuntu1~intrepid2 [48.8kB]
Get:117 http://be.archive.ubuntu.com intrepid-updates/main libmimelib4 4:4.1.3-0ubuntu1~intrepid2 [113kB]
Get:118 http://be.archive.ubuntu.com intrepid-updates/main kmail 4:4.1.3-0ubuntu1~intrepid2 [3342kB]
Get:119 http://be.archive.ubuntu.com intrepid-updates/main kmix 4:4.1.3-0ubuntu1~intrepid1 [279kB]
Get:120 http://be.archive.ubuntu.com intrepid-updates/main kmousetool 4:4.1.3-0ubuntu1~intrepid1 [58.7kB]
Get:121 http://be.archive.ubuntu.com intrepid-updates/main konqueror 4:4.1.3-0ubuntu1~intrepid1 [1296kB]
Get:122 http://be.archive.ubuntu.com intrepid-updates/main konqueror-nsplugins 4:4.1.3-0ubuntu1~intrepid1 [138kB]
Get:123 http://be.archive.ubuntu.com intrepid-updates/main konsole 4:4.1.3-0ubuntu1~intrepid1 [788kB]
Get:124 http://be.archive.ubuntu.com intrepid-updates/main kontact 4:4.1.3-0ubuntu1~intrepid2 [526kB]
Get:125 http://be.archive.ubuntu.com intrepid-updates/main konversation 1.1-0ubuntu2.1 [4830kB]
Get:126 http://be.archive.ubuntu.com intrepid/main libqca2 2.0.0-4 [522kB]     
Get:127 http://be.archive.ubuntu.com intrepid-updates/main kopete 4:4.1.3-0ubuntu1~intrepid2 [7057kB]
Get:128 http://be.archive.ubuntu.com intrepid/main libvncserver0 0.9.3.dfsg.1-1ubuntu1 [163kB]
Get:129 http://be.archive.ubuntu.com intrepid-updates/main krdc 4:4.1.3-0ubuntu1~intrepid2 [388kB]
Get:130 http://be.archive.ubuntu.com intrepid-updates/main krfb 4:4.1.3-0ubuntu1~intrepid2 [457kB]
Get:131 http://be.archive.ubuntu.com intrepid-updates/main ksysguardd 4:4.1.3-0ubuntu1~intrepid1 [85.3kB]
Get:132 http://be.archive.ubuntu.com intrepid-updates/main ksysguard 4:4.1.3-0ubuntu1~intrepid1 [226kB]
Get:133 http://be.archive.ubuntu.com intrepid-updates/main ksystemlog 4:4.1.3-0ubuntu1~intrepid1 [746kB]
Get:134 http://be.archive.ubuntu.com intrepid-updates/main ktimetracker 4:4.1.3-0ubuntu1~intrepid2 [380kB]
Get:135 http://be.archive.ubuntu.com intrepid/main libgeoip1 1.4.4.dfsg-2 [641kB]
Get:136 http://be.archive.ubuntu.com intrepid/main ktorrent 3.1.2+dfsg.1-0ubuntu2 [1872kB]
Get:137 http://be.archive.ubuntu.com intrepid/main kubuntu-artwork-usplash 1:8.10-13 [107kB]
Get:138 http://be.archive.ubuntu.com intrepid/main kubuntu-default-settings 1:8.10-13 [526kB]
Get:139 http://be.archive.ubuntu.com intrepid-updates/main kde-zeroconf 4:4.1.3-0ubuntu1~intrepid2 [57.8kB]
Get:140 http://be.archive.ubuntu.com intrepid-updates/main ksnapshot 4:4.1.3-0ubuntu1~intrepid1 [218kB]
Get:141 http://be.archive.ubuntu.com intrepid-updates/main kuser 4:4.1.3-0ubuntu1~intrepid1 [242kB]
Get:142 http://be.archive.ubuntu.com intrepid/main language-selector-qt 0.3.17 [22.5kB]
Get:143 http://be.archive.ubuntu.com intrepid-updates/main libokularcore1 4:4.1.3-0ubuntu1~intrepid1 [265kB]
Get:144 http://be.archive.ubuntu.com intrepid/main libpoppler-qt4-3 0.8.7-1 [157kB]
Get:145 http://be.archive.ubuntu.com intrepid-updates/main okular 4:4.1.3-0ubuntu1~intrepid1 [945kB]
Get:146 http://be.archive.ubuntu.com intrepid-updates/main phonon-backend-xine 4:4.1.3-0ubuntu1~intrepid1 [158kB]
Get:147 http://be.archive.ubuntu.com intrepid-updates/main software-properties-kde 0.68.1 [18.4kB]
Get:148 http://be.archive.ubuntu.com intrepid-updates/main systemsettings 4:4.1.3-0ubuntu1~intrepid1 [108kB]
Get:149 http://be.archive.ubuntu.com intrepid/main kubuntu-desktop 1.101 [20.7kB]
Get:150 http://be.archive.ubuntu.com intrepid/main kubuntu-docs 8.10-6 [241kB] 
Get:151 http://be.archive.ubuntu.com intrepid/main kubuntu-konqueror-shortcuts 0.6 [5344B]
Get:152 http://be.archive.ubuntu.com intrepid/main kvkbd 0.6.0-0ubuntu1 [83.8kB]
Get:153 http://be.archive.ubuntu.com intrepid-updates/main kwalletmanager 4:4.1.3-0ubuntu1~intrepid1 [365kB]
Get:154 http://be.archive.ubuntu.com intrepid/main libdbus-1-qt3 0.9-0ubuntu1 [79.5kB]
Get:155 http://be.archive.ubuntu.com intrepid-updates/main libqt4-core 4.4.3-0ubuntu1.1 [7556B]
Get:156 http://be.archive.ubuntu.com intrepid/main libqca2-plugin-ossl 0.1~20070904-3 [111kB]
Get:157 http://be.archive.ubuntu.com intrepid/main libsearchclient0 0.5.11-1ubuntu2 [38.3kB]
Get:158 http://be.archive.ubuntu.com intrepid/main libstrigihtmlgui0 0.5.11-1ubuntu2 [28.2kB]
Get:159 http://be.archive.ubuntu.com intrepid/main mediamanager 4:3.5.10-0ubuntu3 [113kB]
Get:160 http://be.archive.ubuntu.com intrepid/main network-manager-kde 1:0.7svn864988-0ubuntu1 [528kB]
Get:161 http://be.archive.ubuntu.com intrepid/main oxygen-cursor-theme 0.0.2008-01-27-a7b68163e7c8ccc1376-2ubuntu3 [110kB]
Get:162 http://be.archive.ubuntu.com intrepid/main plasmoid-quickaccess 0.7.1-0ubuntu1 [69.8kB]
Get:163 http://be.archive.ubuntu.com intrepid/main speedcrunch 0.10.1-1ubuntu1 [518kB]
Get:164 http://be.archive.ubuntu.com intrepid/main strigi-daemon 0.5.11-1ubuntu2 [139kB]
Get:165 http://be.archive.ubuntu.com intrepid/main strigi-client 0.5.11-1ubuntu2 [57.5kB]
Get:166 http://be.archive.ubuntu.com intrepid/main system-config-printer-kde 0.11 [49.4kB]
Get:167 http://be.archive.ubuntu.com intrepid/main ttf-dustin 20030517-6 [621kB]
Get:168 http://be.archive.ubuntu.com intrepid-updates/main update-manager-kde 1:0.93.34 [32.7kB]
Get:169 http://be.archive.ubuntu.com intrepid/main update-notifier-kde 0.9 [10.4kB]
Get:170 http://be.archive.ubuntu.com intrepid-updates/main libkipi-common 4:4.1.3-0ubuntu1~intrepid1 [43.5kB]
Get:171 http://be.archive.ubuntu.com intrepid-updates/main libkipi5 4:4.1.3-0ubuntu1~intrepid1 [37.6kB]
Get:172 http://be.archive.ubuntu.com intrepid-updates/main gwenview 4:4.1.3-0ubuntu1~intrepid1 [1218kB]
Get:173 http://be.archive.ubuntu.com intrepid-updates/main kamera 4:4.1.3-0ubuntu1~intrepid1 [88.3kB]
Get:174 http://be.archive.ubuntu.com intrepid-updates/main kdegraphics-strigi-plugins 4:4.1.3-0ubuntu1~intrepid1 [52.5kB]
Get:175 http://be.archive.ubuntu.com intrepid/main konqueror-plugin-searchbar 4:4.1.2-0ubuntu2 [36.8kB]
Get:176 http://be.archive.ubuntu.com intrepid-updates/main okular-extra-backends 4:4.1.3-0ubuntu1~intrepid1 [51.9kB]
Fetched 190MB in 1min39s (1921kB/s)                                            
Failed to fetch http://be.archive.ubuntu.com/ubuntu/pool/main/j/jockey/jockey-gtk_0.5~beta3-0ubuntu6_all.deb  404 Not Found
Failed to fetch http://be.archive.ubuntu.com/ubuntu/pool/main/j/jockey/jockey-common_0.5~beta3-0ubuntu6_all.deb  404 Not Found
Failed to fetch http://be.archive.ubuntu.com/ubuntu/pool/main/j/jockey/jockey-kde_0.5~beta3-0ubuntu6_all.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@Shadows-PC:/home/shadows# --fix-missing
bash: --fix-missing: command not found
root@Shadows-PC:/home/shadows# apt-get update
Hit http://be.archive.ubuntu.com intrepid Release.gpg
Ign http://be.archive.ubuntu.com intrepid/main Translation-en_US
Ign http://be.archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://be.archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://be.archive.ubuntu.com intrepid/multiverse Translation-en_US
Get:1 http://be.archive.ubuntu.com intrepid-updates Release.gpg [189B]
Ign http://be.archive.ubuntu.com intrepid-updates/main Translation-en_US
Get:2 http://security.ubuntu.com intrepid-security Release.gpg [189B]
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US
Ign http://be.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://be.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://be.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
Get:3 http://security.ubuntu.com intrepid-security Release [44.0kB]
Hit http://be.archive.ubuntu.com intrepid Release  
Get:4 http://be.archive.ubuntu.com intrepid-updates Release [51.2kB]
Hit http://be.archive.ubuntu.com intrepid/main Packages                        
Hit http://be.archive.ubuntu.com intrepid/restricted Packages
Hit http://be.archive.ubuntu.com intrepid/main Sources
Hit http://be.archive.ubuntu.com intrepid/restricted Sources
Hit http://be.archive.ubuntu.com intrepid/universe Packages
Get:5 http://security.ubuntu.com intrepid-security/main Packages [36.4kB]
Hit http://be.archive.ubuntu.com intrepid/universe Sources
Hit http://be.archive.ubuntu.com intrepid/multiverse Packages
Hit http://be.archive.ubuntu.com intrepid/multiverse Sources
Get:6 http://be.archive.ubuntu.com intrepid-updates/main Packages [254kB]
Get:7 http://security.ubuntu.com intrepid-security/restricted Packages [1785B]
Get:8 http://security.ubuntu.com intrepid-security/main Sources [11.7kB]       
Get:9 http://security.ubuntu.com intrepid-security/restricted Sources [571B]   
Get:10 http://security.ubuntu.com intrepid-security/universe Packages [14.0kB] 
Get:11 http://be.archive.ubuntu.com intrepid-updates/restricted Packages [3861B]
Get:12 http://be.archive.ubuntu.com intrepid-updates/main Sources [79.3kB]
Get:13 http://security.ubuntu.com intrepid-security/universe Sources [1617B]   
Get:14 http://security.ubuntu.com intrepid-security/multiverse Packages [14B]  
Get:15 http://security.ubuntu.com intrepid-security/multiverse Sources [14B] 
Get:16 http://be.archive.ubuntu.com intrepid-updates/restricted Sources [1169B]
Get:17 http://be.archive.ubuntu.com intrepid-updates/universe Packages [29.4kB]
Get:18 http://be.archive.ubuntu.com intrepid-updates/universe Sources [5727B]
Get:19 http://be.archive.ubuntu.com intrepid-updates/multiverse Packages [1923B]
Get:20 http://be.archive.ubuntu.com intrepid-updates/multiverse Sources [803B]
Fetched 537kB in 0s (631kB/s)                      
Reading package lists... Done
root@Shadows-PC:/home/shadows# 


```
i'm not sure it worked it said fail or something??
Thank you,
- Shadows.

didn't work.. it said failed to change session to kde, changing session back to normal or something because of missing things..
i'll try this command again..
second edit:
it seems it's doing more than last time now, i'll hope this time it works :D

---

### Post by Bucky Ball on 2008-12-17
Are you going from a restart (not logout/in)? It shouldn't make any difference but may be.

---

### Post by shadows123 on 2008-12-17
nah, it downloaded wrongly, i redid the apt-get
and now it works :D.
Thanks guys!
Wow i love kubuntu xD..
- Shadows123.
thanked both of you :D.

---

### Post by Bucky Ball on 2008-12-17
Try installing Openbox and login to Sessions -> KDE/Openbox and see if things speed up for you. It's in Synaptics. And you're welcome BTW. :)

---

### Post by shadows123 on 2008-12-17
I'll try that when i have time.
Damn i love Kubuntu :D.
Didn't know it's so great!
omg, really idk how it's possible it's so great xD..
those graphics :O
thanks again!
firstly i thought i hated this cursor but it's okay xD..
now em.. i have a question, i'm too much used to a double click for opening folders um.. any idea where i can change this? :D.
- Shadows.

---

### Post by Bucky Ball on 2008-12-17
Not familiar with KDE, currently in love with Xfce!

---

