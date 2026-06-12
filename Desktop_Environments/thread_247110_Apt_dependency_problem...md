---
title: "Apt dependency problem.."
date: 2006-08-30
forum: Desktop Environments
---

### Post by Adrian_b on 2006-08-30
```
sagara@sousuke:~$ agi quodlibet
Reading package lists... Done
Building dependency tree... Done
quodlibet is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  python2.4-kde3: Depends: python2.4-sip4-qt3 (>= 4.3) but it is not going to be installed
                  Depends: python2.4-sip4-qt3 (< 4.4) but it is not going to be installed
  python2.4-qt3: Depends: python2.4-sip4-qt3 (>= 4.3) but it is not going to be installed
                 Depends: python2.4-sip4-qt3 (< 4.4) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
sagara@sousuke:~$ agi -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python2.4-sip4-qt3
The following NEW packages will be installed:
  python2.4-sip4-qt3
0 upgraded, 1 newly installed, 0 to remove and 103 not upgraded.
73 not fully installed or removed.
Need to get 0B/69.8kB of archives.
After unpacking 221kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 179727 files and directories currently installed.)
Unpacking python2.4-sip4-qt3 (from .../python2.4-sip4-qt3_4.3.2-0ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/python2.4-sip4-qt3_4.3.2-0ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/python2.4/site-packages/sipconfig.py', which is also in package python2.4-sip-qt3
Errors were encountered while processing:
 /var/cache/apt/archives/python2.4-sip4-qt3_4.3.2-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
sagara@sousuke:~$

```
(note: agi is my alias for apt-get install + quodlibet is already installed, it's an example)

I have no idea whatsoever how to fix this, please enlighten me :(

---

### Post by mgmiller on 2006-08-30
apt-get needs to be run as sudo, is your alias dong that?

---

### Post by Anonii on 2006-08-30
> **mgmiller said:**
> apt-get needs to be run as sudo, is your alias dong that?
Ye, he would get a different error message if he didnt.

---

### Post by Adrian_b on 2006-08-30
No other help?
I'm out of ideas and reinstalling would be a real pain in the ***..

---

### Post by Anonii on 2006-08-30
> **Adrian_b said:**
> No other help?
I'm out of ideas and reinstalling would be a real pain in the ***..
Try with aptitude. And report back :/

---

### Post by Adrian_b on 2006-08-30
```

sagara@sousuke:~$ sudo aptitude -f install
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  python2.4-sip4-qt3
The following packages have been kept back:
  app-install-data-commercial base-files cgwd compiz compiz-gnome cupsys cupsys-bsd cupsys-client dia-common dia-gnome dia-libs eog file-roller firefox firefox-gnome-support
  gaim gdm gedit gedit-common gnome-about gnome-accessibility-themes gnome-applets gnome-applets-data gnome-desktop-data gnome-games gnome-games-data gnome-menus gnome-panel
  gnome-panel-data gnome-screensaver gnome-session gnome-themes gnupg gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps
  gstreamer0.10-x gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf
  gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice gtkhtml3.8 imagemagick language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base libcupsimage2 libcupsys2 libcupsys2-dev libdrm2 libeel2-2 libeel2-data libgl1-mesa libgl1-mesa-dev libgl1-mesa-dri libglu1-mesa libglu1-mesa-dev
  libgnome-menu2 libgstreamer-plugins-base0.10-0 libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libkadm55 libkrb5-dev libkrb53 libmagick9 libnautilus-burn3
  libnautilus-extension1 libnspr4 libnss3 libpanel-applet2-0 libtag1c2a libtheora0 libtiff-tools libtotem-plparser1 libtunepimp-bin libwmf0.2-7 linux-image-2.6.15-26-686
  linux-image-386 linux-restricted-modules-386 mesa-common-dev mesa-utils nautilus nautilus-cd-burner nautilus-data python-gmenu python2.4-tunepimp totem ubuntu-base
  ubuntu-minimal ubuntu-standard usp vmware-player-kernel-modules xnest xserver-xorg-core yelp zenity
The following NEW packages will be installed:
  dillo gaim-data libgnome-desktop-dev libwnck-dev python-gtk2-dev python2.4-sip4-qt3 rhythmbox rhythmbox-applet totem-gstreamer
The following packages will be REMOVED:
  abiword-plugins abiword-plugins-gnome amarok amarok-xine apollon bos debfoster epiphany-browser epiphany-extensions f-spot freedoom gcc-3.4-base gcursor gift giftcurs giftd
  gjots2 gnome-icon-theme-gperfection2 gnome-icon-theme-suede gnuboy-x gtweakui gv kaffeine kaffeine-xine kde kde-amusements kde-core kdeaddons kdebase konq-plugins konqueror
  lapack3 lgc-pg lgeneral libaa1-dev libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a liballegro4.2 libarchive-zip-perl libares-gift libcompress-zlib-perl
  libcrypt-ssleay-perl libcurl3-dev libcurl3-openssl-dev libdate-manip-perl libdb4.2 libdbus-1-cil libfasttrack-gift libfcgi-perl libg2c0 libgdome2-0 libgdome2-cpp-smart0c2a
  libgift0 libgiftproto0 libglademm-2.4-1c2a libglitz1-dev libgnutella-gift libgtkmathview0c2a libguichan0 libhttp-cache-transparent-perl libio-socket-ssl-perl libmime-lite-perl
  libncurses5-dev libnet-ssleay-perl libopenft-gift libossp-uuid-perl libossp-uuid13 libots0 libsdl-image1.2 libsdl-mixer1.2 libsdl-ttf2.0-0 libsdl1.2-dev libslang2-dev
  libsmpeg0 libsoap-lite-perl libt1-5 libterm-readkey-perl libtk-tablematrix-perl libwpd-stream8c2a libwww-mechanize-perl libxine1c2 libxml-libxml-common-perl libxml-libxml-perl
  libxml-namespacesupport-perl libxml-sax-perl libxml-twig-perl libxml-writer-perl libxmltv-perl libzvt2.0-0 libzvt2.0-dev liquidwar liquidwar-data liquidwar-server mc mpage
  mpg123 p7zip perl-tk python-pygame python2.4-numeric-ext python2.4-pygame refblas3 stratagus tilda tmw totem-xine vlc-plugin-esd xarchive xaw3dg xmltv xmltv-gui xmltv-util
0 packages upgraded, 9 newly installed, 113 to remove and 105 not upgraded.
Need to get 3551kB/4318kB of archives. After unpacking 181MB will be freed.
Do you want to continue? [Y/n/?]

```

Doesn't make any sense at all :s

EDIT: I got it fixed!
I removed language-selector-qt, python2.4-kde3 and python2.4-qt3 which did the trick.

---

### Post by wsetyonugroho on 2006-09-01
i got this message when trying to do
sudo apt-get install amarok

could anyone help me, please ?
thx
===================================================
[I]Reading package lists... Done
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
  amarok: Depends: amarok-xine but it is not going to be installed
          Depends: ruby but it is not installable
          Depends: python-qt3 but it is not installable
          Depends: kdelibs4c2a (>= 4:3.5.2) but it is not going to be installed
          Depends: libifp4 but it is not installable
E: Broken packages[/I]

---

