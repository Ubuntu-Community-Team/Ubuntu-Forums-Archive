---
title: "Cannot install kdelibs4-dev after upgrade to kde 3.5"
date: 2006-01-23
forum: Desktop Environments
---

### Post by mlomker on 2006-01-23
I have that package installed on my box, so I know it is possible.  I'd recommend removing all 3rd party repositories from your configuration and then updating again.  3rd party repos will often have versions that conflict with the Ubuntu ones.  Attach or post your sources.list if you're not sure...

---

### Post by alonso on 2006-01-23
Hi,

I need kdelibs4-dev for compiling rosegarden-1.2. I have upgraded to kde 3.5 using these instructions:

[http://kubuntu.org/announcements/kde-35.php](http://kubuntu.org/announcements/kde-35.php)

Now, when I try to install kdelibs4-dev I get the following message:

```

@ubuntu:/tmp$ sudo apt-get install kdelibs4-dev
Reading package lists... Done
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
  kdelibs4-dev: Depends: libfam-dev
E: Broken packages

```

Now, if I try to install libfam-dev, I get the following message:
```

@ubuntu:/tmp$ sudo apt-get install libfam-dev
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libfam0
Recommended packages:
  fam
The following packages will be REMOVED:
  adept akregator amarok amarok-gstreamer amarok-xine amor ark artsbuilder
  atlantik atlantikdesigner cervisia dcoprss digikam eclipse-jdt
  eclipse-jdt-common eclipse-pde eclipse-pde-common eclipse-platform
  eclipse-platform-common eclipse-rcp eclipse-sdk eyesapplet fifteenapplet
  gamin gstreamer0.8-gnomevfs gstreamer0.8-plugins gtk2-engines-gtk-qt
  gwenview juk k3b k3blibs kaboodle kaddressbook kaddressbook-plugins kaffeine
  kaffeine-gstreamer kamera kappfinder karm kasteroids katapult kate
  kate-plugins katomic kaudiocreator kbabel kbackgammon kbattleship kblackbox
  kbounce kbugbuster kcachegrind kcalc kcharselect kcoloredit kcontrol kcron
  kdat kde-guidance kde-style-lipstik kde-systemsettings kdeaddons
  kdeaddons-kfile-plugins kdeadmin kdeadmin-kfile-plugins kdeartwork
  kdeartwork-style kdeartwork-theme-window kdebase kdebase-bin
  kdebase-kio-plugins kdebluetooth kdegames kdegraphics
  kdegraphics-kfile-plugins kdelibs kdelibs-bin kdelibs4c2 kdelirc
  kdemultimedia kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins
  kdemultimedia-kio-plugins kdenetwork kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdeprint
  kdesdk-kfile-plugins kdesdk-misc kdesktop kdessh kdetoys kdeutils kdf kdict
  kdm kdvi kedit kenolaba kfax kfaxview kfind kfloppy kfouleggs kgamma kget
  kghostview kgoldrunner kgpg khelpcenter khexedit kicker kicker-applets
  kiconedit kile kio-apt kio-locate kjots kjumpingcube klaptopdaemon klickety
  klines klipper kmahjongg kmail kmenuedit kmid kmilo kmines kmix kmoon kmrml
  kmtrace knetworkconf knewsticker knotes kodo koffice-data koffice-libs kolf
  kolourpaint kompare konq-plugins konqueror konqueror-nsplugins konquest
  konserve konsole kontact konversation kooka kopete korganizer kpackage
  kpager kpat kpdf kpersonalizer kpf kpoker kpovmodeler kppp krdc krec
  kregexpeditor kreversi krfb krita kruler ksame kscd kscreensaver
  kscreensaver-xsavers kshisen ksig ksim ksirc ksirtet ksmiletris ksmserver
  ksnake ksnapshot ksokoban kspaceduel ksplash ksvg ksysguard ksystemlog ksysv
  kteatime ktimer ktip ktron ktuberling ktux kubuntu-default-settings
  kubuntu-docs kubuntu-konqueror-shortcuts kuickshow kuiviewer kuser kview
  kviewshell kwalletmanager kweather kwifimanager kwin kwin4 kworldclock
  libarts1-akode libarts1-xine libbonoboui2-0 libcvsservice0 libdbus-qt-1-1c2
  libgamin0 libgnome2-0 libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common
  libkcal2b libkcddb1 libkdegames1 libkdepim1a libkexif1 libkipi0
  libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1
  libkscan1 libksieve0 libktnef1 libmimelib1c2 librss1 libswt3.1-gtk-java
  libswt3.1-gtk-jni libwvstreams4.0c2-extras lskat noatun noatun-plugins nvu
  openoffice.org2-kde python-kde3 python2.4-gamin python2.4-kde3 rosegarden4
  sanekonsole secpolicy superkaramba umbrello vimpart wvdial
The following NEW packages will be installed:
  libfam-dev libfam0
0 upgraded, 2 newly installed, 255 to remove and 1 not upgraded.
Need to get 60.6kB of archives.
After unpacking 582MB disk space will be freed.
Do you want to continue [Y/n]? n

```

What can I do?

BR, 
    A

---

### Post by alonso on 2006-01-24
Hi,

I did remove all third party repositories, but it did not help.

Could it be the wrong version of libgamin? 
I once upgraded libgamin from 0.15 (breezy) to 0.17 (dapper) using these instructions:

[http://www.ubuntuforums.org/showthread.php?t=98885&highlight=libgamin](http://www.ubuntuforums.org/showthread.php?t=98885&highlight=libgamin)

I removed all third parties from my sources.lst:
```

deb     http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 

deb     http://archive.ubuntu.com/ubuntu breezy main restricted 
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted 

deb     http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse 


## Major bug fix updates produced after the final release of the
## distribution.
deb     http://archive.ubuntu.com/ubuntu breezy-updates main restricted 
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted 


deb     http://kubuntu.org/packages/kde35 breezy main
deb-src http://kubuntu.org/packages/kde35 breezy main

deb http://security.ubuntu.com/ubuntu breezy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted 

deb http://security.ubuntu.com/ubuntu breezy-security universe 
deb-src http://security.ubuntu.com/ubuntu breezy-security universe 

```

(There few duplicates, but it should not hurt)

Now I still get the same errors as before. At some point, when I was experimenting with less repositories I got an error about libgamin...

```
sudo apt-get install libfam-dev
Reading package lists... Done
Building dependency tree... Done
Note, selecting libgamin-dev instead of libfam-dev
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgamin-dev: Depends: libgamin0 (= 0.1.5-0ubuntu1) but 0.1.7-2ubuntu1 is to be installed
E: Broken packages

```

Still this is what I get with the current sources.list:

```

 sudo apt-get install libfam-dev
Reading package lists... Done
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
  libfam-dev: Depends: libfam0 (= 2.7.0-5ubuntu3)
E: Broken packages

 sudo apt-get install libfam0
Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  fam
The following packages will be REMOVED:
  adept amarok amarok-gstreamer cervisia dcoprss digikam eclipse-jdt
  eclipse-jdt-common eclipse-pde eclipse-pde-common eclipse-platform
  eclipse-platform-common eclipse-rcp eclipse-sdk eyesapplet fifteenapplet
  gamin gstreamer0.8-gnomevfs gstreamer0.8-plugins gtk2-engines-gtk-qt
  gwenview juk k3b k3blibs kaboodle kaddressbook kaddressbook-plugins kaffeine
  kaffeine-gstreamer kamera kappfinder karm kasteroids katapult kate
  kate-plugins katomic kaudiocreator kbabel kbackgammon kbattleship kblackbox
  kbounce kbugbuster kcachegrind kcalc kcharselect kcoloredit kcontrol kcron
  kdat kde-guidance kde-style-lipstik kde-systemsettings
  kdeaddons-kfile-plugins kdeadmin kdeadmin-kfile-plugins kdeartwork
  kdeartwork-style kdeartwork-theme-window kdebase kdebase-bin
  kdebase-kio-plugins kdebluetooth kdegraphics kdegraphics-kfile-plugins
  kdelibs kdelibs-bin kdelibs4c2 kdelirc kdemultimedia-kappfinder-data
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins
  kdeprint kdesdk-kfile-plugins kdesdk-misc kdesktop kdessh kdf kdict kdm kdvi
  kedit kenolaba kfax kfaxview kfind kfloppy kfouleggs kgamma kget kghostview
  kgoldrunner kgpg khelpcenter khexedit kicker kicker-applets kiconedit kile
  kio-apt kio-locate kjots kjumpingcube klaptopdaemon klickety klines klipper
  kmahjongg kmail kmenuedit kmid kmilo kmines kmix kmoon kmrml kmtrace
  knetworkconf knewsticker knotes kodo koffice-data koffice-libs kolf
  kolourpaint kompare konqueror konqueror-nsplugins konquest konserve konsole
  kontact konversation kooka kopete korganizer kpackage kpager kpat kpdf
  kpersonalizer kpf kpoker kpovmodeler kppp krdc kregexpeditor kreversi krfb
  krita kruler ksame kscd kscreensaver kscreensaver-xsavers kshisen ksig ksim
  ksirc ksirtet ksmiletris ksmserver ksnake ksnapshot ksokoban kspaceduel
  ksplash ksvg ksysguard ksystemlog ksysv kteatime ktimer ktip ktron
  ktuberling ktux kubuntu-default-settings kubuntu-docs
  kubuntu-konqueror-shortcuts kuickshow kuiviewer kuser kview kviewshell
  kwalletmanager kweather kwifimanager kwin kwin4 kworldclock libarts1-xine
  libbonoboui2-0 libcvsservice0 libdbus-qt-1-1c2 libgamin0 libgnome2-0
  libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common libkcal2b libkcddb1
  libkdegames1 libkdepim1a libkexif1 libkipi0 libkleopatra1 libkmime2 libkonq4
  libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1
  libmimelib1c2 librss1 libswt3.1-gtk-java libswt3.1-gtk-jni
  libwvstreams4.0c2-extras lskat nvu openoffice.org2-kde python-kde3
  python2.4-gamin python2.4-kde3 rosegarden4 sanekonsole secpolicy
  superkaramba umbrello vimpart wvdial
The following NEW packages will be installed:
  libfam0
0 upgraded, 1 newly installed, 238 to remove and 0 not upgraded.
Need to get 25.0kB of archives.
After unpacking 550MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.


```

if I try to uninstall libgamin0, it wants to uninstall half of my system:
```


sudo apt-get remove libgamin0
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  amarok amarok-gstreamer cervisia dcoprss digikam eclipse-jdt
  eclipse-jdt-common eclipse-pde eclipse-pde-common eclipse-platform
  eclipse-platform-common eclipse-rcp eclipse-sdk eyesapplet fifteenapplet
  gamin gstreamer0.8-gnomevfs gstreamer0.8-plugins gtk2-engines-gtk-qt
  gwenview juk k3b k3blibs kaboodle kaddressbook kaddressbook-plugins kaffeine
  kaffeine-gstreamer kamera kappfinder karm kasteroids katapult kate
  kate-plugins katomic kaudiocreator kbabel kbackgammon kbattleship kblackbox
  kbounce kbugbuster kcachegrind kcalc kcharselect kcoloredit kcontrol kcron
  kdat kde-guidance kde-style-lipstik kde-systemsettings
  kdeaddons-kfile-plugins kdeadmin kdeadmin-kfile-plugins kdeartwork
  kdeartwork-style kdeartwork-theme-window kdebase kdebase-bin
  kdebase-kio-plugins kdebluetooth kdegraphics kdegraphics-kfile-plugins
  kdelibs kdelibs-bin kdelibs4c2 kdelirc kdemultimedia-kappfinder-data
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins
  kdeprint kdesdk-kfile-plugins kdesdk-misc kdesktop kdessh kdf kdict kdm kdvi
  kedit kenolaba kfax kfaxview kfind kfloppy kfouleggs kgamma kget kghostview
  kgoldrunner kgpg khelpcenter khexedit kicker kicker-applets kiconedit kile
  kio-apt kio-locate kjots kjumpingcube klaptopdaemon klickety klines klipper
  kmahjongg kmail kmenuedit kmid kmilo kmines kmix kmoon kmrml kmtrace
  knetworkconf knewsticker knotes kodo koffice-data koffice-libs kolf
  kolourpaint kompare konqueror konqueror-nsplugins konquest konserve konsole
  kontact konversation kooka kopete korganizer kpackage kpager kpat kpdf
  kpersonalizer kpf kpoker kpovmodeler kppp krdc kregexpeditor kreversi krfb
  krita kruler ksame kscd kscreensaver kscreensaver-xsavers kshisen ksig ksim
  ksirc ksirtet ksmiletris ksmserver ksnake ksnapshot ksokoban kspaceduel
  ksplash ksvg ksysguard ksystemlog ksysv kteatime ktimer ktip ktron
  ktuberling ktux kubuntu-default-settings kubuntu-docs
  kubuntu-konqueror-shortcuts kuickshow kuiviewer kuser kview kviewshell
  kwalletmanager kweather kwifimanager kwin kwin4 kworldclock libarts1-xine
  libbonoboui2-0 libcvsservice0 libdbus-qt-1-1c2 libgamin0 libgnome2-0
  libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common libkcal2b libkcddb1
  libkdegames1 libkdepim1a libkexif1 libkipi0 libkleopatra1 libkmime2 libkonq4
  libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1
  libmimelib1c2 librss1 libswt3.1-gtk-java libswt3.1-gtk-jni
  libwvstreams4.0c2-extras lskat nvu openoffice.org2-kde python-kde3
  python2.4-gamin python2.4-kde3 rosegarden4 sanekonsole secpolicy
  superkaramba umbrello vimpart wvdial
0 upgraded, 0 newly installed, 237 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 546MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
```


I'm lost... Any way that I could downgrade gamin and libgamin to the breezy versions without uninstalling half of my system?

---

### Post by magnusbb on 2006-01-24
I don't know if this will work for you, but try:

Open Synaptic.

Find the packages (ie. gamin and libgamin) and select one of them. Then press CTRL + E (that is the option in the Package-menu called "Force version..."). In the drop-down-menu find the original Breezy package, and try to force it.

---

### Post by alonso on 2006-01-24
I tried that already... It wants to remove the same things... 

I think I will do that and re-install everything. I think most of my settings should be saved, since they are in the home dir...

So it seems that APT works great until you start messing around with additional repositories...

-A

---

### Post by alonso on 2006-01-24
It worked!

I just did 

```
apt-get remove libgamin0
```

That uninstalled most of KDE. Then I simply did 

```

apt-get install kubuntu-desktop
apt-get install kdelibs4-dev

```

I love apt again :)

-A

---

### Post by mlomker on 2006-01-24
Yeah, installing DEBS from another version was your problem.  If you need a package that isn't available in the Breezy repos then you'll want to compile it from source rather than installing an unknown DEB.  You can bork the system pretty good, otherwise.

---

### Post by sharperguy on 2006-03-21
fs i wish *i* knew that a few weeks ago!
</reinstallingjustabouteverything>

---

