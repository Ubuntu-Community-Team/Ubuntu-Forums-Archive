---
title: "problems installing kde on ubuntu"
date: 2007-01-11
forum: Desktop Environments
---

### Post by holdyn wolf on 2007-01-11
Alright I can't get kde to install.  I have no clue what I am doing wrong.  Followed instructions I found online.  Running Ubuntu 6.06 at the moment.  Here's what I get when I try and install using

sudo apt-get install kubuntu-desktop

in Terminal.

> Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: adept but it is not going to be installed
                   Depends: akregator but it is not installable
                   Depends: amarok but it is not going to be installed
                   Depends: ark but it is not installable
                   Depends: arts but it is not installable
                   Depends: bogofilter but it is not installable
                   Depends: gtk2-engines-gtk-qt but it is not installable
                   Depends: gwenview but it is not installable
                   Depends: k3b but it is not going to be installed
                   Depends: kaddressbook but it is not installable
                   Depends: kaffeine-xine but it is not installable
                   Depends: kamera but it is not installable
                   Depends: karm but it is not installable
                   Depends: katapult but it is not installable
                   Depends: kate but it is not going to be installed
                   Depends: kaudiocreator but it is not installable
                   Depends: kcontrol but it is not going to be installed
                   Depends: kcron but it is not installable
                   Depends: kde-guidance but it is not going to be installed
                   Depends: kde-systemsettings but it is not installable
                   Depends: kdeadmin-kfile-plugins but it is not installable
                   Depends: kdebase-kio-plugins but it is not going to be installed
                   Depends: kdebluetooth but it is not installable
                   Depends: kdegraphics-kfile-plugins but it is not installable
                   Depends: kdemultimedia-kfile-plugins but it is not installable
                   Depends: kdemultimedia-kio-plugins but it is not installable
                   Depends: kdenetwork-filesharing but it is not going to be installed
                   Depends: kdenetwork-kfile-plugins but it is not going to be installed
                   Depends: kdepasswd but it is not going to be installed
                   Depends: kdepim-kio-plugins but it is not installable
                   Depends: kdepim-wizards but it is not installable
                   Depends: kdeprint but it is not going to be installed
                   Depends: kdesktop but it is not going to be installed
                   Depends: kdm but it is not going to be installed
                   Depends: kdnssd but it is not going to be installed
                   Depends: keep but it is not installable
                   Depends: kfind but it is not going to be installed
                   Depends: kghostview but it is not installable
                   Depends: khelpcenter but it is not going to be installed
                   Depends: kicker but it is not going to be installed
                   Depends: kio-apt but it is not installable
                   Depends: kio-locate but it is not installable
                   Depends: klaptopdaemon
                   Depends: klipper but it is not going to be installed
                   Depends: kmail but it is not installable
                   Depends: kmailcvt but it is not installable
                   Depends: kmenuedit but it is not going to be installed
                   Depends: kmilo but it is not installable
                   Depends: kmix but it is not installable
                   Depends: kmplayer-konq-plugins but it is not installable
                   Depends: knetworkconf but it is not installable
                   Depends: knotes but it is not installable
                   Depends: konq-plugins but it is not installable
                   Depends: konqueror but it is not going to be installed
                   Depends: konqueror-nsplugins but it is not going to be installed
                   Depends: konsole but it is not going to be installed
                   Depends: kontact but it is not installable
                   Depends: konversation but it is not going to be installed
                   Depends: kooka but it is not installable
                   Depends: kopete but it is not going to be installed
                   Depends: korganizer but it is not installable
                   Depends: kpdf but it is not installable
                   Depends: kpf but it is not going to be installed
                   Depends: kppp but it is not going to be installed
                   Depends: krdc but it is not going to be installed
                   Depends: krfb but it is not going to be installed
                   Depends: krita but it is not installable
                   Depends: kscd but it is not installable
                   Depends: kscreensaver but it is not installable
                   Depends: ksmserver but it is not going to be installed
                   Depends: ksnapshot but it is not installable
                   Depends: ksplash but it is not going to be installed
                   Depends: ksplash-engine-moodin but it is not installable
                   Depends: ksvg but it is not installable
                   Depends: ksysguard but it is not going to be installed
                   Depends: ksystemlog but it is not installable
                   Depends: ktorrent but it is not going to be installed
                   Depends: kubuntu-default-settings but it is not going to be installed
                   Depends: kubuntu-docs but it is not going to be installed
                   Depends: kubuntu-konqueror-shortcuts but it is not installable
                   Depends: kwalletmanager but it is not installable
                   Depends: kwin but it is not going to be installed
                   Depends: language-selector-qt but it is not going to be installed
                   Depends: libarts1-akode but it is not installable
                   Depends: libnss-mdns but it is not installable
                   Depends: openoffice.org-kde but it is not going to be installed
                   Depends: qca-tls but it is not installable
                   Depends: scim-qtimm but it is not installable
                   Depends: skim but it is not installable
                   Depends: speedcrunch but it is not installable
                   Depends: vorbis-tools but it is not installable
                   Depends: wlassistant but it is not installable
E: Broken packages

Any help would be appreciated.

---

### Post by holdyn wolf on 2007-01-11
Alright so then I go and try sudo aptitude install kubuntu-desktop

After making sure aptitude is updated and this is what I get: 

> holdynwolf@ubuntu:~$ sudo aptitude install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  adept amarok avahi-daemon kde-guidance kdebase-kio-plugins kdelibs-bin
  kdelibs4c2a kdenetwork-filesharing kdeprint kicker ksysguardd
  kubuntu-default-settings kubuntu-desktop kwin language-selector-qt
  libk3b2 libkonq4 libxine-extracodecs libxine-main1
The following NEW packages will be automatically installed:
  amarok-xine k3b kate kcontrol kdebase-bin kdebase-data kdelibs-data
  kdenetwork-kfile-plugins kdepasswd kdesktop kdm kdnssd kfind khelpcenter
  klipper kmenuedit konqueror konqueror-nsplugins konsole konversation
  kopete kpersonalizer kpf kpowersave kppp krdc kregexpeditor krfb
  ksmserver ksplash ksysguard ktorrent kubuntu-artwork-usplash kubuntu-docs
  libavahi-core4 libavahi-qt3-1 libdbus-qt-1-1c2 libifp4 libiso9660-4
  libjasper-runtime libpcre3 libqt3-mt libruby1.8 libtunepimp3 libvcdinfo0
  libvisual-0.4-0 libvisual-0.4-plugins openoffice.org-kde vcdimager
The following NEW packages will be installed:
  amarok-xine k3b kate kcontrol kdebase-bin kdebase-data kdelibs-data
  kdenetwork-kfile-plugins kdepasswd kdesktop kdm kdnssd kfind khelpcenter
  klipper kmenuedit konqueror konqueror-nsplugins konsole konversation
  kopete kpersonalizer kpf kpowersave kppp krdc kregexpeditor krfb
  ksmserver ksplash ksysguard ktorrent kubuntu-artwork-usplash kubuntu-docs
  libavahi-core4 libavahi-qt3-1 libdbus-qt-1-1c2 libifp4 libiso9660-4
  libjasper-runtime libpcre3 libqt3-mt libruby1.8 libtunepimp3 libvcdinfo0
  libvisual-0.4-0 libvisual-0.4-plugins openoffice.org-kde vcdimager
0 packages upgraded, 68 newly installed, 0 to remove and 0 not upgraded.
Need to get 112MB/112MB of archives. After unpacking 307MB will be used.
The following packages have unmet dependencies:
  kubuntu-default-settings: Depends: kde-style-lipstik which is a virtual package.
                            Depends: ksplash-engine-moodin which is a virtual package.
                            Depends: kwin-style-crystal which is a virtual package.
  kdelibs4c2a: Depends: libarts1c2a (>= 1.5.2) which is a virtual package.
               Depends: libopenexr2c2a (>= 1.2.2) which is a virtual package.
  kdeprint: Depends: enscript which is a virtual package.
            Depends: poster which is a virtual package.
            Depends: psutils which is a virtual package.
  kwin: Depends: libxcomposite1 which is a virtual package.
  libxine-extracodecs: Depends: libmad0 (>= 0.15.1b) which is a virtual package.  libk3b2: Depends: libartsc0 (>= 1.5.2-0) which is a virtual package.
           Depends: libflac++5c2 which is a virtual package.
           Depends: libmpcdec3 which is a virtual package.
  avahi-daemon: Depends: libdaemon0 which is a virtual package.
  kicker: Depends: libxcomposite1 which is a virtual package.
  kubuntu-desktop: Depends: akregator which is a virtual package.
                   Depends: ark which is a virtual package.
                   Depends: arts which is a virtual package.
                   Depends: bogofilter which is a virtual package.
                   Depends: gtk2-engines-gtk-qt which is a virtual package.
                   Depends: gwenview which is a virtual package.
                   Depends: kaddressbook which is a virtual package.
                   Depends: kaffeine-xine which is a virtual package.
                   Depends: kamera which is a virtual package.
                   Depends: karm which is a virtual package.
                   Depends: katapult which is a virtual package.
                   Depends: kaudiocreator which is a virtual package.
                   Depends: kcron which is a virtual package.
                   Depends: kde-systemsettings which is a virtual package.
                   Depends: kdeadmin-kfile-plugins which is a virtual package.
                   Depends: kdebluetooth which is a virtual package.
                   Depends: kdegraphics-kfile-plugins which is a virtual package.
                   Depends: kdemultimedia-kfile-plugins which is a virtual package.
                   Depends: kdemultimedia-kio-plugins which is a virtual package.
                   Depends: kdepim-kio-plugins which is a virtual package.
                   Depends: kdepim-wizards which is a virtual package.
                   Depends: keep which is a virtual package.
                   Depends: kghostview which is a virtual package.
                   Depends: kio-apt which is a virtual package.
                   Depends: kio-locate which is a virtual package.
                   Depends: kmail which is a virtual package.
                   Depends: kmailcvt which is a virtual package.
                   Depends: kmilo which is a virtual package.
                   Depends: kmix which is a virtual package.
                   Depends: kmplayer-konq-plugins which is a virtual package.
                   Depends: knetworkconf which is a virtual package.
                   Depends: knotes which is a virtual package.
                   Depends: konq-plugins which is a virtual package.
                   Depends: kontact which is a virtual package.
                   Depends: kooka which is a virtual package.
                   Depends: korganizer which is a virtual package.
                   Depends: kpdf which is a virtual package.
                   Depends: krita which is a virtual package.
                   Depends: kscd which is a virtual package.
                   Depends: kscreensaver which is a virtual package.
                   Depends: ksnapshot which is a virtual package.
                   Depends: ksplash-engine-moodin which is a virtual package.
                   Depends: ksvg which is a virtual package.
                   Depends: ksystemlog which is a virtual package.
                   Depends: kubuntu-konqueror-shortcuts which is a virtual package.
                   Depends: kwalletmanager which is a virtual package.
                   Depends: libarts1-akode which is a virtual package.
                   Depends: libnss-mdns which is a virtual package.
                   Depends: qca-tls which is a virtual package.
                   Depends: scim-qtimm which is a virtual package.
                   Depends: skim which is a virtual package.
                   Depends: speedcrunch which is a virtual package.
                   Depends: vorbis-tools which is a virtual package.
                   Depends: wlassistant which is a virtual package.
  adept: Depends: debtags which is a virtual package.
         Depends: libtdb1 which is a virtual package.
  kdebase-kio-plugins: Depends: libopenexr2c2a (>= 1.2.2) which is a virtual package.
  libkonq4: Depends: libarts1c2a (>= 1.5.2) which is a virtual package.
  libxine-main1: Depends: libmodplug0c2 (>= 1:0.7-4.1) which is a virtual package.
                 Depends: libxvmc1 which is a virtual package.
  amarok: Depends: ruby which is a virtual package.
          Depends: python-qt3 which is a virtual package.
  kdenetwork-filesharing: Depends: perl-suid which is a virtual package.
  kde-guidance: Depends: libpythonize0 which is a virtual package.
                Depends: pykdeextensions which is a virtual package.
                Depends: python-kde3 which is a virtual package.
  ksysguardd: Depends: libsensors3 (>= 1:2.9.2) which is a virtual package.
  kdelibs-bin: Depends: menu-xdg which is a virtual package.
  language-selector-qt: Depends: python2.4-qt3 which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
adept [Not Installed]
amarok [Not Installed]
amarok-xine [Not Installed]
avahi-daemon [Not Installed]
k3b [Not Installed]
kate [Not Installed]
kcontrol [Not Installed]
kde-guidance [Not Installed]
kdebase-bin [Not Installed]
kdebase-kio-plugins [Not Installed]
kdelibs-bin [Not Installed]
kdelibs4c2a [Not Installed]
kdenetwork-filesharing [Not Installed]
kdenetwork-kfile-plugins [Not Installed]
kdepasswd [Not Installed]
kdeprint [Not Installed]
kdesktop [Not Installed]
kdm [Not Installed]
kdnssd [Not Installed]
kfind [Not Installed]
khelpcenter [Not Installed]
kicker [Not Installed]
klipper [Not Installed]
kmenuedit [Not Installed]
konqueror [Not Installed]
konqueror-nsplugins [Not Installed]
konsole [Not Installed]
konversation [Not Installed]
kopete [Not Installed]
kpersonalizer [Not Installed]
kpf [Not Installed]
kpowersave [Not Installed]
kppp [Not Installed]
krdc [Not Installed]
kregexpeditor [Not Installed]
krfb [Not Installed]
ksmserver [Not Installed]
ksplash [Not Installed]
ksysguard [Not Installed]
ksysguardd [Not Installed]
ktorrent [Not Installed]
kubuntu-default-settings [Not Installed]
kubuntu-desktop [Not Installed]
kubuntu-docs [Not Installed]
kwin [Not Installed]
language-selector-qt [Not Installed]
libk3b2 [Not Installed]
libkonq4 [Not Installed]
libxine-extracodecs [Not Installed]
libxine-main1 [Not Installed]
openoffice.org-kde [Not Installed]

Score is 449

Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done

Doint a cat /etc/apt/sources.list  

gives me: 

> #
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by Jackp90 on 2008-04-19
I am coming up with the same problem only not as many error messages as you mine reads:

robert@laptop01:~$ sudo apt-get install kubuntu-desktop
[sudo] password for robert:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: kdebase-kio-plugins but it is not going to be installed
                   Depends: kdesktop but it is not going to be installed
                   Depends: konq-plugins but it is not going to be installed
                   Recommends: amarok but it is not going to be installed
                   Recommends: digikam but it is not going to be installed
                   Recommends: kmail but it is not going to be installed
                   Recommends: kmailcvt but it is not going to be installed
                   Recommends: kmplayer-konq-plugins but it is not going to be installed
                   Recommends: konqueror but it is not going to be installed
                   Recommends: konqueror-nsplugins but it is not going to be installed
                   Recommends: kontact but it is not going to be installed
                   Recommends: kubuntu-konqueror-shortcuts but it is not going to be installed
                   Recommends: strigi-applet but it is not going to be installed
                   Recommends: strigi-daemon but it is not going to be installed
E: Broken packages
robert@laptop01:~$

Did you ever figure out what the problem was?

---

