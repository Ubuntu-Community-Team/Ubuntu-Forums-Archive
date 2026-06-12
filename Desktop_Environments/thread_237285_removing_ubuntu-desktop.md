---
title: "removing ubuntu-desktop"
date: 2006-08-15
forum: Desktop Environments
---

### Post by bonjun on 2006-08-15
hi there,

i have successfully upgrade from breezy to dapper, using dist-upgrade,,
i want to replace my ubuntu-desktop with xubuntu-desktop, due to hardware limitation,, ubuntu-desktop runs very slow on this pc...
i want to try xubuntu-desktop on this pc, but the problem is i can't remove my ubuntu-desktop

i've use apt-get, and give me this result:
> user@pc:~$ sudo apt-get remove ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Package ubuntu-desktop is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


in synaptic and search for ubuntu-desktop, but to my surprise there is no desktop installed but in reality there is and I'm using it right now...\

how can i remove my current desktop and install xubuntu-desktop?

on the contrary i can install xubuntu-desktop but i have a problem of disk space, so this is not an option...

TIA

---

### Post by meng on 2006-08-15
Short answer: ubuntu-desktop is just a metapackage. Removing it does not remove all of its dependencies, namely GNOME + many apps.

Check this out if you want to remove GNOME completely:
[http://www.psychocats.net/ubuntu/purexfce.php](http://www.psychocats.net/ubuntu/purexfce.php)

Then after doing this, you can sudo aptitude install xubuntu-desktop, and you'll have a pure XFCE.

---

### Post by skale on 2006-08-15
What I guess happened was that a number of programs depend on gnome to run, and so did not remove it. If it did, you would notice that a chunk of your program collection would not run. Also, you used apt-get, which will not all of the extra programs required for [I]gnome itself to run[/I.]Can you install xubuntu-desktop first, and then try removing it again? This time, type "sudo aptitude remove ubuntu-desktop".

---

### Post by aysiu on 2006-08-15
*ubuntu-desktop* is only a metapackage.

Since you're low on disk space, I'd do something like this:

1. ```
cd
gedit removegnome
``` Paste in this code: ```
#!/bin/bash
sudo apt-get remove alacarte app-install-data app-install-data-commercial at-spi bicyclerepair bittorrent blt bluez-cups bluez-pcmcia-support bluez-pin bluez-utils brltty brltty-x11 bsh bug-buddy ca-certificates capplets-data contact-lookup-applet deskbar-applet diveintopython ekiga eog esound esound-common evince evolution evolution-data-server evolution-exchange evolution-plugins evolution-webcal fastjar festival festlex-cmu festlex-poslex festvox-kallpc16k file-roller firefox-gnome-support fping gcalctool gcj-4.1-base gconf-editor gdb gedit gedit-common gij-4.1 gimp-python gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-mag gnome-media gnome-menus gnome-mime-data gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gnopernicus gok gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-lighthouseblue gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-thinice gtkhtml3.8 gucharmap guile-1.6-libs hal-device-manager hwdb-client java-common java-gcj-compat libadns1 libatspi1.0-0 libaudio2 libavahi-client3 libavahi-common-data libavahi-common3 libavahi-glib1 libavc1394-0 libbeagle0 libbluetooth1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrlapi1 libbtctl2 libcamel1.2-8 libcdio6 libcompfaceg1 libcurl3 libcurl3-gnutls libdv4 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-7 libedataserverui1.2-6 libeel2-2 libeel2-data libegroupwise1.2-9 libesd-alsa0 libestools1.2 libexchange-storage1.2-1 libflac7 libgail-common libgail-gnome-module libgail17 libgcj-common libgcj7 libgcj7-jar libgd2-noxpm libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common libgeoip1 libglew1 libglib-perl libgmp3c2 libgnome-desktop-2 libgnome-mag2 libgnome-menu2 libgnome-pilot2 libgnome-speech3 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomebt0 libgnomecupsui1.0-1c2a libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgnucrypto-java libgphoto2-2 libgphoto2-port0 libgpod0 libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk2-perl libgtkhtml2-0 libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libgtop2-7 libgucharmap4 libguile-ltdl-1 libhsqldb-java libicu34 libid3-3.8.3c2a libidn11 libieee1284-3 libjasper-1.701-1 libjaxp1.2-java libjessie-java libjline-java liblircclient0 liblpint-bonobo0 libmagick9 libmdbtools libmetacity0 libmusicbrainz4c2a libmysqlclient15off libnautilus-burn3 libnautilus-extension1 libneon25 libnetcdf3 libnotify1 liboil0.3 libopal-2.2.0 libopenobex-1.0-0 libpanel-applet2-0 libpisock8 libpisync0 libportaudio0 libpq4 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 libraptor1 librasqal0 libraw1394-5 librdf0 libsane libsdl1.2debian libsdl1.2debian-alsa libservlet2.3-java libsexy2 libshout3 libsmbclient libsndfile1 libsoup2.2-8 libsqlite0 libsqlite3-0 libstlport4.6c2 libtotem-plparser1 libvorbisenc2 libvorbisfile3 libwnck-common libwnck18 libxalan2-java libxerces2-java libxklavier10 libxml2-utils libxmlsec1 libxmlsec1-nss libxmlsec1-openssl libxres1 libxt-java metacity mysql-common nautilus nautilus-cd-burner nautilus-data nautilus-sendto notification-daemon openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-java-common openoffice.org-math openoffice.org-writer openssl pkg-config python-adns python-cddb python-clientcookie python-crypto python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-epydoc python-eunuchs python-examples python-gadfly python-gd python-gdbm python-genetic python-geoip python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras python-gst0.10 python-htmlgen python-htmltmpl python-id3lib python-imaging python-imaging-sane python-jabber python-kjbuckets python-launchpad-integration python-ldap python-libxml2 python-mysqldb python-netcdf python-newt python-numeric python-pam python-parted python-pexpect python-pgsql python-pisock python-pqueue python-pyao python-pylibacl python-pyogg python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr python-reportlab python-simpletal python-soappy python-sqlite python-stats python-syck python-tk python-unit python-uno python-xdg python-xml python-xmpp python2.4-adns python2.4-clientcookie python2.4-crypto python2.4-dbus python2.4-dictclient python2.4-egenix-mxdatetime python2.4-egenix-mxproxy python2.4-egenix-mxstack python2.4-egenix-mxtexttools python2.4-egenix-mxtools python2.4-epydoc python2.4-eunuchs python2.4-examples python2.4-gadfly python2.4-gd python2.4-gdbm python2.4-geoip python2.4-gnome2 python2.4-gnome2-desktop python2.4-gnome2-extras python2.4-htmlgen python2.4-htmltmpl python2.4-id3lib python2.4-imaging python2.4-imaging-sane python2.4-jabber python2.4-kjbuckets python2.4-ldap python2.4-librdf python2.4-libxml2 python2.4-libxslt1 python2.4-mysqldb python2.4-pam python2.4-pexpect python2.4-pgsql python2.4-pycurl python2.4-pylibacl python2.4-pyopenssl python2.4-pyorbit python2.4-pyxattr python2.4-reportlab python2.4-simpletal python2.4-soappy python2.4-sqlite python2.4-syck python2.4-tk python2.4-unit python2.4-xml python2.4-xmpp rdesktop rhythmbox rss-glx screensaver-default-images serpentine sound-juicer ssh-askpass-gnome tangerine-icon-theme tcl8.4 tk8.4 totem totem-gstreamer tsclient ttf-opensymbol ubuntu-desktop ubuntu-docs update-notifier vino vnc-common whois xsane xsane-common xsltproc xvncviewer yelp zenity
``` Exit Gedit. ```
chmod +x removegnome
```

2. Control-Alt-F1. This will bring you to a huge terminal.

3. Log in and type ```
sudo /etc/init.d/gdm stop
``` This will stop the Gnome Display Manager.

4. ```
./removegnome
``` This will remove a lot of crap so that you're left with almost nothing but a barebones system.

5. ```
sudo apt-get clean
``` This will remove all the old .deb files from the /var/cache/apt/archives folder to free up even more space.

6. ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
``` This will install Xubuntu.

7. ```
sudo /etc/init.d/gdm start
``` This will restart the Gnome Display Manager... but this time with Xubuntu!

---

### Post by bonjun on 2006-08-15
thanks for the reply guys,, i will post on the result later on,,,, thanks again

---

### Post by skale on 2006-08-15
What I guess happened was that a number of programs depend on gnome to run, and so did not remove it. If it did, you would notice that a chunk of your program collection would not run. Also, you used apt-get, which will not all of the extra programs required for [I]gnome itself to run[/I.]Can you install xubuntu-desktop first, and then try removing it again? This time, type "sudo aptitude remove ubuntu-desktop".

---

### Post by bonjun on 2006-08-16
i have done,,, thanks for the help

---

### Post by 3rdalbum on 2006-08-16
Just for everyone's future reference, you can uninstall Gnome will still running it.

---

