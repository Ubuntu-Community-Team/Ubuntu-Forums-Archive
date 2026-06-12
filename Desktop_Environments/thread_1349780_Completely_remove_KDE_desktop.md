---
title: "Completely remove KDE desktop"
date: 2009-12-08
forum: Desktop Environments
---

### Post by atentik on 2009-12-08
Is there a way to completely remove KDE desktop? After install kde-desktop on my laptop, I notice a strange start up screen ... Blank screen. I am not completely sure if the blank screen is attributed to the installation of kde-desktop since it started a few times normally after the installation. Somehow, my guts tells me to completely remove the kde-desktop and things will be somehow solve. I tried > sudo aptitude remove kde-desktop to remove the kde-desktop but it won't remove. Is there any other thing I can do to completely remove this desktop and/switch to gnome startup. I also tried > switchdesktop gnome but to no avail. If there is a way to completely remove KDE-desktop, please let me know.

Thank you.

---

### Post by andrea000 on 2009-12-08
Try this
> sudo apt-get purge kubuntu-desktop

---

### Post by wojox on 2009-12-08
[PureGnome]("http://www.psychocats.net/ubuntu/puregnome")

---

### Post by atentik on 2009-12-08
> **andrea000 said:**
> Try this

Thanks but this does not work...

---

### Post by atentik on 2009-12-08
> **wojox said:**
> [PureGnome]("http://www.psychocats.net/ubuntu/puregnome")

How do I start the season with Gnome?

---

### Post by Hozza on 2009-12-16
will ```
sudo apt-get remove akonadi-server akregator amarok amarok-common amarok-utils apport-kde apturl-kde ark cdrdao dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ibus-qt4 ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data kaddressbook kamera kate kcm-gtk kde-icons-oxygen kde-style-qtcurve kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-groupware kdepim-kresources kdepim-runtime kdepim-runtime-data kdepim-runtime-libs4 kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdesudo kdm kfind khelpcenter4 kipi-plugins klipper kmag kmail kmix kmousetool knotes konq-plugins konq-plugins-l10n konqueror konqueror-nsplugins konqueror-plugin-searchbar konqueror-plugins konsole kontact kopete korganizer kpackagekit kppp krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-firefox-installer kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin-style-qtcurve language-selector-qt libakonadiprivate1 libao2 libaudio2 libboost-program-options1.38.0 libclucene0ldbl libepub0 libexiv2-5 libfftw3-3 libflac++6 libindicate-qt0 libjpeg-progs libk3b6 libkabcommon4 libkcddb4 libkdcraw7 libkdecorations4 libkdepim4 libkexiv2-7 libkipi6 libkleo4 libknotificationitem1 libkonq5 libkonq5-templates libkonqsidebarplugin4 libkontactinterfaces4 libkopete4 libkorundum4-ruby1.8 libkpgp4 libksane0 libksieve4 libkwineffects1 liblancelot0 liblastfm0 liblzma0 libmimelib4 libmodplug0c2 libmpcdec3 libmsn0.1 libokularcore1 libotr2 libpackagekit-glib11 libpackagekit-qt11 libplasma3 libpolkit-dbus2 libpolkit-grant2 libpolkit-qt0 libpolkit2 libpoppler-qt4-3 libqca2 libqca2-plugin-ossl libqimageblitz4 libqscintilla2-5 libqt4-assistant libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-phonon libqt4-qt3support libqt4-ruby1.8 libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml libruby1.8 libscim8c2a libsmokekde4-2 libsmokeqt4-2 libsoprano4 libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 libtag-extras1 libtidy-0.99-0 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-server-core-5.1 okular okular-extra-backends openoffice.org-kde openoffice.org-style-oxygen oxygen-cursor-theme packagekit packagekit-backend-apt phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-scriptengine-python plasma-widget-facebook plasma-widget-folderview plasma-widget-googlecalendar plasma-widget-indicatordisplay plasma-widget-kimpanel plasma-widget-kubuntu-qa-feedback plasma-widget-lancelot plasma-widget-networkmanagement plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace policykit printer-applet python-kde4 python-packagekit python-qt4 python-qt4-dbus python-sip4 quassel quassel-data ruby ruby1.8 software-properties-kde soprano-daemon speedcrunch system-config-printer-kde systemsettings ttf-arphic-uming ttf-dejavu ttf-dejavu-extra update-manager-kde update-notifier-kde usb-creator-kde userconfig && sudo apt-get install ubuntu-desktop
```

remove all of KDE and its apps?

P.S. i got this code from the PureGnome link.

---

### Post by brommage on 2009-12-16
Correct me if I'm wrong, but kde-desktop is a metapackage.  It depends upon all of the applications in the full KDE install, but they are not dependent upon it.  The effect is that you can pull all of the usual packages to get KDE by pulling it from apt.  The converse means that removing the kde-desktop package does not really remove anything at all.

---

### Post by nibirumarduk on 2009-12-17
Atentik, purging kde from your Ubuntu or other *buntus ain't as easy a task as a mere sudo apt-get --purge remove kde-desktop.

Firstly before we begin, I assume you have already an alternative to fall back on e.g. GNOME, Xfce, LXDE or a WM such as fluxbox, openbox, etc. Ok assuming you have one or more, the steps are as follow:

1.
Make a listing of all kde and qt-related packages installed
dpkg --get-selections | grep kde
dpkg --get-selections | grep qt

2.
Remove all the kde and qt packages identified using dpkg --get-selections in 1., proceed to purge remove them all with sudo aptitude --purge remove. You may need to keep some of the kde/qt apps and libs if you use things like amarok, smplayer, kmplayer, minitube, xbmc, etc. E.g. for those with smplayer installed, do a aptitude why libqtcore4 and you'll see soon enough the dependency relationship between smplayer and libqtcore4. So you need to know what is it that you actually want (i.e. a KDE-free system or a pure GNOME/GTK install without a single kde/qt app)? Aptitude is your best friend. For more on what aptitude is capable of issue aptitude -h at the commandline for more.

Beware that certain indiscreet, stealthy but still kde/qt packages such as soprano-daemon and soprano-daemon-sesame may still remain. Purge them too (with sudo aptitude --purge remove soprano-daemon soprano-daemon-sesame) for a truly KDE/QT-free desktop.  

3. Purging residual configs, verifying that KDE/QT have been totally purge and housekeeping
Type these commands to remove residual configs as well as performing badly needed housekeeping:

sudo deborphan | xargs sudo apt-get -y remove --purge && sudo deborphan --guess-data | xargs sudo apt-get -y remove --purge; sudo apt-get autoremove && sudo aptitude purge '~c'; sudo apt-get autoclean

and then re-issue these commands to make triply sure.
dpkg --get-selections | grep kde
dpkg --get-selections | grep qt

That's all. All the best guys!

---

### Post by atentik on 2009-12-19
Forgot to mention the problem was SOLVED by wojox method. Thanks.

---

