---
title: "KDE Removal Error"
date: 2010-04-25
forum: Desktop Environments
---

### Post by Dibjibjub on 2010-04-25
I'm trying to remove KDE from my computer and I keep running in to this error code:

"E: Sub-process /usr/bin/dpkg returned an error code (1)"

after I enter the code:

apt-get remove kde

Know what I am doing wrong?

---

### Post by Alan James on 2010-04-25
I think the command is "sudo apt-get remove kde-base". I think you can also do this from synaptic.

---

### Post by Alan James on 2010-04-25
But if you really want to get it all off of your computer try this.

```
sudo apt-get remove adept adept-batch adept-common adept-installer  adept-manager adept-notifier adept-updater akregator amarok amarok-xine  apport-qt ark arts debtags digikam dolphin enscript fftw3  foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine  gwenview hplip-gui hwdb-client-kde ijsgutenprint k3b kaddressbook  kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron  kde-guidance kde-guidance-powermanager kde-icons-mono  kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins  kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth  kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd  kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop  kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt  kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt  kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins  knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole  kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb  kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg  ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash  kubuntu-default-settings kubuntu-desktop kubuntu-docs  kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal  language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0  libaudio2 libavahi-qt3-1 libclucene0 libcluceneindex0 libdbus-qt-1-1c2  libept0 libexiv2-0 libflac++6 libgmp3c2 libgpgme11 libid3tag0 libifp4  libijs-0.35 libimlib2 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b  libkcddb1 libkdcraw1 libkdepim1a libkexiv2-1 libkipi0 libkleopatra1  libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8  libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmimelib1c2a  libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libofa0  libopenexr2c2a libopenobex1 libpoppler-qt2 libpq5 libpth20 libpulse0  libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1  libruby1.8 libsamplerate0 libsearchclient0 libskim0 libsmokeqt1  libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libungif4g  libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1  libxvmc1 mysql-common network-manager-kde networkstatus  openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt  poster psutils pykdeextensions python-kde3 python-qt3 python-qt4  python-qt4-dbus python-sip4 python2.5-dev qca-tls rdiff-backup  restricted-manager-kde ruby ruby1.8 scim-qtimm skim  software-properties-kde speedcrunch strigi-applet strigi-daemon  && sudo apt-get install ubuntu-desktop
```

---

### Post by Dibjibjub on 2010-04-25
> **Alan James said:**
> I think the command is "sudo apt-get remove kde-base". I think you can also do this from synaptic.

I get this error code:
E: Couldn't find package kde-base


> **Alan James said:**
> But if you really want to get it all off of your computer try this.

```
sudo apt-get remove adept adept-batch adept-common adept-installer  adept-manager adept-notifier adept-updater akregator amarok amarok-xine  apport-qt ark arts debtags digikam dolphin enscript fftw3  foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine  gwenview hplip-gui hwdb-client-kde ijsgutenprint k3b kaddressbook  kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron  kde-guidance kde-guidance-powermanager kde-icons-mono  kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins  kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth  kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd  kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop  kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt  kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt  kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins  knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole  kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb  kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg  ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash  kubuntu-default-settings kubuntu-desktop kubuntu-docs  kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal  language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0  libaudio2 libavahi-qt3-1 libclucene0 libcluceneindex0 libdbus-qt-1-1c2  libept0 libexiv2-0 libflac++6 libgmp3c2 libgpgme11 libid3tag0 libifp4  libijs-0.35 libimlib2 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b  libkcddb1 libkdcraw1 libkdepim1a libkexiv2-1 libkipi0 libkleopatra1  libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8  libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmimelib1c2a  libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libofa0  libopenexr2c2a libopenobex1 libpoppler-qt2 libpq5 libpth20 libpulse0  libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1  libruby1.8 libsamplerate0 libsearchclient0 libskim0 libsmokeqt1  libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libungif4g  libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1  libxvmc1 mysql-common network-manager-kde networkstatus  openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt  poster psutils pykdeextensions python-kde3 python-qt3 python-qt4  python-qt4-dbus python-sip4 python2.5-dev qca-tls rdiff-backup  restricted-manager-kde ruby ruby1.8 scim-qtimm skim  software-properties-kde speedcrunch strigi-applet strigi-daemon  && sudo apt-get install ubuntu-desktop
```

Error code:
Package adept is not installed, so not removed
E: Couldn't find package adept-batch

---

### Post by Alan James on 2010-04-26
Did it remove the other packages though? If a package isnt installed just remove it from the command and the whole command should work.

---

### Post by Zorael on 2010-04-26
Those packages are for KDE3 so most should be missing from Karmic repositories. Adept is no longer used, for one. Nor is kde-guidance.

I think the easiest way is to purge **kdelibs5**. All KDE4 apps need that one, so removing it should pull a whole lot down with it. Some may remain, like plugin packages that only recommend the main package they boost.

```
$ sudo aptitude purge kdelibs5
$ sudo aptitude purge ~c
```

---

### Post by Alan James on 2010-04-26
I didn't notice that but yes they are.

I am a little more advanced than a novice and I have always had a hard time completely removing either Gnome or KDE once installed. I always just do a fresh install which works well for me. I recommend it if you have the time.

---

