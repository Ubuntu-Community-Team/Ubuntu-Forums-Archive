---
title: "broken packages"
date: 2005-05-21
forum: Desktop Environments
---

### Post by boosted on 2005-05-21
whenever I open Package Manager it says I have 3 broken packages.  So I filter the broken packages then click fix broken packages then Apply.  Well it says it is going to Remove 166 Packages?  WTF it looks like it is removing the whole OS ..I mean I think everything is in there.  What should I do?

---

### Post by SGC on 2005-05-21
What are the names of these three packages?

---

### Post by boosted on 2005-05-21
[QUOTE=SGC]What are the names of these three packages?[/QUOTE]

well I am a little confused because it says 3 broken packages, but when I go through and filter broken packages then click fix broken packages, there are a lot more than 3!  I am assuming that before I click apply and scroll through them the Ones highlighted in RED with an X are the broken ones?

sudo apt-get -f install
Reading Package Lists... Done
Building Dependency Tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  apache2 apache2-common apache2-mpm-prefork bug-buddy capplets capplets-data
  contact-lookup-applet dbus-1 desktop-file-utils eog evolution
  evolution-data-server evolution-exchange evolution-webcal file-roller
  fontconfig gaim gcalctool gconf-editor gconf2 gdm gedit gedit-common
  gftp-common gftp-gtk gimp gimp-python gksu gnome-about gnome-applets
  gnome-applets-data gnome-control-center gnome-cpufreq-applet
  gnome-cups-manager gnome-games gnome-gv gnome-keyring gnome-media
  gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data
  gnome-pilot gnome-pilot-conduits gnome-session gnome-spell
  gnome-system-monitor gnome-system-tools gnome-terminal gnome-themes
  gnome-utils gnomemeeting gossip gstreamer0.8-gnomevfs gstreamer0.8-misc
  gthumb gtk2-engines-crux gtk2-engines-industrial gtk2-engines-lighthouseblue
  gtk2-engines-mist gtk2-engines-pixbuf gtk2-engines-smooth
  gtk2-engines-thinice gtkhtml3.2 gucharmap libapache2-mod-auth-plain
  libapache2-mod-php4 libapr0 libbonoboui2-0 libeel2-2 libexpat1 libexpat1-dev
  libfontconfig1 libgail-common libgail17 libgal2.2-1 libgal2.2-common
  libgconf2-4 libgimp2.0 libgksu1.2-0 libgksuui1.0-0 libglade2-0
  libgnome-desktop-2 libgnome-keyring0 libgnome2-0 libgnome2-common
  libgnomecanvas2-0 libgnomecupsui1.0-1 libgnomeprint2.2-0
  libgnomeprintui2.2-0 libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common
  libgstreamer-gconf0.8-0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libgtkhtml2-0 libgtkhtml3.2-11 libgtksourceview1.0-0 libgtkspell0
  libgucharmap4 libmetacity0 libmusicbrainz2 libmusicbrainz4 libnautilus2-2
  libopenh323-1.13.2 libpanel-applet2-0 libpango1.0-0 libpango1.0-common
  libpt-1.6.3 libpt-plugins-alsa libpt-plugins-v4l libqt3c102 libqt3c102-mt
  libqt3c102-mt-mysql libqt3c102-mt-psql librsvg2-2 librsvg2-common libvte4
  libwmf0.2-7 libwnck4 libxft1 libxft2 lsb metacity mozilla-browser
  mozilla-firefox nautilus nvidia-settings openoffice.org openoffice.org-bin
  openoffice.org-debian-files openoffice.org-help-en
  openoffice.org-hyphenation-en-gb openoffice.org-hyphenation-en-us
  openoffice.org-l10n-en openoffice.org-thesaurus-en-us php4-cgi python-glade2
  python-gnome2 python-gtk2 python-musicbrainz python2.3-glade2
  python2.3-gnome2 python2.3-gtk2 python2.3-musicbrainz rhythmbox screem skype
  sound-juicer ssh-askpass-gnome synaptic trashapplet tsclient ttf-opensymbol
  vino xbase-clients xchat xlibs xsane xscreensaver xscreensaver-gl xterm yelp
  zenity
0 upgraded, 0 newly installed, 166 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 653MB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.

those are the packages!

---

### Post by SGC on 2005-05-21
That weird.

The problem is probably caused by a program(s) that you installed recently. So try to remove any recently installed package(s) and check to see if the problem still excite.
(apt-get remove PACKAGE_NAME).

Try also,  apt-get update, before doing, apt-get –f install, It may help.

---

### Post by boosted on 2005-05-21
[QUOTE=SGC]That weird.

The problem is probably caused by a program(s) that you installed recently. So try to remove any recently installed package(s) and check to see if the problem still excite.
(apt-get remove PACKAGE_NAME).

Try also,  apt-get update, before doing, apt-get –f install, It may help.[/QUOTE]

I tried the apt-get update, then apt-get -f install but still the same outcome!  it seems as if as soon as I clicked on Mark All Upgrades in the Package manager and then clicked Smart Update.... it updated a hell of a lot of stuff I mean I had to let it finish over night.  After that is when it started saying shit about the broken packages.  So I have no clue what package(s) to remove.

---

### Post by crane on 2005-05-21
[QUOTE=boosted]I tried the apt-get update, then apt-get -f install but still the same outcome!  it seems as if as soon as I clicked on Mark All Upgrades in the Package manager and then clicked Smart Update.... it updated a hell of a lot of stuff I mean I had to let it finish over night.  After that is when it started saying shit about the broken packages.  So I have no clue what package(s) to remove.[/QUOTE]

So after letting it update all night and running update again, what packages were listed? 
Is it still trying to remove all the same packages?

---

