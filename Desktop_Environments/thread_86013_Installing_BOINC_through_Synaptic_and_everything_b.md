---
title: "Installing BOINC through Synaptic and everything breaks"
date: 2005-11-04
forum: Desktop Environments
---

### Post by ubuntunewb75 on 2005-11-04
Hello, I tried to install BOINC through Syanptic and it gace a list of files that weren't able to be installed, which was thus:

[I]boinc-manager:
  Depends: libcurl3 (>=7.15.0-1) but 7.14.0-2ubuntu1.1 is to be installed
  Depends: libidn11 (>=0.5.18) but 0.5.13-1.0 is to be installed
 Depends: libssl0.9.8  but it is not installable
  Depends: libstdc++6 (>=4.0.2) but 4.0.1-4ubuntu9 is to be installed
  Depends: libwxgtk2.6-0 (>=2.6.1.2) but 2.6.1.1.1ubuntu2 is to be installed[/I]

after hunting down the .deb packages for these files and installing them, I get this message in Synaptic after trying to install or upgrade anything :

[I]alien will be removed
antlr will be removed
bluez-pin will be removed
bsh will be removed
bug-buddy will be removed
build-essential will be removed
capplets-data will be removed
contact-lookup-applet will be removed
cpp will be removed
cpp-4.0 will be removed
debhelper will be removed
ecj-bootstrap will be removed
eog will be removed
evince will be removed
evolution will be removed
evolution-data-server will be removed
evolution-exchange will be removed
evolution-plugins will be removed
evolution-webcal will be removed
file-roller will be removed
firefox will be removed
firefox-gnome-support will be removed
g++ will be removed
g++-4.0 will be removed
gcalctool will be removed
gcc will be removed
gcc-4.0 will be removed
gcj-4.0 will be removed
gconf-editor will be removed
gconf2 will be removed
gdm will be removed
gedit will be removed
gettext will be removed
gij will be removed
gij-4.0 will be removed
gjdoc will be removed
gnome-about will be removed
gnome-app-install will be removed
gnome-applets will be removed
gnome-applets-data will be removed
gnome-bin will be removed
gnome-btdownload will be removed
gnome-control-center will be removed
gnome-cups-manager will be removed
gnome-games will be removed
gnome-libs-data will be removed
gnome-media will be removed
gnome-netstatus-applet will be removed
gnome-nettool will be removed
gnome-panel will be removed
gnome-panel-data will be removed
gnome-pilot will be removed
gnome-pilot-conduits will be removed
gnome-session will be removed
gnome-spell will be removed
gnome-system-monitor will be removed
gnome-system-tools will be removed
gnome-terminal will be removed
gnome-utils will be removed
gnome-volume-manager will be removed
gnomebaker will be removed
gnomemeeting will be removed
gstreamer0.8-gnomevfs will be removed
gstreamer0.8-misc will be removed
gstreamer0.8-vorbis will be removed
gthumb will be removed
gtkhtml3.8 will be removed
gucharmap will be removed
gweled will be removed
hal-device-manager will be removed
hwdb-client will be removed
intltool-debian will be removed
java-gcj-compat will be removed
java-gcj-compat-dev will be removed
libbonobo2-0 will be removed
libbonobo2-common will be removed
libbonoboui2-0 will be removed
libcamel1.2-6 will be removed
libebook1.2-5 will be removed
libecal1.2-3 will be removed
libedata-book1.2-2 will be removed
libedata-cal1.2-1 will be removed
libedataserver1.2-4 will be removed
libedataserverui1.2-6 will be removed
libeel2-2 will be removed
libegroupwise1.2-8 will be removed
libexchange-storage1.2-0 will be removed
libgcj6 will be removed
libgcj6-awt will be removed
libgcj6-common will be removed
libgcj6-dev will be removed
libgconf2-4 will be removed
libgnome-desktop-2 will be removed
libgnome2-0 will be removed
libgnome2-common will be removed
libgnome2-perl will be removed
libgnome2-vfs-perl will be removed
libgnome32 will be removed
libgnomecupsui1.0-1 will be removed
libgnomesupport0 will be removed
libgnomeui-0 will be removed
libgnomeui32 will be removed
libgnomevfs2-0 will be removed
libgnomevfs2-common will be removed
libgnorba27 will be removed
libgnorbagtk0 will be removed
libgnucrypto-java will be removed
libgnujaxp-java will be removed
libgsf-1 will be removed
libgstreamer-gconf0.8-0 will be removed
libgtkhtml3.8-15 will be removed
libgucharmap4 will be removed
libhsqldb-java will be removed
libidl0 will be removed
libjaxp1.2-java will be removed
libjessie-java will be removed
liblpint-bonobo0 will be removed
libmetacity0 will be removed
libnautilus-extension1 will be removed
liborbit0 will be removed
liborbit2 will be removed
libpanel-applet2-0 will be removed
librsvg2-2 will be removed
librsvg2-common will be removed
libservlet2.3-java will be removed
libstdc++6-4.0-dev will be removed
libtotem-plparser0 will be removed
libxalan2-java will be removed
libxerces2-java will be removed
libxt-java will be removed
metacity will be removed
mozilla-mplayer will be removed
nautilus will be removed
nautilus-cd-burner will be removed
nautilus-sendto will be removed
openoffice.org2 will be removed
openoffice.org2-base will be removed
openoffice.org2-calc will be removed
openoffice.org2-common will be removed
openoffice.org2-core will be removed
openoffice.org2-draw will be removed
openoffice.org2-evolution will be removed
openoffice.org2-gnome will be removed
openoffice.org2-impress will be removed
openoffice.org2-java-common will be removed
openoffice.org2-math will be removed
openoffice.org2-writer will be removed
po-debconf will be removed
python-gnome2 will be removed
python-gnome2-extras will be removed
python-pyorbit will be removed
python-uno will be removed
python2.4-gnome2 will be removed
python2.4-gnome2-extras will be removed
python2.4-pyorbit will be removed
rhythmbox will be removed
serpentine will be removed
sound-juicer will be removed
totem will be removed
totem-gstreamer will be removed
tsclient will be removed
ubuntu-desktop will be removed
update-manager will be removed
update-notifier will be removed
vino will be removed
xwine will be removed
yelp will be removed[/I]

It gives me this message even if I try to just remove the .deb packages I installed using dpkg.  Any help on resolving this issues wuld be greatly appreciated!

---

### Post by dcstar on 2005-11-04
[QUOTE=ubuntunewb75]Hello, I tried to install BOINC through Syanptic and it gace a list of files that weren't able to be installed, which was thus:
........[/QUOTE]
Boinc doesn't appear in my Synaptic list, what repository did you use to get it?

I have my own Boinc running from a manual install of a .deb package.

---

### Post by veehell on 2005-12-03
Fix your repository or install boinc by another way not via "synaptic"
try command line apt-get. And as the post above mine, check your repository as 1st step, and i suggest you to use only "correct one" (you can sellect which repository types you want to list and how the synaptic manager will work) 

or
[http://boinc.berkeley.edu/download.php](http://boinc.berkeley.edu/download.php)

here is some additional official or unofficial ones ;) (as i know, the package the correct one, always download the "fresh one" package via "wget" (my installation failed on this step, no possible retrieve of tar.gz file with source. So i downloaded manually and proceed by ./config make make install tria-command ;) to have it.
Ok i am talking too much....good luck.

---

