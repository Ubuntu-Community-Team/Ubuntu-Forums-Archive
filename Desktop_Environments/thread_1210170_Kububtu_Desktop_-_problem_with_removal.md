---
title: "Kububtu Desktop - problem with removal"
date: 2009-07-11
forum: Desktop Environments
---

### Post by aladdinshams on 2009-07-11
[B][SIZE="3"][FONT="Tahoma"]am using Ubuntu 8.04 and installed Kubuntu-desktop .. and while trying to remove something wrong happened.

first I pasted this command at the terminal:

```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts cryptsetup debtags desktop-effects-kde digikam dmsetup dolphin enscript foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hpijs-ppds hplip-gui ijsgutenprint jockey-kde k3b kaddressbook kaffeine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-qtcurve kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-bin-kde3 kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libavcodec1d libavutil1d libclucene0ldbl libdbus-qt-1-1c2 libept0 libexiv2-2 libfftw3-3 libflac++6 libgmp3c2 libgsm1 libifp4 libijs-0.35 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw3 libkdepim1a libkexiv2-3 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmad0 libmimelib1c2a libmodplug0c2 libmpcdec3 libnjb5 libofa0 libpoppler-qt2 libpostproc1d libpq5 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x libxvmc1 network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-dev python-kde3 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 python2.5-dev qca-tls rdiff-backup ruby ruby1.8 scim-bridge-client-qt scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon system-config-printer-kde ttf-arphic-ukai vorbis-tools && sudo apt-get install ubuntu-desktop
```

it started to remove it and when it came to switching kdm to kgm I chose to remove kdm and didn't wait, and restarted the computer to find Kubuntu is still existing.

repeated the process from beginning and typed the same command I mentioned above, I got this message:


```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
``` 

I typed the requested command:

```
dpkg --configure -a
```

and got this message:

```
dpkg: requested operation requires superuser privilege
```


I can't understand the message and don't know what should I do???

Thanks in advance
 [/FONT][/SIZE][/B]

---

### Post by tacantara on 2009-07-11
All I can deduce from that is that the command (dpkg --configure -a) needs to be prefixed with sudo (sudo dpkg --configure -a), unless I'm not reading enough into the problem.  Have you tried that yet?

---

### Post by cyzak on 2009-07-11
Not sure about the whole problem but last error 
dpkg: requested operation requires superuser privilege

just means that you have to run dpkg with sudo. 
Something of the sort
sudo dpkg --configure -a

---

### Post by aladdinshams on 2009-07-11
THanks everybody :) it has worked and Kubuntu desktop is completely removed:)

---

### Post by tacantara on 2009-07-11
No problem :)  What helps me to remember the sudo command and how it is usd is that sudo is short for "super user do."  Thus, if I get an error in the terminal that requires super user privilege, I add sudo to whatever I'm using.
 
Keir Thomas' "Ubuntu Pocket Guide" is great for figuring out how the terminal commands work and how they are named.  You can download it for free.  Just run the title through a Google search and you should find a link for the PDF download version.

---

