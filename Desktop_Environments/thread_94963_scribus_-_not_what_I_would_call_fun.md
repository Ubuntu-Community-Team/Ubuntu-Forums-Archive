---
title: "scribus - not what I would call fun"
date: 2005-11-25
forum: Desktop Environments
---

### Post by hoodwink on 2005-11-25
Hmmm? All I wanted to do was install scribus, like on any other distro. Got the following:

---

Suggested packages:
  libqt3-mt-psql libqt3-mt-mysql libqt3-mt-odbc pinentry-doc scribus-template
  scribus-doc
The following packages will be REMOVED:
  akode akregator amarok amarok-arts ark arts artsbuilder dcoprss gwenview juk k3b
  k3blibs kaddressbook kaffeine kalarm kamera kappfinder karm kate kaudiocreator kcalc
  kcharselect kcontrol kcron kde-style-lipstik kdeadmin kdeadmin-kfile-plugins
  kdebase-bin kdegraphics kdegraphics-kfile-plugins kdelibs-bin kdelibs4 kdemultimedia
  kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins
  kdenetwork kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kfile-plugins kdepim-kio-plugins kdepim-wizards kdeprint kdesktop kdeutils kdm
  kfind kfloppy kgamma kghostview kgpg khelpcenter kicker kitchensync klaptopdaemon
  klipper kmenuedit kmilo kmix kmrml knetworkconf knewsticker knode knotes kolourpaint
  konqueror-nsplugins konserve konsole konsolekalendar kontact konversation kooka kopete
  korganizer kpager kpdf kpersonalizer kpf kpilot kppp krdc kregexpeditor krfb kscd
  kscreensaver ksim ksmserver ksnapshot ksplash ksvg ksync ksysguard ktnef
  kubuntu-default-settings kubuntu-docs kuser kwalletmanager kwifimanager kwin libarts1
  libarts1-audiofile libarts1-xine libkcal2a libkcddb1 libkdepim1 libkgantt0 libkipi0
  libkleopatra0a libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0
  libktnef1 libmimelib1a libqt3c102-mt librss1 networkstatus secpolicy
The following NEW packages will be installed:
  libqt3-mt scribus
The following packages will be upgraded:
  pinentry-qt
1 upgraded, 2 newly installed, 120 to remove and 50 not upgraded.
Need to get 8315kB of archives.
After unpacking 240MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

---

All I can say is, WTF?

---

### Post by cwaldbieser on 2005-11-25
[QUOTE=hoodwink]Hmmm? All I wanted to do was install scribus, like on any other distro. Got the following:

---

Suggested packages:
  libqt3-mt-psql libqt3-mt-mysql libqt3-mt-odbc pinentry-doc scribus-template
  scribus-doc
The following packages will be REMOVED:
  akode akregator amarok amarok-arts ark arts artsbuilder dcoprss gwenview juk k3b
  k3blibs kaddressbook kaffeine kalarm kamera kappfinder karm kate kaudiocreator kcalc
  kcharselect kcontrol kcron kde-style-lipstik kdeadmin kdeadmin-kfile-plugins
  kdebase-bin kdegraphics kdegraphics-kfile-plugins kdelibs-bin kdelibs4 kdemultimedia
  kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins
  kdenetwork kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kfile-plugins kdepim-kio-plugins kdepim-wizards kdeprint kdesktop kdeutils kdm
  kfind kfloppy kgamma kghostview kgpg khelpcenter kicker kitchensync klaptopdaemon
  klipper kmenuedit kmilo kmix kmrml knetworkconf knewsticker knode knotes kolourpaint
  konqueror-nsplugins konserve konsole konsolekalendar kontact konversation kooka kopete
  korganizer kpager kpdf kpersonalizer kpf kpilot kppp krdc kregexpeditor krfb kscd
  kscreensaver ksim ksmserver ksnapshot ksplash ksvg ksync ksysguard ktnef
  kubuntu-default-settings kubuntu-docs kuser kwalletmanager kwifimanager kwin libarts1
  libarts1-audiofile libarts1-xine libkcal2a libkcddb1 libkdepim1 libkgantt0 libkipi0
  libkleopatra0a libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0
  libktnef1 libmimelib1a libqt3c102-mt librss1 networkstatus secpolicy
The following NEW packages will be installed:
  libqt3-mt scribus
The following packages will be upgraded:
  pinentry-qt
1 upgraded, 2 newly installed, 120 to remove and 50 not upgraded.
Need to get 8315kB of archives.
After unpacking 240MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

---

All I can say is, WTF?[/QUOTE]

I think what it is saying is that the version of scribus you want depends on a version of QT that will force you to uninstall a bunk of other KDE apps that depend on the old QT library.  I am not sure where the "libqt3c102-mt" package you have came from, but it looks like the version of scribus you want to use depends on a newer version.

---

### Post by GeneralZod on 2005-11-25
It's fine here.  How are you trying to install it? Have you manually downloaded a .deb from somewhere, or are you using the one in the repos? If the latter, can you post your sources.list?

---

### Post by hoodwink on 2005-11-25
[QUOTE=cwaldbieser]I think what it is saying is that the version of scribus you want depends on a version of QT that will force you to uninstall a bunk of other KDE apps that depend on the old QT library.  I am not sure where the "libqt3c102-mt" package you have came from, but it looks like the version of scribus you want to use depends on a newer version.[/QUOTE]

Indeed. Unfortunately the 'apt-get install' does not tell me which of the repositories this came from - I would suspect universe. Does anyone have a clue where I could find a version of scrbus that does not attempt to take down all of kde with this type of qt dependancy?

---

### Post by hoodwink on 2005-11-25
[QUOTE=GeneralZod]It's fine here.  How are you trying to install it? Have you manually downloaded a .deb from somewhere, or are you using the one in the repos? If the latter, can you post your sources.list?[/QUOTE]
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

---

I'll try again without multiverse.

---

### Post by GeneralZod on 2005-11-25
[QUOTE=hoodwink]
I'll try again without multiverse.[/QUOTE]

No, it shouldn't be that - I have mulitverse in my sources.list.  Hmmm...very odd.

Here's mine, just in case it helps.  It's a bit of a mess, though!

```

#deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 


#deb http://gb.archive.ubuntu.com/ubuntu/ breezy main restricted 
#deb-src http://gb.archive.ubuntu.com/ubuntu/ breezy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
#deb http://gb.archive.ubuntu.com/ubuntu/ breezy-updates main restricted 
#deb-src http://gb.archive.ubuntu.com/ubuntu/ breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.


deb http://gb.archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse 
deb http://gb.archive.ubuntu.com/ubuntu/ breezy-security universe main restricted multiverse 
deb http://gb.archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse 

deb-src http://gb.archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse 
deb-src http://gb.archive.ubuntu.com/ubuntu/ breezy-security universe main restricted multiverse 
deb-src http://gb.archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse 




## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse 
# deb-src http://gb.archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted 

deb http://security.ubuntu.com/ubuntu/ breezy-security universe 
deb-src http://security.ubuntu.com/ubuntu/ breezy-security universe 

#w32codecs
# deb ftp://ftp.nerim.net/debian-marillat/ etch main  

deb http://soulmachine.net/breezy unstable/

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse

deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free


```

---

