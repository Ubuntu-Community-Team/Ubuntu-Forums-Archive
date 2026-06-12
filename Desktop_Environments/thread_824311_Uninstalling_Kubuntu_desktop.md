---
title: "Uninstalling Kubuntu desktop"
date: 2008-06-10
forum: Desktop Environments
---

### Post by Tribulation on 2008-06-10
Sorry I didn't put this in my KDE 3 or KDE 4? thread, I can't seem to post there. Every time I go to that topic I see that I'm not logged in. Every time I try to log in it acts like I do but once I return to the forum I find that I am not logged in. I can log in just fine every where else it seems. Anyway, I decided to remove the Kubuntu desktop (I installed using apt-get, I didn't know about aptitude at the time). I tried to remove it using some code it some threads on this forum but it will not go away. 

```
sudo apt-get remove adept akregator amarok amarok-gstreamer ark arts debtags enscript gtk2-engines-gtk-qt gwenview imagemagick ivman kaddressbook kaffeine  kaffeine-gstreamer kamera kappfinder karm katapult kate kaudiocreator kcron kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins  kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdm kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmenuedit kmilo kmix knetworkconf knotes konq-plugins konqueror-nsplugins konserve konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksvg ksysguard ksysguardd ksystemlog kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kwalletmanager kwifimanager kwin libgadu3 libgpgme11 libjpeg-progs libkcal2a libkcddb1 libkdepim1 libkipi0 libkleopatra0a libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 libmimelib1a libopenobex-1.0-0 libpythonize0 libsensors3 libtdb1 openoffice.org2-kde poster psutils python-kde3 python-opengl python2
``` doesn't do anything. I keep getting the message > Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package amarok-gstreamer

---

### Post by Bubba64 on 2008-06-10
So you have kubuntu installed on top of the hardy setup is this correct.

---

### Post by Tribulation on 2008-06-10
It seems so

---

### Post by Bubba64 on 2008-06-10
> **Tribulation said:**
> It seems so

Okay I am trying to find the website that gives that same list, or one like it. Also if you know what day or at least close there is a history in synaptic that will show installs, I think even if installed from the terminal, how did you install.

---

### Post by Tribulation on 2008-06-10
I installed it this morning, I'll see if I can find it in Synaptic.

EDIT: It doesn't seem to be in there. The only thing I see in history is May 2008.

---

### Post by aysiu on 2008-06-10
The command should be ```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts cryptsetup debtags desktop-effects-kde digikam dmsetup dolphin enscript foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hpijs-ppds hplip-gui ijsgutenprint jockey-kde k3b kaddressbook kaffeine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-qtcurve kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-bin-kde3 kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libavcodec1d libavutil1d libclucene0ldbl libdbus-qt-1-1c2 libept0 libexiv2-2 libfftw3-3 libflac++6 libgmp3c2 libgsm1 libifp4 libijs-0.35 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw3 libkdepim1a libkexiv2-3 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmad0 libmimelib1c2a libmodplug0c2 libmpcdec3 libnjb5 libofa0 libpoppler-qt2 libpostproc1d libpq5 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x libxvmc1 network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-dev python-kde3 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 python2.5-dev qca-tls rdiff-backup ruby ruby1.8 scim-bridge-client-qt scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon system-config-printer-kde ttf-arphic-ukai vorbis-tools && sudo apt-get install ubuntu-desktop
``` Where did you get your command from (the one with *amarok-gstreamer* in it)?

It isn't from any of my Pure Gnome pages ([http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome))

---

### Post by Tribulation on 2008-06-10
One quick question, what is the command to restore my splash page to the normal Ubuntu one? I switched it to Kubuntu's by mistake when I installed it.

---

### Post by aysiu on 2008-06-10
> **Tribulation said:**
> One quick question, what is the command to restore my splash page to the normal Ubuntu one? I switched it to Kubuntu's by mistake when I installed it.
```
sudo update-alternatives --config usplash-artwork.so
```

---

### Post by Bubba64 on 2008-06-10
aysiu has the right information, but I was looking at your old posts, and am wondering if you installed with the desktop cd that you were using.

---

### Post by Tribulation on 2008-06-10
No I didn't install with the CD. And also, good news and bad news. The good news is that Kubuntu and all of it's programs are gone. Thanks for your help aysiu. However now when I try to get into add/remove programs I get the message > 
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

When I use the command "Sudo apt-get update" I get > Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy Release.gpg
Ign [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy/main Translation-en_US
Ign [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy/restricted Translation-en_US
Ign [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy/universe Translation-en_US
Ign [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy/multiverse Translation-en_US
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-updates Release.gpg
Ign [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-updates/main Translation-en_US
Ign [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-updates/restricted Translation-en_US
Ign [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-updates/universe Translation-en_US
Ign [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-updates/multiverse Translation-en_US
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-security Release.gpg
Ign [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-security/main Translation-en_US
Ign [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-security/restricted Translation-en_US
Ign [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-security/universe Translation-en_US
Ign [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-security/multiverse Translation-en_US
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy Release
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-updates Release
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-security Release
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy/main Packages
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy/restricted Packages
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy/main Sources
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy/restricted Sources
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy/universe Packages
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy/universe Sources
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy/multiverse Packages
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy/multiverse Sources
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-updates/main Packages
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-updates/restricted Packages
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-updates/main Sources
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-updates/restricted Sources
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-updates/universe Packages
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-updates/universe Sources
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-updates/multiverse Packages
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-updates/multiverse Sources
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-security/main Packages
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-security/restricted Packages
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-security/main Sources
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-security/restricted Sources
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-security/universe Packages
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-security/universe Sources
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-security/multiverse Packages
Hit [http://ubuntu.mirror.rafal.ca](http://ubuntu.mirror.rafal.ca) hardy-security/multiverse Sources
Reading package lists... Done

but when I type in "Sudo apt-get install f" I get > Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfreebob0 libdb4.6++ kdeartwork-misc kdegames-card-data libdc1394-13
  texlive-base texlive-fonts-recommended liblockdev1 libwxgtk2.6-0 ttf-dustin
  libjack0 texlive-common kdeedu-data mysql-common kdeartwork-theme-icon
  libdvbpsi4 kalzium-data texlive-base-bin libxosd2 libmysqlclient15off
  kgeography-data libvlc0 tidy libtidy-0.99-0 gettext ttf-sjfonts cvs
  libtiff-tools kdeartwork-emoticons kdewallpapers libwxbase2.6-0
  klettres-data libopensync0 kstars-data edict libdvdnav4 libiso9660-5
  libdvdread3 libindex0 kanjidic libsidplay1 libid3tag0 libtar indi
  libvcdinfo0 texlive-doc-base libebml0 tex-common libboost-python1.34.1
  libmatroska0 libmpeg2-4 quanta-data libsdl-image1.2 liba52-0.7.4
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  kio-umountwrapper
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
1 not fully installed or removed.
After this operation, 111kB disk space will be freed.
Do you want to continue [Y/n]? 


When I choose yes I see > (Reading database ... 132153 files and directories currently installed.)
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)

EDIT: Nevermind, I fixed it. I had given up hope of trying to figure it out myself so I ignored the problem. I decided to pay a visit to the Update Manager and after I was done updating my software I tried to get back into add/remove applications on a hunch and viola, no problems anymore.

---

