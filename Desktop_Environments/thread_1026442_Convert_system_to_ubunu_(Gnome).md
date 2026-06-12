---
title: "Convert system to ubunu (Gnome)"
date: 2008-12-31
forum: Desktop Environments
---

### Post by chrestomanci on 2008-12-31
Hello

I have been using linux for many years, and up until now I have always been using KDE as my desktop manager, my main system runs kubuntu intrepid.

Recently, I have decided that I don't like KDE4, I also have a laptop that I installed ubuntu (Gnome) on, and I have decided that I prefer a Gnome based desktop to a KDE one. I would like to permanently convert my kubuntu system to ubuntu. How should I do that?

I have already installed all the default gnome packages using:
```
tasksel --task-packages ubuntu-desktop | xargs aptitude install -d -y
```
The Gnome desktop works, but I do not have the nice default task bar and menu entries that I have on my laptop that was Gnome from first install. It would also be nice to have Gnome as the default desktop when I log in, and a brown splash screen when the system boots.

---

### Post by Dr.Suave on 2008-12-31
try ```
sudo apt-get install ubuntu-desktop
```

---

### Post by Barriehie on 2008-12-31
I had to do the same thing;  found this link:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Barrie

---

### Post by chrestomanci on 2008-12-31
> **Barriehie said:**
> I had to do the same thing;  found this link:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Barrie

Thanks for the link

It points to this code snippet:
```

sudo apt-get remove adept akregator amarok amarok-common amarok-engine-xine apport-qt ark dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk-qt-engine guidance-power-manager gwenview hpijs-ppds hplip-gui ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data kaddressbook kamera kate kde-icons-oxygen kde-printer-applet kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons kdeplasma-addons-data kdeplasma-addons-libs4 kdesudo kdm kfind kgrubeditor khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact konversation kopete korganizer krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libcapseo0 libcaptury0 libclucene0ldbl libdbus-1-qt3 libdbus-qt-1-1c2 libexiv2-4 libfftw3-3 libflac++6 libgeoip1 libifp4 libk3b3 libkcddb4 libkdecorations4 libkdepim4 libkholidays4 libkipi-common libkipi5 libkleo4 libkonq5 libkonq5-templates libkpgp4 libksieve4 libkwineffects1 liblua50 liblualib50 libmimelib4 libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libofa0 libokularcore1 libphonon4 libplasma2 libpoppler-qt4-3 libpq5 libqca2 libqca2-plugin-ossl libqimageblitz4 libqt3-mt libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libraptor1 librasqal0 librdf0 libruby1.8 libsearchclient0 libsoprano4 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libstrigiqtdbusclient0 libtunepimp5 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libxvmc1 libzip1 mediamanager mysql-common network-manager-kde okular okular-extra-backends openoffice.org-kde openoffice.org-style-crystal oxygen-cursor-theme phonon phonon-backend-gstreamer phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasmoid-quickaccess python-kde4 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 qt4-qtconfig raptor-utils redland-utils ruby ruby1.8 software-properties-kde soprano-daemon speedcrunch strigi-client strigi-daemon system-config-printer-kde systemsettings ttf-dustin update-manager-kde update-notifier-kde

sudo apt-get install ubuntu-desktop

```

i.e. It just tells you to remove a whole bunch of packages that are in some way related to KDE, and then install gnome desktop. (Though I think that in some cases the relationship is tenuous, I can't imagine how **mysql-common** is specifically related to KDE and not Gnome).

In any case, that solution would not suit me, as I like many KDE applications. For example, I prefer K3B to Brasero because it fills in the name of the disc automatically from the first file I add. In my case, it is just the window manager I don't want to use.

---

### Post by benerivo on 2008-12-31
To change to the ubuntu splash sreen try```
sudo update-alternatives --config usplash-artwork.so
```

Use Synaptic to get rid of kde packages, that clutter up your main menu. As long as you use kde apps such as amarok (which might be the app that needs mysql-common (for your music library) then you will have to keep some packages that you would otherwise not need. Just use Synaptic carefully as you remove kde apps, so that you don't uninstall essential packages. This will generally be straight forward, or you may want to just issue the psychocats command and then reinstall anything you wanted to keep. I would choose the second way.

---

