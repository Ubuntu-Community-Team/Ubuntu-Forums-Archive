---
title: "Switching to kde-base"
date: 2009-10-12
forum: Desktop Environments
---

### Post by Falc7 on 2009-10-12
I am currently using kubuntu-desktop (and ubuntu), and i would like to switch to kde-base, how do i do that?

My second question is if i have a live cd, how would i install just kde-base?

---

### Post by rb0171610 on 2009-10-12
> **Falc7 said:**
> I am currently using kubuntu-desktop (and ubuntu), and i would like to switch to kde-base, how do i do that?

kubuntu-desktop is just a package that offers a set of programs available in KDE.  You could install it or uninstall it as you see fit.  kde-base is the base set of programs that provides you with the KDE desktop. You are using the KDE desktop environment on the Ubuntu Linux distribution.

I am not quite sure what you are trying to say.  Could you be a little more specific?  If you still need help let me know.

---

### Post by Falc7 on 2009-10-12
Well, i'm using kubuntu-desktop now, but i've heard that kde-base is a little more minimalist, a little bit quicker, and i enjoy the idea of adding the packages i need rather than removing the ones i don't. I currently have a full kubuntu-desktop, so i wanted to basically get rid of it, and start again with kde-base and build it from the ground up. 
I hope thats clear :)

---

### Post by rb0171610 on 2009-10-12
> **Falc7 said:**
> Well, i'm using kubuntu-desktop now, but i've heard that kde-base is a little more minimalist, a little bit quicker, and i enjoy the idea of adding the packages i need rather than removing the ones i don't. I currently have a full kubuntu-desktop, so i wanted to basically get rid of it, and start again with kde-base and build it from the ground up. 
I hope thats clear :)

No, unfortunately despite your best efforts it is not clear. What distribution are you using i.e. Ubuntu 9.04, Kubuntu 9.04, etc?
You will find that Ubuntu's default KDE installation is not bloated and has only installed what you need.

I would just leave it the way it is.  You are not going to find it overloaded with unnecessary packages. If you are just experimenting, you can try completely uninstalling KDE and reinstalling it.  I am not sure what you expect to happen though by doing this.

Are you on a slow machine?  Are you running out of hard drive space?
Do you want to see what KDE would look like without any Ubuntu tweaks?

---

### Post by Falc7 on 2009-10-12
Well, first i installed ubuntu 9.10, then installed kubuntu-desktop to try it out, i liked it. I was reading this:
[http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)
And i liked this paragraph > Why kde-core?
You may not have a reason to run kde-core. You might be perfectly satisfied with kubuntu-desktop. If so, go on your merry way—you don't really need this page. Some people are attracted to kde-core because they want more control over what gets installed (they'd rather build from the ground up than remove unwanted packages one at a time). Others want to try kde-core because it might run more lightly (i.e., faster) on their systems than the standard Kubuntu. 

So i want to know how i can remove kubuntu-desktop, and try kde-core

---

### Post by rb0171610 on 2009-10-12
> **Falc7 said:**
> Well, first i installed ubuntu 9.10, then installed kubuntu-desktop to try it out, i liked it. I was reading this:
[http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)
And i liked this paragraph 

So i want to know how i can remove kubuntu-desktop, and try kde-core

Ok, now that I have some insight into your logic. You can uninstall or install programs from the command line.
Open a terminal and type:

[I]sudo apt-get update 
sudo apt-cache search kubuntu [/I]

You should see output similar to this:
[I]
edubuntu-desktop-kde - educational desktop for Kubuntu
kubuntu-artwork-usplash - Kubuntu artwork for usplash
kubuntu-default-settings - Default settings and artwork for the Kubuntu desktop
kubuntu-desktop - Kubuntu desktop system
kubuntu-docs - kubuntu system documentation
kubuntu-konqueror-shortcuts - Konqueror shortcuts for the Kubuntu wiki, Ubuntu Docs, Launchpad and more
kmformat - floppy and USB disk formatting tool for KDE
kubuntu-grub-splashimages - grub splashimages for Kubuntu
uck - Tool to customize official Ubuntu Live CDs
winff - graphical video and audio batch converter using ffmpeg
kubuntu-restricted-extras - Commonly used restricted packages
language-selector-qt - Language selector for Kubuntu Linux[/I]

This is a list of packages with kubuntu in the name. To uninstall kubuntu-desktop, you can type:

*sudo apt-get remove kubuntu-desktop*


You should get output similar to this:
[I]
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  kubuntu-desktop
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded[/I].

---

### Post by rb0171610 on 2009-10-12
> **Falc7 said:**
> Well, first i installed ubuntu 9.10, then installed kubuntu-desktop to try it out, i liked it. I was reading this:
[http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)
And i liked this paragraph 

So i want to know how i can remove kubuntu-desktop, and try kde-core

I just wanted to point out that when you install kdebase or kdecore you will find you are adding packages ;).

[I]sudo apt-get install **kdebase**
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  kappfinder kwrite
The following NEW packages will be installed:
  kappfinder kdebase kwrite
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 582kB of archives.
After this operation, 2511kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.



rob@tux:~$ sudo apt-get install **kde-core**
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  kdebase-workspace
Suggested packages:
  kde-l10n
The following NEW packages will be installed:
  kde-core kdebase-workspace
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 51.2kB of archives.
After this operation, 365kB of additional disk space will be used.
Do you want to continue [Y/n]?
[/I]

I don't think you are going to find any benefit in doing this but carry on. Good Luck.

---

### Post by rb0171610 on 2009-10-12
> **Falc7 said:**
> Well, i'm using kubuntu-desktop now, but i've heard that kde-base is a little more minimalist, a little bit quicker, and i enjoy the idea of adding the packages i need rather than removing the ones i don't. I currently have a full kubuntu-desktop, so i wanted to basically get rid of it, and start again with kde-base and build it from the ground up. 
I hope thats clear :)

You could always try to uninstall everything to do with KDE: 
*sudo apt-get remove kde*

and only install what you like.
That approach might work best for you.

---

### Post by Falc7 on 2009-10-12
Thanks for your help, i'll play around a bit

---

### Post by SuperSonic4 on 2009-10-12
Easiest of all would be to reinstall from the minimal cd and install kde-core but this will cause data loss unless you had a separate /home and didn't format it. It's not beginner stuff though CLI partitioning.

---------------------------------------------------

Remove the kubuntu components and the ubuntu components:

```
sudo apt-get remove akregator amarok amarok-common apport-qt ark cdrdao dolphin dontzap dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ijsgutenprint install-package jockey-kde k3b k3b-data kaddressbook kamera kate kde-icons-oxygen kde-printer-applet kde-style-qtcurve kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons kdeplasma-addons-data kdesudo kdm kfind khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete korganizer kpackagekit krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libao2 libaudio2 libavahi-qt3-1 libboost-program-options1.35.0 libclucene0ldbl libdbus-qt-1-1c2 libeet1 libexiv2-5 libflac++6 libgeoip1 libk3b3 libk3b3-extracodecs libkcddb4 libkdecorations4 libkdepim4 libkexiv2-7 libkholidays4 libkipi6 libkleo4 libkonq5 libkonq5-templates libkpgp4 libksieve4 libkwineffects1 libloudmouth1-0 liblua50 liblualib50 libmad0 libmimelib4 libmodplug0c2 libmpcdec3 libmsn0.1 libmysqlclient15off libokularcore1 libpackagekit-glib11 libpackagekit-qt11 libphonon4 libplasma3 libpoppler-qt4-3 libpq5 libqca2 libqca2-plugin-ossl libqedje0 libqimageblitz4 libqt3-mt libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqzion0 libraptor1 librasqal1 librdf0 libsearchclient0 libsoprano4 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libstrigiqtdbusclient0 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-common okular okular-extra-backends openoffice.org-kde openoffice.org-style-crystal oxygen-cursor-theme packagekit packagekit-backend-apt phonon phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-widget-network-manager plasma-widget-quickaccess python-dev python-kde4 python-packagekit python-plasma python-qt4 python-qt4-common python-qt4-dbus python-sip4 python2.6-dev qt4-qtconfig quassel quassel-data raptor-utils redland-utils software-properties-kde soprano-daemon speedcrunch strigi-client strigi-daemon system-config-printer-kde systemsettings ttf-dejavu ttf-dejavu-extra update-manager-kde update-notifier-kde && sudo apt-get remove alacarte app-install-data-partner apport-gtk apturl at-spi binfmt-support bluez-gnome brasero brltty-x11 capplets-data checkbox checkbox-gtk cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf computer-janitor computer-janitor-gtk contact-lookup-applet dcraw desktop-file-utils dmz-cursor-theme doc-base docbook-xml ekiga eog esound-clients esound-common espeak espeak-data evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-indicator evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet file-roller firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support firefox-gnome-support gamin gcalctool gconf-editor gconf2 gconf2-common gdebi gdm gdm-guest-session gedit gedit-common ggzcore-bin gimp gimp-data gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-cards-data gnome-codec-install gnome-control-center gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-mag gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-mount gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-session-canberra gnome-settings-daemon gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu gnome-user-guide gnome-utils gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse human-icon-theme human-theme indicator-applet indicator-messages jockey-gtk language-selector libart2.24-cil libasound2-plugins libatspi1.0-0 libaudiofile0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbabl-0.0-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrasero-media0 libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gtk-module libcanberra-gtk0 libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio7 libcompizconfig0 libcroco3 libcryptui0 libdecoration0 libdmx1 libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13 libesd-alsa0 libespeak1 libevdocument1 libevview1 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libfreezethaw-perl libgadu3 libgail-common libgail-gnome-module libgail18 libgamin0 libgconf2-4 libgconf2.24-cil libgcr0 libgdata-google1.2-1 libgdata1.2-1 libgdict-1.0-6 libgdiplus libgegl-0.0-0 libggz2 libggzcore9 libggzmod4 libgimp2.0 libgksu2-0 libglade2-0 libglade2.0-cil libglew1.5 libglib-perl libglib2.0-cil libglibmm-2.4-1c2a libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime2.2a-cil libgnome-desktop-2-11 libgnome-keyring0 libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-speech7 libgnome-vfs2.24-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomekbd-common libgnomekbd3 libgnomekbdui3 libgnomepanel2.24-cil libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgp11-0 libgpod-common libgpod4 libgsf-1-114 libgsf-1-common libgsm1 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml2-0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview-common libgtksourceview1.0-0 libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgvfscommon0 libgweather-common libgweather1 libhesiod0 libidl0 libiec61883-0 libindicate1 libjpeg-progs libkpathsea4 liblaunchpad-integration1 liblircclient0 liblpint-bonobo0 libmbca0 libmetacity0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-data2.0-cil libmono-getoptions2.0-cil libmono-i18n2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil libnautilus-burn4 libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnotify1 liboil0.3 liboobs-1-4 libopal3.6.1 liborbit2 libpam-gnome-keyring libpanel-applet2-0 libpangomm-1.4-1 libpisock9 libpisync1 libpolkit-gnome0 libpoppler-glib4 libportaudio2 libprotobuf3 libproxy0 libpt2.6.1 libpt2.6.1-plugins-alsa libpt2.6.1-plugins-v4l2 libpulse-browse0 libpulsecore9 libpurple-bin libpurple0 librarian0 librsvg2-2 librsvg2-common libschroedinger-1.0-0 libscim8c2a libsexy2 libsgutils1 libshout3 libsilc-1.1-2 libsndfile1 libsoup-gnome2.4-1 libsoup2.4-1 libspeexdsp1 libsqlite0 libstartup-notification0 libtdb1 libtie-ixhash-perl libtotem-plparser12 libtrackerclient0 libunique-1.0-0 libuuid-perl libv4l-0 libvisual-0.4-0 libvisual-0.4-plugins libvte-common libvte9 libwmf0.2-7-gtk libwnck-common libwnck22 libxml-twig-perl libxml-xpath-perl libxres1 libzephyr3 metacity metacity-common mobile-broadband-provider-info mono-2.0-gac mono-2.0-runtime mono-common mono-gac mono-jit mono-runtime mousetweaks mtools nautilus nautilus-data nautilus-sendto nautilus-share network-manager-gnome notification-daemon notify-osd onboard openoffice.org-gnome openoffice.org-gtk pidgin pidgin-data pidgin-libnotify pidgin-otr pkg-config policykit-gnome pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-utils python-brlapi python-cairo python-fstab python-gconf python-gdata python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnomecanvas python-gst0.10 python-gtk2 python-gtkhtml2 python-gtksourceview2 python-launchpad-integration python-notify python-pkg-resources python-pyatspi python-pyorbit python-rdflib python-sexy python-virtkey python-vte rarian-compat rhythmbox rss-glx scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule scim-modules-socket screen-resolution-extra screensaver-default-images seahorse seahorse-plugins sg3-utils sgml-data software-properties-gtk ssh-askpass-gnome synaptic syslinux system-config-printer-gnome system-tools-backends tangerine-icon-theme tomboy totem totem-common totem-gstreamer totem-mozilla totem-plugins transmission-common transmission-gtk tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-gdm-themes ubuntu-sounds ubuntu-system-service ubuntu-wallpapers update-manager update-notifier usb-creator usplash-theme-ubuntu vinagre vino whois xbitmaps xdg-user-dirs-gtk xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xterm xulrunner-1.9 xulrunner-1.9-gnome-support yelp zenity
```

Then install kde-core

```
sudo apt-get install kde-core
```

---

### Post by rb0171610 on 2009-10-12
> **SuperSonic4 said:**
> Easiest of all would be to reinstall from the minimal cd and install kde-core but this will cause data loss unless you had a separate /home and didn't format it. It's not beginner stuff though CLI partitioning.

---------------------------------------------------

Remove the kubuntu components and the ubuntu components:

```
sudo apt-get remove akregator amarok amarok-common apport-qt ark cdrdao dolphin dontzap dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ijsgutenprint install-package jockey-kde k3b k3b-data kaddressbook kamera kate kde-icons-oxygen kde-printer-applet kde-style-qtcurve kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons kdeplasma-addons-data kdesudo kdm kfind khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete korganizer kpackagekit krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libao2 libaudio2 libavahi-qt3-1 libboost-program-options1.35.0 libclucene0ldbl libdbus-qt-1-1c2 libeet1 libexiv2-5 libflac++6 libgeoip1 libk3b3 libk3b3-extracodecs libkcddb4 libkdecorations4 libkdepim4 libkexiv2-7 libkholidays4 libkipi6 libkleo4 libkonq5 libkonq5-templates libkpgp4 libksieve4 libkwineffects1 libloudmouth1-0 liblua50 liblualib50 libmad0 libmimelib4 libmodplug0c2 libmpcdec3 libmsn0.1 libmysqlclient15off libokularcore1 libpackagekit-glib11 libpackagekit-qt11 libphonon4 libplasma3 libpoppler-qt4-3 libpq5 libqca2 libqca2-plugin-ossl libqedje0 libqimageblitz4 libqt3-mt libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqzion0 libraptor1 librasqal1 librdf0 libsearchclient0 libsoprano4 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libstrigiqtdbusclient0 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-common okular okular-extra-backends openoffice.org-kde openoffice.org-style-crystal oxygen-cursor-theme packagekit packagekit-backend-apt phonon phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-widget-network-manager plasma-widget-quickaccess python-dev python-kde4 python-packagekit python-plasma python-qt4 python-qt4-common python-qt4-dbus python-sip4 python2.6-dev qt4-qtconfig quassel quassel-data raptor-utils redland-utils software-properties-kde soprano-daemon speedcrunch strigi-client strigi-daemon system-config-printer-kde systemsettings ttf-dejavu ttf-dejavu-extra update-manager-kde update-notifier-kde && sudo apt-get remove alacarte app-install-data-partner apport-gtk apturl at-spi binfmt-support bluez-gnome brasero brltty-x11 capplets-data checkbox checkbox-gtk cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf computer-janitor computer-janitor-gtk contact-lookup-applet dcraw desktop-file-utils dmz-cursor-theme doc-base docbook-xml ekiga eog esound-clients esound-common espeak espeak-data evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-indicator evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet file-roller firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support firefox-gnome-support gamin gcalctool gconf-editor gconf2 gconf2-common gdebi gdm gdm-guest-session gedit gedit-common ggzcore-bin gimp gimp-data gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-cards-data gnome-codec-install gnome-control-center gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-mag gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-mount gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-session-canberra gnome-settings-daemon gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu gnome-user-guide gnome-utils gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse human-icon-theme human-theme indicator-applet indicator-messages jockey-gtk language-selector libart2.24-cil libasound2-plugins libatspi1.0-0 libaudiofile0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbabl-0.0-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrasero-media0 libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gtk-module libcanberra-gtk0 libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio7 libcompizconfig0 libcroco3 libcryptui0 libdecoration0 libdmx1 libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13 libesd-alsa0 libespeak1 libevdocument1 libevview1 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libfreezethaw-perl libgadu3 libgail-common libgail-gnome-module libgail18 libgamin0 libgconf2-4 libgconf2.24-cil libgcr0 libgdata-google1.2-1 libgdata1.2-1 libgdict-1.0-6 libgdiplus libgegl-0.0-0 libggz2 libggzcore9 libggzmod4 libgimp2.0 libgksu2-0 libglade2-0 libglade2.0-cil libglew1.5 libglib-perl libglib2.0-cil libglibmm-2.4-1c2a libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime2.2a-cil libgnome-desktop-2-11 libgnome-keyring0 libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-speech7 libgnome-vfs2.24-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomekbd-common libgnomekbd3 libgnomekbdui3 libgnomepanel2.24-cil libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgp11-0 libgpod-common libgpod4 libgsf-1-114 libgsf-1-common libgsm1 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml2-0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview-common libgtksourceview1.0-0 libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgvfscommon0 libgweather-common libgweather1 libhesiod0 libidl0 libiec61883-0 libindicate1 libjpeg-progs libkpathsea4 liblaunchpad-integration1 liblircclient0 liblpint-bonobo0 libmbca0 libmetacity0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-data2.0-cil libmono-getoptions2.0-cil libmono-i18n2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil libnautilus-burn4 libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnotify1 liboil0.3 liboobs-1-4 libopal3.6.1 liborbit2 libpam-gnome-keyring libpanel-applet2-0 libpangomm-1.4-1 libpisock9 libpisync1 libpolkit-gnome0 libpoppler-glib4 libportaudio2 libprotobuf3 libproxy0 libpt2.6.1 libpt2.6.1-plugins-alsa libpt2.6.1-plugins-v4l2 libpulse-browse0 libpulsecore9 libpurple-bin libpurple0 librarian0 librsvg2-2 librsvg2-common libschroedinger-1.0-0 libscim8c2a libsexy2 libsgutils1 libshout3 libsilc-1.1-2 libsndfile1 libsoup-gnome2.4-1 libsoup2.4-1 libspeexdsp1 libsqlite0 libstartup-notification0 libtdb1 libtie-ixhash-perl libtotem-plparser12 libtrackerclient0 libunique-1.0-0 libuuid-perl libv4l-0 libvisual-0.4-0 libvisual-0.4-plugins libvte-common libvte9 libwmf0.2-7-gtk libwnck-common libwnck22 libxml-twig-perl libxml-xpath-perl libxres1 libzephyr3 metacity metacity-common mobile-broadband-provider-info mono-2.0-gac mono-2.0-runtime mono-common mono-gac mono-jit mono-runtime mousetweaks mtools nautilus nautilus-data nautilus-sendto nautilus-share network-manager-gnome notification-daemon notify-osd onboard openoffice.org-gnome openoffice.org-gtk pidgin pidgin-data pidgin-libnotify pidgin-otr pkg-config policykit-gnome pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-utils python-brlapi python-cairo python-fstab python-gconf python-gdata python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnomecanvas python-gst0.10 python-gtk2 python-gtkhtml2 python-gtksourceview2 python-launchpad-integration python-notify python-pkg-resources python-pyatspi python-pyorbit python-rdflib python-sexy python-virtkey python-vte rarian-compat rhythmbox rss-glx scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule scim-modules-socket screen-resolution-extra screensaver-default-images seahorse seahorse-plugins sg3-utils sgml-data software-properties-gtk ssh-askpass-gnome synaptic syslinux system-config-printer-gnome system-tools-backends tangerine-icon-theme tomboy totem totem-common totem-gstreamer totem-mozilla totem-plugins transmission-common transmission-gtk tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-gdm-themes ubuntu-sounds ubuntu-system-service ubuntu-wallpapers update-manager update-notifier usb-creator usplash-theme-ubuntu vinagre vino whois xbitmaps xdg-user-dirs-gtk xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xterm xulrunner-1.9 xulrunner-1.9-gnome-support yelp zenity
```Then install kde-core

```
sudo apt-get install kde-core
```
My concern is that for someone who doesn't know the full functionality of a DE suite, would not know what to install after they have a barebones DE.  If they never had a list of text editors in their start menu, they would not be familiar with them and thus not know what to install.  Similarly, if you never saw the full installation of KDE, you might never know the cd burning software miracle known as K3B.
If you have an older computer, I would say don't try to skimp on the DE.  Switch to Vector Linux or Puppy Linux instead.  I have not found that trimming down KDE to nothing helps anyone with anything.  Ok, I stand corrected.  I remember a few kids in college booting and rebooting their system with a stop watch, excited because they can now login 3 seconds faster. Yippee!!


I just want to say, most people have used XP for years and never thought anything about the fact that Paint and Notepad are in their start menu.  I dont think finding a version of XP without these kinds of programs would save them hard disk space or increase their overall user experience.

---

### Post by nerdy_kid on 2009-10-13
wouldn't sudo apt-get autoremove do the same thing (as removing all those packages)?

---

### Post by rb0171610 on 2009-10-13
> **Falc7 said:**
> I am currently using kubuntu-desktop (and ubuntu), and i would like to switch to kde-base, how do i do that?

My second question is if i have a live cd, how would i install just kde-base?

I just wanted to provide further information for you about the various components of the KDE desktop.  This is from the KDE Project website:

[http://www.kde.org/whatiskde/project.php#usersview](http://www.kde.org/whatiskde/project.php#usersview)

**The Current KDE distribution**

 The current **official** KDE distribution consists of the following packages:
  
[LIST]
[*]KDE-Libs: Various run-time libraries.
[*]KDE-Base: The base components (window-manager, desktop, panel, Konqueror)
[*]KDE-Plasma-Addons: Additional themes and applets for the desktop and panel
[*]KDE-Network: Networking applications such as an instant messenger and download manager.
[*][KDE-Pim]("http://kontact.kde.org/"): Mail client, addressbook, organizer and groupware integration.
[*]KDE-Graphics: Document viewer, image viewer and selected other graphics applications.
[*][KDE-Multimedia]("http://multimedia.kde.org/"): Includes a video player as well as different audio players.
[*][Phonon]("http://phonon.kde.org/"): Multimedia layer that supports different backends, on different operating systems, for multimedia output.
[*][KDE-Accessibility]("http://accessibility.kde.org/"): Applications to improve computer access for disabled people such as a text-to-speech system.
[*][KDE-Utilities]("http://utils.kde.org/"): Useful utilities like an archiving tool and a calculator.
[*][KDE-Edu]("http://edu.kde.org/"): Education and science applications.
[*][KDE-Games]("http://games.kde.org/"): Classic and modern games.
[*]KDE-Toys: KDE's fun stuff.
[*][KDE-Artwork]("http://kde-artists.org/"): Additional icons, styles, wallpapers, screensavers and window decorations.
[*]KDE-Admin: Various tools to aid with system administration.
[*]KDE-SDK: Script and tools which simplify development of KDE applications.
[*][KOffice]("http://koffice.org/"): Integrated office suite.
[*][KDevelop]("http://kdevelop.org/"): C/C++ Integrated Development Environment.
[*]KDE-Bindings: bindings for various programming languages (Python, Ruby, Perl, Java...).
[*][KDEWebdev]("http://www.kdewebdev.org/"): Web development applications and tools.
[/LIST]
  Two pseudo-packages **not part of the official release** are also available.
 
[LIST]
[*][KDE-Extragear]("http://extragear.kde.org/"): Extragear is a collection of applications associated with the KDE project, not part of the official release for various reasons. These are however still part of the project and can be downloaded separately. This gives them higher visibility to Translators and Documentation Writers.
[*]KDE-Playground: Similar to KDE-Extragear, this pseudo-package also contains software not part of the main KDE release.
[/LIST]
  And last but certainly not the least, there are literally thousands of excellent KDE applications not part of KDE releases or the Official KDE project. You can find these using KDE's [central database]("http://www.kde-apps.org/").


Hopefully this information will give you some insight as to what packages are essential to your particular setup.

---

### Post by Falc7 on 2009-10-13
thanks :)

---

### Post by mechanic on 2009-10-26
Full marks to the OP for wanting to start from the ground up to define a working system, KDE is rather bloated in the default install (at least three editors and two browsers!!) and - unlike with the Debian installer - there seems no way of getting the installer CD to just get you to a working command prompt system (unless you use the Ubuntu server installer and just install the minimum from that, adding kde-core afterwards). Stripping all the junk out of the standard install can take a while, but is does save lots of MB of disk space. Some of us are using 4GB of SD or SSD to hold these systems!
[later edit] Or use the Minimal CD install - [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

