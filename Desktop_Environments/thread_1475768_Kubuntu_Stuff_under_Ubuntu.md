---
title: "Kubuntu Stuff under Ubuntu"
date: 2010-05-07
forum: Desktop Environments
---

### Post by georgf.d on 2010-05-07
Hi There,
i recently installed DigiKam on my Ubuntu 10.04 installation.
As i explored, that some KDE-Apps are also installed i deinstalled digikam again. The Ubuntu software center removed it properly, but now there is still the filebrowser and other stuff from kde on my desktop.
Is there any option to get those "K"-Applications out of my installation. i just use the ubuntu default stuff and dont want to have another filebrowser beside nautilus ...

With best regards, 

georgf.d

---

### Post by kio_http on 2010-05-07
Yes.

to remove all KDE components.
```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts bogofilter bogofilter-bdb bogofilter-common debtags digikam enscript fftw3 gtk-qt-engine gwenview hwdb-client-kde k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kexi kfind kghostview khelpcenter kicker kio-apt kio-locate kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knetworkmanager knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libavahi-compat-libdnssd1 libavahi-qt3-1 libcurl3-gnutls libdbus-qt-1-1c2 libexiv2-0.12 libflac++5c2 libgmp3c2 libgpgme11 libgsl0 libid3tag0 libifp4 libimlib2 libjasper-runtime libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkexiv2-0 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 liblua50 liblualib50 libmeanwhile1 libmimelib1c2a libmodplug0c2 libmpcdec3 libmtp5 libmysqlclient15off libnjb5 libofa0 liboggflac3 libopenexr2c2a libopenobex1 libpcre3 libpoppler1-qt libpq5 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsamplerate0 libskim0 libsmokeqt1 libsqlite0 libtdb1 libtunepimp5 libxine1 libxvmc1 mysql-common networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pmount poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-sip4 python2.5-dev qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch vorbis-tools && sudo apt-get install ubuntu-desktop
```

I'm sorry you had a bad experience with KDE, could you please explain what we can do to improve?

---

### Post by aceracer24 on 2010-05-07
> **georgf.d said:**
> Hi There,
i recently installed DigiKam on my Ubuntu 10.04 installation.
As i explored, that some KDE-Apps are also installed i deinstalled digikam again. The Ubuntu software center removed it properly, but now there is still the filebrowser and other stuff from kde on my desktop.
Is there any option to get those "K"-Applications out of my installation. i just use the ubuntu default stuff and dont want to have another filebrowser beside nautilus ...

With best regards, 

georgf.d

There are certain application that are KDE dependant and when you install them, they will install certain KDE applications as well. The same happens if you use Kubuntu and install something gnome dependant. Even if you later uninstall that specific application, most of the other dependancies will remain. It's just one of those things that you have to get used to. That said, as was instructed above, that should remove all of the KDE stuff.

---

### Post by georgf.d on 2010-05-07
Hi,
first of all, thanks for the fast response :)
Mainly im not Against "KDE" but, it doesnt fit into your enviroment when you ge tother applications in it, which run on a totally different Base.
My first thought was, why are they installing KDE Apps to make this programm run, but on the one side of using linux, or better *buntu is, you can do everything, but there are many applications which do the same.
So Digikam installed a new Filebrowser...

There should be some "GLOBAL SUPPORT....

though you could use nautilus with digikam and Konqueror with gnome well. Maybe thats the bad side of the "Software Freedom" :D

Okay im trying that remove thing out and report. Thanks for your answers...

---

### Post by Zorael on 2010-05-08
That's a quirk that comes with virtual packages and dependencies. **kubuntu-desktop** as a package contains basically nothing, but because it depends on the applications that build up the Kubuntu "suite" those will get installed, and that's what you'll end up with. Turning it around, however, those applications don't depend on kubuntu-desktop. So removing kubuntu-desktop will still leave you with all of them installed.

Moreover, as of semi-recently (Jaunty?), apt is set up to consider recommended packages as dependencies. So if the Digikam package recommends Gwenview, as they're both related to pictures and images and work well with eachother - and Gwenview recommends Dolphin, since they're both filesystem navigators and work well with eachother - and Dolphin recommends X that recommends Y that recommends Z that recommends KTorrent... ...then installing Digikam will also tag KTorrent for installation. I think they reworked it now, but it used to be that installing Firefox onto Kubuntu made it install PulseAudio at the same time, unless you changed the setting or specifically told it to ignore recommends.

> **kio_http said:**
> to remove all KDE components.
```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts bogofilter bogofilter-bdb bogofilter-common debtags digikam enscript fftw3 gtk-qt-engine gwenview hwdb-client-kde k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kexi kfind kghostview khelpcenter kicker kio-apt kio-locate kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knetworkmanager knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libavahi-compat-libdnssd1 libavahi-qt3-1 libcurl3-gnutls libdbus-qt-1-1c2 libexiv2-0.12 libflac++5c2 libgmp3c2 libgpgme11 libgsl0 libid3tag0 libifp4 libimlib2 libjasper-runtime libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkexiv2-0 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 liblua50 liblualib50 libmeanwhile1 libmimelib1c2a libmodplug0c2 libmpcdec3 libmtp5 libmysqlclient15off libnjb5 libofa0 liboggflac3 libopenexr2c2a libopenobex1 libpcre3 libpoppler1-qt libpq5 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsamplerate0 libskim0 libsmokeqt1 libsqlite0 libtdb1 libtunepimp5 libxine1 libxvmc1 mysql-common networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pmount poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-sip4 python2.5-dev qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch vorbis-tools && sudo apt-get install ubuntu-desktop
```
That list is for KDE3 and won't work with KDE4 (and apt-get). It will halt when trying to remove Adept. It *may* work if you use aptitude, not sure.

---

### Post by kio_http on 2010-05-08
> **Zorael said:**
> That's a quirk that comes with virtual packages and dependencies. **kubuntu-desktop** as a package contains basically nothing, but because it depends on the applications that build up the Kubuntu "suite" those will get installed, and that's what you'll end up with. Turning it around, however, those applications don't depend on kubuntu-desktop. So removing kubuntu-desktop will still leave you with all of them installed.

Moreover, as of semi-recently (Jaunty?), apt is set up to consider recommended packages as dependencies. So if the Digikam package recommends Gwenview, as they're both related to pictures and images and work well with eachother - and Gwenview recommends Dolphin, since they're both filesystem navigators and work well with eachother - and Dolphin recommends X that recommends Y that recommends Z that recommends KTorrent... ...then installing Digikam will also tag KTorrent for installation. I think they reworked it now, but it used to be that installing Firefox onto Kubuntu made it install PulseAudio at the same time, unless you changed the setting or specifically told it to ignore recommends.


That list is for KDE3 and won't work with KDE4 (and apt-get). It will halt when trying to remove Adept. It *may* work if you use aptitude, not sure.

It will work. Before kde 4 packages has -kde4 at the end. Now KDE4 is default. Apt-get will just say package x not found so not removed and proceed.

---

### Post by Zorael on 2010-05-08
> **kio_http said:**
> It will work. Before kde 4 packages has -kde4 at the end. Now KDE4 is default. Apt-get will just say package x not found so not removed and proceed.
```
zorael@lethe:~$ sudo apt-get remove *<stuff>*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adept is not installed, so not removed
E: Couldn't find package adept-batch
zorael@lethe:~$
```

---

### Post by kio_http on 2010-05-08
> **Zorael said:**
> ```
zorael@lethe:~$ sudo apt-get remove *<stuff>*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adept is not installed, so not removed
E: Couldn't find package adept-batch
zorael@lethe:~$
```

Odd I could have sworn it worked, maybe older apt-get versions. Because I remember doing this multiple times many years back.

---

