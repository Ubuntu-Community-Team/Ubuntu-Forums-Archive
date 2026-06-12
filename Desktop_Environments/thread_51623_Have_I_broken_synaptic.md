---
title: "Have I broken synaptic?"
date: 2005-07-24
forum: Desktop Environments
---

### Post by tseliot on 2005-07-24
I was having problems with alsa and I did:

sudo apt-get remove libesd-alsa0 

but this implied removing lots of things:


The following packages will be REMOVED:
  akode akregator amarok amarok-arts amor ark artsbuilder atlantik
  atlantikdesigner ayttm bug-buddy capplets cervisia dbus-qt-1 eog evolution
  evolution-data-server evolution-exchange evolution-webcal eyesapplet
  fifteenapplet file-roller gcalctool gconf-editor gdm gedit gedit-common
  gnome-about gnome-applets gnome-applets-data gnome-btdownload
  gnome-control-center gnome-cups-manager gnome-games gnome-gv gnome-media
  gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data
  gnome-pilot gnome-pilot-conduits gnome-session gnome-spell
  gnome-system-monitor gnome-system-tools gnome-terminal gnome-utils
  gnome-volume-manager gnomemeeting gstreamer0.8-esd gthumb gtkhtml3.6
  gucharmap gwenview hal-device-manager hwdb-client juk k3b k3blibs
  kaddressbook kaddressbook-plugins kalarm kalzium kamera kappfinder karm
  kasteroids kate kate-plugins katomic kaudiocreator kbabel kbackgammon
  kbattleship kblackbox kbounce kbruch kbstate kbugbuster kcachegrind kcalc
  kcharselect kcontrol kcron kde-style-lipstik kdeaddons-kfile-plugins
  kdeadmin kdeadmin-kfile-plugins kdeartwork kdeartwork-style
  kdeartwork-theme-window kdebase-bin kdebase-kio-plugins kdeedu kdegraphics
  kdegraphics-kfile-plugins kdelibs kdelibs-bin kdelibs4
  kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins
  kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins
  kdepasswd kdepim-kfile-plugins kdepim-kio-plugins kdepim-wizards kdeprint
  kdesdk-kfile-plugins kdesdk-misc kdesktop kdevelop3 kdevelop3-data
  kdevelop3-plugins kdewebdev kdm keduca kenolaba kfilereplace kfind kfloppy
  kfouleggs kgamma kghostview kgoldrunner kgpg khangman khelpcenter kicker
  kicker-applets kig kimagemapeditor kitchensync kiten kjumpingcube
  klaptopdaemon klatin klettres klickety klines klinkstatus klipper kmag
  kmahjongg kmail kmailcvt kmenuedit kmessedwords kmilo kmines kmix kmoon
  kmousetool kmouth kmplot kmrml kmtrace knewsticker knode knotes kodo kolf
  kolourpaint kommander kompare konq-plugins konqueror konqueror-nsplugins
  konquest konsole konsolekalendar kontact kooka kopete korganizer kpager kpat
  kpdf kpercentage kpersonalizer kpf kpilot kpoker kppp krdc kregexpeditor
  kreversi krfb ksame ksayit kscd kscreensaver kscreensaver-xsavers kshisen
  ksig ksim ksirtet ksmiletris ksmserver ksnake ksnapshot ksokoban kspaceduel
  ksplash kstars ksvg ksync ksysguard kteatime ktnef ktouch ktron kttsd
  ktuberling kturtle ktux kubuntu-default-settings kuiviewer kuser kverbos
  kvim kvoctrain kwalletmanager kweather kwifimanager kwin kwin-baghira kwin4
  kwordquiz kworldclock kxsldbg libarts1 libarts1-audiofile libarts1-mpeglib
  libarts1-xine libbonoboui2-0 libcamel1.2-3 libcvsservice0 libebook1.2-3
  libecal1.2-2 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-4
  libedataserverui1.2-4 libeel2-2 libegroupwise1.2-5 libesd-alsa0 libgal2.4-0
  libgal2.4-common libgnome-desktop-2 libgnome2-0 libgnome2-perl
  libgnomecupsui1.0-1 libgnomeui-0 libgtkhtml3.6-18 libgucharmap4 libkcal2a
  libkcddb1 libkdeedu1 libkdegames1 libkdepim1 libkgantt0 libkipi0
  libkleopatra0a libkonq4 libkpimexchange1 libkpimidentities1 libkscan1
  libksieve0 libktnef1 libmimelib1a libopenal0 libpanel-applet2-0 librss1
  libwxgtk2.5.3 lskat mozilla-firefox mozilla-firefox-gnome-support
  mozilla-mplayer mozilla-plugin-vlc mpeglib mplayer-amd64 mplayer-fonts
  nautilus nautilus-cd-burner nautilus-sendto networkstatus noatun
  python-gnome2 python2.4-gnome2 quanta rhythmbox rss-glx secpolicy smb4k
  sound-juicer superkaramba totem totem-gstreamer tsclient umbrello
  update-manager update-notifier vimpart vino vlc vlc-alsa vlc-plugin-alsa
  wxvlc xmms-kde yelp
0 upgraded, 0 newly installed, 313 to remove and 5 not upgraded.
Need to get 0B of archives.
After unpacking 791MB disk space will be freed.

Do you want to continue [Y/n]?

I erroneously said yes to Apt request. And shut down the Konsole.

Now I can't install anything in synaptic (it just downloads the file and then the installation ends).

If I try to install anything from "apt-get", here's what I get:

alberto@ubuntu:~$ sudo apt-get install scummvm
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  timidity beneath-a-steel-sky flight-of-the-amazon-queen
The following NEW packages will be installed:
  scummvm
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B/1037kB of archives.
After unpacking 3117kB of additional disk space will be used.

[COLOR=Red]Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 6 package `kdenetwork':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)
[/COLOR]


Please, help me, I don't want to reinstall Ubuntu AGAIN!

---

### Post by Xian on 2005-07-24
Read this [THREAD](http://www.ubuntuforums.org/showthread.php?p=238397#post238397) for more information.

---

### Post by tseliot on 2005-07-24
This doesn't seem to work

Can this be the error (in the first lines of "status" and "status-old")?

Package: kdenetwork
Status: purge ok installed
Priority: optional
Section: kde

---

### Post by tseliot on 2005-07-24
What else can I do?

---

### Post by charlieg on 2005-07-24
Bloodey hell, it looks like you removed almost everything!

It might be time to reconsider a re-install of Ubuntu.  You can install over your old partition and hence keep your home directory (i.e. your data) so not all is lost.

Failing that, try using dpkg to install all those files again.

---

### Post by tseliot on 2005-07-24
I installed Ubuntu 3 days ago... ](*,)

---

