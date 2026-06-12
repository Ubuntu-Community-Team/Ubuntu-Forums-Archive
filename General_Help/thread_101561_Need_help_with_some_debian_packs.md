---
title: "Need help with some debian packs"
date: 2005-12-10
forum: General Help
---

### Post by JonassanoJ on 2005-12-10
Hello, i tried to install xmoto from a .deb pack i found [here]("http://packages.debian.org/unstable/games/xmoto").
After that i got the update logo in the right corner of my screen that said 6packs are broken.
I tried "dpkg -r" but libgcc1 needed other packs and stuff. so that dident work.
apt-get -f install is deleting every single (almost) program that i have installed..

alien azureus bluefish bluez-pin bug-buddy build-essential camorama
capplets-data contact-lookup-applet cpp cpp-4.0 dcgui debhelper dh-make eog
evince evolution evolution-data-server evolution-exchange evolution-plugins
evolution-webcal fglrx-kernel-source file-roller firefox
firefox-gnome-support g++ g++-4.0 gcalctool gcc gcc-4.0 gconf-editor gconf2
gdesklets gdesklets-data gdm gedit gettext ghex gij gij-4.0 gnome-about
gnome-app-install gnome-applets gnome-applets-data gnome-art
gnome-btdownload gnome-control-center gnome-cups-manager gnome-games
gnome-media gnome-netstatus-applet gnome-nettool gnome-panel
gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-spell
gnome-splashscreen-manager gnome-system-monitor gnome-system-tools
gnome-terminal gnome-themes-extras gnome-utils gnome-volume-manager
gnomebaker gnomemeeting gstreamer0.8-gnomevfs gstreamer0.8-misc
gstreamer0.8-vorbis gthumb gtk2-engines-spherecrystal gtkhtml3.8 gucharmap
hal-device-manager hwdb-client intltool-debian j2re1.4-mozilla-plugin
java-gcj-compat libbonobo2-0 libbonobo2-common libbonoboui2-0 libcamel1.2-6
libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1
libedataserver1.2-4 libedataserverui1.2-6 libeel2-2 libegroupwise1.2-8
libexchange-storage1.2-0 libgcj6 libgcj6-common libgconf2-4 libgconf2-ruby
libgnome-desktop-2 libgnome2-0 libgnome2-common libgnome2-perl
libgnome2-vfs-perl libgnomecupsui1.0-1 libgnomeui-0 libgnomevfs2-0
libgnomevfs2-common libgsf-1 libgstreamer-gconf0.8-0 libgtkhtml3.8-15
libgucharmap4 libhsqldb-java libidl0 liblpint-bonobo0 libmetacity0
libnautilus-extension1 liborbit2 libpanel-applet2-0 librsvg2-2
librsvg2-common libservlet2.3-java libstdc++6-4.0-dev libswt-gtk-3.1-java
libswt-gtk-3.1-jni libtotem-plparser0 metacity nautilus nautilus-cd-burner
nautilus-sendto openoffice.org2 openoffice.org2-base openoffice.org2-gnome
po-debconf python-gnome2 python-gnome2-extras python-pyorbit
python2.4-gnome2 python2.4-gnome2-extras python2.4-pyorbit rhythmbox
serpentine sound-juicer totem totem-gstreamer tsclient ubuntu-desktop
update-manager update-notifier vino yelp


Can someone help me, saving my ubuntu breezy
jonas@Linda:~$ uname -mor
2.6.12-9-386 i686 GNU/Linux

Btw: sorry for my english, im from norway :P

---

### Post by invalid on 2005-12-10
Open synaptic, and choose "Fix Broken Packages" in the Edit menu.

Cheers,
Cb

---

### Post by JonassanoJ on 2005-12-10
Yeah sure BUT one problem with that..


alien azureus bluefish bluez-pin bug-buddy build-essential camorama
capplets-data contact-lookup-applet cpp cpp-4.0 dcgui debhelper dh-make eog
evince evolution evolution-data-server evolution-exchange evolution-plugins
evolution-webcal fglrx-kernel-source file-roller firefox
firefox-gnome-support g++ g++-4.0 gcalctool gcc gcc-4.0 gconf-editor gconf2
gdesklets gdesklets-data gdm gedit gettext ghex gij gij-4.0 gnome-about
gnome-app-install gnome-applets gnome-applets-data gnome-art
gnome-btdownload gnome-control-center gnome-cups-manager gnome-games
gnome-media gnome-netstatus-applet gnome-nettool gnome-panel
gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-spell
gnome-splashscreen-manager gnome-system-monitor gnome-system-tools
gnome-terminal gnome-themes-extras gnome-utils gnome-volume-manager
gnomebaker gnomemeeting gstreamer0.8-gnomevfs gstreamer0.8-misc
gstreamer0.8-vorbis gthumb gtk2-engines-spherecrystal gtkhtml3.8 gucharmap
hal-device-manager hwdb-client intltool-debian j2re1.4-mozilla-plugin
java-gcj-compat libbonobo2-0 libbonobo2-common libbonoboui2-0 libcamel1.2-6
libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1
libedataserver1.2-4 libedataserverui1.2-6 libeel2-2 libegroupwise1.2-8
libexchange-storage1.2-0 libgcj6 libgcj6-common libgconf2-4 libgconf2-ruby
libgnome-desktop-2 libgnome2-0 libgnome2-common libgnome2-perl
libgnome2-vfs-perl libgnomecupsui1.0-1 libgnomeui-0 libgnomevfs2-0
libgnomevfs2-common libgsf-1 libgstreamer-gconf0.8-0 libgtkhtml3.8-15
libgucharmap4 libhsqldb-java libidl0 liblpint-bonobo0 libmetacity0
libnautilus-extension1 liborbit2 libpanel-applet2-0 librsvg2-2
librsvg2-common libservlet2.3-java libstdc++6-4.0-dev libswt-gtk-3.1-java
libswt-gtk-3.1-jni libtotem-plparser0 metacity nautilus nautilus-cd-burner
nautilus-sendto openoffice.org2 openoffice.org2-base openoffice.org2-gnome
po-debconf python-gnome2 python-gnome2-extras python-pyorbit
python2.4-gnome2 python2.4-gnome2-extras python2.4-pyorbit rhythmbox
serpentine sound-juicer totem totem-gstreamer tsclient ubuntu-desktop
update-manager update-notifier vino yelp

Will also be deleted...

---

### Post by JonassanoJ on 2005-12-10
*bump*

---

### Post by JonassanoJ on 2005-12-10
*bump* 2. time

Soon im going over to slack!

---

