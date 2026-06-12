---
title: "Dependencies problem"
date: 2005-12-31
forum: General Help
---

### Post by janfsd on 2005-12-31
Hi! ive got a big problem, i was trying to manually install some deb programs 'cause i needed newer versions of g++ ...so now i got 5 broken packages :
 gij-4.0 lib32stdc++6 libgcj6 libstdc++6 libstdc++6-4.0-dev

and whenever i want to install or reinstall one of those, it appears that i have to remove a hell lot of packages:  i think all the basic ones:

```
 akode akode-mpeg alien amule apt apt-utils aptitude artsbuilder aspell
  aspell-en aspell-pl atlantik base-config beep-media-player
  beep-media-player-dev bluez-cups bmp-mp4 build-essential cdrdao clamav
  clamav-freshclam clamtk cupsys cupsys-driver-gimpprint
  cupsys-driver-gimpprint-data d4x debhelper dselect dvd+rw-tools easytag
  evince firefox firefox-gnome-support foomatic-db-gimp-print
  foomatic-db-hpijs freeglut3 freeglut3-dev frozen-bubble g++ g++-4.0 gaim gdm
  gdm-themes gedit gettext gij gij-4.0 gksu glutg3-dev gnome-app-install
  gnome-cups-manager gnome-games gnome-media gnome-netstatus-applet
  gnome-spell gnome-system-monitor gnome-volume-manager gnomebaker
  gnomemeeting gparted graveman groff-base gs-common gs-esp gstreamer0.8-dirac
  gstreamer0.8-faac gstreamer0.8-faad gstreamer0.8-lame gstreamer0.8-misc
  gstreamer0.8-plugins-multiverse gstreamer0.8-sid gstreamer0.8-vorbis
  gstreamer0.8-wavpack gstreamer0.8-xvid gtoaster gxine hpijs hplip-base
  hplip-data html2text hwdb-client ijsgimpprint intltool-debian
  j2re1.4-mozilla-plugin java-gcj-compat java-package k3b k3blibs kasteroids
  katomic kbackgammon kbattleship kblackbox kbounce kcontrol kdeartwork
  kdeartwork-style kdeartwork-theme-window kdebase-bin kdegames kdelibs-bin
  kdelibs4c2 kdesktop kenolaba kfouleggs kgoldrunner kicker kjumpingcube
  klickety klines kmahjongg kmines kolf konquest kpat kpoker kreversi ksame
  kscreensaver kscreensaver-xsavers kshisen ksirtet ksmiletris ksnake ksokoban
  kspaceduel ktron ktuberling kwin kwin4 language-selector language-support-en
  lib32gcj6 lib32stdc++6 libarts1-dev libarts1c2 libaspell-dev libaspell15
  libavifile-0.7 libavifile-0.7-dev libclamav1 libdbus-qt-1-1c2 libdc0c2
  libdirac0 libdjvulibre15 libfaac-dev libfaac0 libflac++-dev libflac++5c2
  libflash-swfplayer libflash0c2 libgc1c2 libgcj6 libgcj6-common libgksu1.2-0
  libgksuui1.0-0 libgl1-mesa libgl1-mesa-dev libgl1-mesa-dri libgle3
  libglibmm-2.4-1c2 libglibmm-2.4-dev libglu1-mesa libglu1-mesa-dev libglut3
  libglut3-dev libgmp3c2 libgmpxx3 libgnomecupsui1.0-1 libgtkmm-2.4-1c2
  libgtkspell-dev libgtkspell0 libhsqldb-java libid3-3.8.3c2 libkdegames1
  libkonq4 libmjpegtools0 libmodplug0c2 libmp4v2-0 libmusicbrainz2c2
  libmusicbrainz4c2 liboggflac++-dev liboggflac++2c2 libopenal0 libopenexr2c2
  libopenh323-1.15.3c2 libpoppler0c2 libpoppler0c2-glib libpspell-dev
  libpt-1.8.3c2 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2
  libqt3-mt libqt3-mt-dev libsdl-mixer1.2 libsdl-perl libsdl-ttf2.0-dev
  libsdl1.2-dev libservlet2.3-java libsidplay1 libsigc++-2.0-0c2
  libsigc++-2.0-dev libsmpeg0c2 libstdc++6 libstdc++6-4.0-dev libtag1-dev
  libtag1c2 libtagc0 libtagc0-dev libvisual0.2-plugins libwvstreams4.0c2-base
  libwvstreams4.0c2-extras libwxgtk2.6-0 libwxgtk2.6-dev libxine1c2
  libxplc0.3.11c2 lshw lskat man-db menu mesa-utils mjpegtools motif-clients
  motv mozilla-firefox-locale-en-gb mozilla-mplayer mpeglib mplayer-amd64
  mplayer-fonts notification-daemon nvidia-glx nvu openoffice.org2
  openoffice.org2-base openoffice.org2-calc openoffice.org2-common
  openoffice.org2-core openoffice.org2-draw openoffice.org2-gnome
  openoffice.org2-impress openoffice.org2-l10n-en-us openoffice.org2-math
  openoffice.org2-writer pia pnm2ppa po-debconf python-apt
  python-gnome2-extras python-id3lib python-musicbrainz python-wxgtk2.6
  python2.4-apt python2.4-gnome2-extras python2.4-id3lib python2.4-musicbrainz
  qt3-dev-tools rhythmbox rss-glx serpentine sound-juicer swf-player synaptic
  tagtool telnet totem totem-xine ubuntu-desktop ubuntu-minimal
  ubuntu-standard unrar-nonfree update-manager update-notifier valknut vlc
  vlc-plugin-alsa vlc-plugin-esd w3m wvdial wx-common wxvlc
  x-window-system-core xawtv xbase-clients xdriinfo xine-ui xmms-xmmplayer
  xprint xprint-common xscreensaver-gl xvncviewer yelp

```

so do i have another option in fixing these files  without removing all the others?i dont want to have to reinstall everything and reconfigure everything.... i would appretiate any kind of help....
by the way have a happy new year!!!:D

---

### Post by janfsd on 2005-12-31
well, it seems that i have fixed the broken packages without having to remove the other packages...

but when i installed the libstdc++6-4.0_dev it got a problem that g++-4... was not configurated properly, and whenever i try to install this g++ it says that it depends on this libstdc and cannot configurate itself... but it installs it anyway, so does this matter?

---

