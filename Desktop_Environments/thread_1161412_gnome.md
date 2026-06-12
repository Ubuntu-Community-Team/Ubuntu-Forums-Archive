---
title: "gnome"
date: 2009-05-16
forum: Desktop Environments
---

### Post by num on 2009-05-16
is it possible to change the appearance from gnome to kde but keep all the programs the same? also keep ntp?

---

### Post by whoop on 2009-05-16
You can install kde on ubuntu like:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

if you would like to remove kde afterwords and keep clean gnome again:
```

sudo apt-get remove akregator amarok amarok-common apport-qt ark cdrdao dolphin dontzap dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ijsgutenprint install-package jockey-kde k3b k3b-data kaddressbook kamera kate kde-icons-oxygen kde-printer-applet kde-style-qtcurve kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons kdeplasma-addons-data kdesudo kdm kfind khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete korganizer kpackagekit krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libao2 libaudio2 libavahi-qt3-1 libboost-program-options1.35.0 libclucene0ldbl libdbus-qt-1-1c2 libeet1 libexiv2-5 libflac++6 libgeoip1 libk3b3 libk3b3-extracodecs libkcddb4 libkdecorations4 libkdepim4 libkexiv2-7 libkholidays4 libkipi6 libkleo4 libkonq5 libkonq5-templates libkpgp4 libksieve4 libkwineffects1 libloudmouth1-0 liblua50 liblualib50 libmad0 libmimelib4 libmodplug0c2 libmpcdec3 libmsn0.1 libmysqlclient15off libokularcore1 libpackagekit-glib11 libpackagekit-qt11 libphonon4 libplasma3 libpoppler-qt4-3 libpq5 libqca2 libqca2-plugin-ossl libqedje0 libqimageblitz4 libqt3-mt libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqzion0 libraptor1 librasqal1 librdf0 libsearchclient0 libsoprano4 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libstrigiqtdbusclient0 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-common okular okular-extra-backends openoffice.org-kde openoffice.org-style-crystal oxygen-cursor-theme packagekit packagekit-backend-apt phonon phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-widget-network-manager plasma-widget-quickaccess python-dev python-kde4 python-packagekit python-plasma python-qt4 python-qt4-common python-qt4-dbus python-sip4 python2.6-dev qt4-qtconfig quassel quassel-data raptor-utils redland-utils software-properties-kde soprano-daemon speedcrunch strigi-client strigi-daemon system-config-printer-kde systemsettings ttf-dejavu ttf-dejavu-extra update-manager-kde update-notifier-kde && sudo apt-get install ubuntu-desktop

```

---

### Post by num on 2009-05-16
i read the link you provided, but is it possible to keep the native gnome applications including libraries such as ntp which comes with gnome and yet use KDE?

---

### Post by GeekGirl1 on 2009-05-16
(post removed - it did not answer the question asked)

---

### Post by whoop on 2009-05-16
> **num said:**
> i read the link you provided, but is it possible to keep the native gnome applications including libraries such as ntp which comes with gnome and yet use KDE?

I'm not 100% sure what you mean, but installing kde on ubuntu will not remove any of your gnome applications. 
The only "issue" you might be having is that kde and gnome have different applications for the same functionality and you will get them both in your applications menu. 
I never use kde, but I run some kde applications in gnome, there's no problem in doing that.

Hope this helps.

---

### Post by theozzlives on 2009-05-16
> **whoop said:**
> I'm not 100% sure what you mean, but installing kde on ubuntu will not remove any of your gnome applications. 
The only "issue" you might be having is that kde and gnome have different applications for the same functionality and you will get them both in your applications menu. 
I never use kde, but I run some kde applications in gnome, there's no problem in doing that.

Hope this helps.

I think what he's asking is can you have KDE with GNOME apps, not KDE apps. Unfortunately I don't know the answer to that.

---

### Post by num on 2009-05-16
> **theozzlives said:**
> I think what he's asking is can you have KDE with GNOME apps, not KDE apps. Unfortunately I don't know the answer to that.

yeah exactly.

---

### Post by whoop on 2009-05-16
> **num said:**
> yeah exactly.
Well, you can try. just install kde as described above. Afterwards start removing kde applications. I think you'll get pretty close. And if you break it, you'll still have gnome and can still remove kde (or gnome, or whatever)

---

### Post by num on 2009-05-16
i tried it but it doesn't change to KDE just stays Gnome.

---

### Post by Ericyzfr1 on 2009-05-17
I tried it a couple of weeks ago to compare both of them and it worked fine. I was able to select either seesion without any problem and all apps were available under both DE.

---

### Post by num on 2009-05-17
how can i have no session select just one session to switch?

---

### Post by whoop on 2009-05-17
> **num said:**
> i tried it but it doesn't change to KDE just stays Gnome.
After installing kde, when you get to the login screen, instead of logging in immediately, click options and then select session. You will be able to change window manager there. You can change it for a single session or change it to make a certain window manager start by default.

---

### Post by balboost on 2009-05-22
hi,

just to say, please try to be more explicit in the title of your topic next time. thanks in advance.

---

### Post by fballem on 2009-05-22
I think I'm going to regret asking this, but "Why?". The reason that I'm asking is that if the Original Poster wants to use the GNOME and doesn't want to use the KDE applications, then what is the point of installing the KDE desktop?

I'm suspecting that there's a specific requirement that the OP wants to solve, and thinks that installing the KDE desktop will solve the problem. If we understood the actual requirement, then there may be better and easier solutions that will solve the problem.

---

### Post by lukjad on 2009-05-22
First off, there are KDE versions of most GNOME apps. So the best, and simplest thing would be to do a fresh install of Kubuntu. That being said, [this guide]("http://www.taimila.com/?q=node/11") helps make GNOME look like OSX, which, to my untrained eye looks like KDE. At the very least, it could give you a few pointers.

---

### Post by hvacmoose on 2009-05-22
> **num said:**
> i tried it but it doesn't change to KDE just stays Gnome.

Intall KDE as OS.>

then 
sudo apt-get install gnome

you will get a question when done asking if you want to use kdm or gdm

choose kdm and you are set .

This is what i do on every install.

Hope this is what you need.

---

