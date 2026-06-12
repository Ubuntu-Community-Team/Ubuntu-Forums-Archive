---
title: "libqt3c102-mt is trying to unistall KDE"
date: 2005-12-28
forum: General Help
---

### Post by _axiom_ on 2005-12-28
I am trying to install *qjackctl* to get my synthesizer working (I already have it working on a gnomish ubuntu box).

Whenever I try to install *qjackctl* it claims it needs *libqt3c102-mt*.  However when I try to install *libqt3c102-mt*, it offers to uninstall KDE.  Somehow, this doesn't strike me as a good idea.  I am running KDE 3.5.  Any advice?

Here is the konsole output:
```

axiom@axiom:~$ sudo apt-get install qjackctl
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
  qjackctl: Depends: libqt3c102-mt (>= 3:3.2.3-3) but it is not going to be installed
E: Broken packages
axiom@axiom:~$ sudo apt-get install libqt3c102-mt
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  libqt3c102-mt-psql libqt3c102-mt-mysql libqt3c102-mt-odbc
The following packages will be REMOVED:
  adept akregator amarok amarok-gstreamer amor ark arts artsbuilder atlantik
  atlantikdesigner basket brahms cervisia dcoprss digikam digikamimageplugins
  eric3 eyesapplet fifteenapplet filelight gtk2-engines-gtk-qt gwenview
  hydrogen juk k3b k3b-mp3 k3blibs kaboodle kaddressbook kaddressbook-plugins
  kaffeine kaffeine-gstreamer kaffeine-mozilla kaffeine-xine kalarm kalzium
  kamera kandy kappfinder karbon karm kasablanca kasteroids katapult kate
  kate-plugins katomic kaudiocreator kbabel kbackgammon kbattleship kbear
  kblackbox kbounce kbruch kbstate kbugbuster kcachegrind kcalc kcharselect
  kchart kcoloredit kcontrol kcron kdat kde kde-amusements kde-core
  kde-guidance kde-style-lipstik kde-systemsettings kdeaccessibility kdeaddons
  kdeaddons-kfile-plugins kdeadmin kdeadmin-kfile-plugins kdeartwork
  kdeartwork-style kdeartwork-theme-window kdebase kdebase-bin
  kdebase-kio-plugins kdebluetooth kdeedu kdegames kdegraphics
  kdegraphics-kfile-plugins kdelibs kdelibs-bin kdelibs4-dev kdelibs4c2
  kdelirc kdemultimedia kdemultimedia-kappfinder-data
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim
  kdepim-kfile-plugins kdepim-kio-plugins kdepim-kresources kdepim-wizards
  kdeprint kdesdk kdesdk-kfile-plugins kdesdk-misc kdesktop kdessh kdetoys
  kdeutils kdevelop3 kdevelop3-data kdevelop3-plugins kdewebdev kdf kdict kdm
  kdvi kedit keduca kenolaba kfax kfilereplace kfind kfloppy kformula
  kfouleggs kgamma kget kghostview kgoldrunner kgpg khangman khelpcenter
  khexedit kicker kicker-applets kiconedit kig kimagemapeditor kio-apt
  kio-locate kitchensync kiten kivio kjots kjumpingcube klaptopdaemon klatin
  kleopatra klettres klickety klines klinkstatus klipper kmag kmahjongg kmail
  kmailcvt kmenuedit kmessedwords kmid kmilo kmines kmix kmoon kmousetool
  kmouth kmplot kmrml kmtrace knetworkconf knewsticker knode knotes kodo
  koffice koffice-data koffice-libs kolf kolourpaint kommander kompare kompose
  konq-plugins konqueror konqueror-nsplugins konquest konserve konsole
  konsolekalendar kontact konversation kooka kopete korganizer korn koshell
  kpackage kpager kpat kpdf kpercentage kpersonalizer kpf kpilot kpoker
  kpovmodeler kppp kpresenter krdc krec kregexpeditor kreversi krfb krita
  kruler ksame ksayit kscd kscreensaver kscreensaver-xsavers kshisen ksig ksim
  ksirc ksirtet ksmiletris ksmserver ksnake ksnapshot ksokoban kspaceduel
  ksplash kspread kspy kstars ksvg ksync ksysguard ksystemlog ksysv kteatime
  kthesaurus ktimer ktip ktnef ktorrent ktouch ktron kttsd ktuberling kturtle
  ktux kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts kugar
  kuickshow kuiviewer kuser kverbos kview kviewshell kvoctrain kwalletmanager
  kweather kwifimanager kwin kwin4 kword kwordquiz kworldclock kxsldbg
  kynaptic labplot libarts1-akode libarts1-audiofile libarts1-dev
  libarts1-mpeglib libarts1-xine libarts1c2 libcvsservice0 libdbus-qt-1-1c2
  libkcal2b libkcddb1 libkdeedu1 libkdegames1 libkdepim1a libkexif1 libkgantt0
  libkipi0 libkiten1 libkleopatra1 libkmime2 libkonq4 libkpimexchange1
  libkpimidentities1 libkscan1 libksieve0 libktnef1 libmimelib1c2
  libqscintilla5c2 libqt3-mt libqt3-mt-dev librss1 licq licq-plugin-qt lskat
  muse networkstatus noatun noatun-plugins openoffice.org-kde
  openoffice.org2-kde pinentry-qt poxml python-kde3 python-qtext
  python2.4-kde3 python2.4-qt3 python2.4-qtext python2.4-sip4-qt3 qca-tls
  qobex qsynth qt3-dev-tools quanta rosegarden4 sanekonsole secpolicy sim
  speedcrunch superkaramba umbrello valknut vimpart
The following NEW packages will be installed:
  libqt3c102-mt
0 upgraded, 1 newly installed, 340 to remove and 4 not upgraded.
Need to get 2960kB of archives.
After unpacking 765MB disk space will be freed.
Do you want to continue [Y/n]?  

```

---

### Post by mazelado on 2006-01-01
Are you installing qjackctl from the Universe repository? I tried installing it on my machine (also KDE 3.5) and it does not require the libqt3c102-mt package. In fact, I don't even have a libqt3c102-mt package available. As far as I know, it's been superceded by another package (libqt3-mt, I think).  Try to find out which repository qjackctl and libqt3c102-mt are coming from and consider removing or disabling them since they appear to have outdated packages. Make sure the Universe repository is enabled, then try installing qjackctl again.

---

