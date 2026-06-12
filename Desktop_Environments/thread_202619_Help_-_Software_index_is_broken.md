---
title: "Help - Software index is broken"
date: 2006-06-23
forum: Desktop Environments
---

### Post by Scorpuk on 2006-06-23
tried to build deb packaes for madwifi card i installed and got totally screwed up. So gave up and reconnected wired network, but after rebooting I had updates to do.

BUT now I can no longer run updates. I get told to do sudo apt-get install -f

unfortunately that doesnt work either, as you can see: -

> 
john@ubuntu-box:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies...Done
The following extra packages will be installed:
  libc6-i686 tzdata
The following NEW packages will be installed
  tzdata
The following packages will be upgraded:
  libc6-i686
1 upgraded, 1 newly installed, 0 to remove and 651 not upgraded.
2 not fully installed or removed.
Need to get 0B/1439kB of archives.
After unpacking 6005kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  tzdata libc6-i686
Install these packages without verification [y/N]? y
(Reading database ... 113377 files and directories currently installed.)
Unpacking tzdata (from .../tzdata_2006g-2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/tzdata_2006g-2_all.deb (--unpack):
 trying to overwrite `/usr/share/zoneinfo/Africa/Algiers', which is also in package locales
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/tzdata_2006g-2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any help would be most appreciated and please be specific as I am new to linux. Be gentle :-)

---

### Post by Ramses de Norre on 2006-06-23
Can you try to run sudo aptitude purge on those two packages? And install them back then, doing that solved similar problems here.
Don't do it if aptitude wants to remove hundreds of packages when you run it =)

---

### Post by Scorpuk on 2006-06-23
ok done that and I get this ( a bit long)

> 
john@ubuntu-box:~$ sudo aptitude purge
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libc6 libc6-i686
The following packages have been kept back:
  acpid adduser alacarte alsa-base alsa-utils apmd apt apt-utils aptitude
  aspell at at-spi atitvout base-files bash beep-media-player
  belocs-locales-bin binutils blt bluez-cups bluez-pcmcia-support bluez-pin
  bluez-utils brltty brltty-x11 bsdmainutils bsdutils bsh bug-buddy
  build-essential bzip2 capplets-data cdparanoia cdrdao cdrecord
  console-common console-data console-tools coreutils cpio cpp cpp-4.0 cron
  cupsys cupsys-bsd cupsys-client dbus dbus-1-utils debconf debconf-i18n
  debianutils dhcdbd dhcp3-client dhcp3-common dictionaries-common
  discover1 discover1-data dmidecode dmsetup doc-base doc-debian
  docbook-xml dpkg dpkg-dev dselect dvd+rw-tools e2fslibs e2fsprogs eject
  eog evms evms-ncurses evolution evolution-data-server evolution-plugins
  evolution-webcal fastjar file file-roller findutils firefox
  firefox-gnome-support flashplugin-nonfree fontconfig foo2zjs foomatic-db
  foomatic-db-engine foomatic-db-hpijs foomatic-filters
  foomatic-filters-ppds freeglut3 g++ g++-4.0 gaim gaim-data gamin
  gcalctool gcc gcc-3.3-base gcc-4.0 gcc-4.0-base gcj-4.1-base gconf-editor
  gdb gdebi gedit gedit-common gettext gettext-base gftp gftp-common
  gftp-gtk gftp-text gij-4.1 gksu gnome-about gnome-applets
  gnome-applets-data gnome-btdownload gnome-control-center
  gnome-desktop-data gnome-games gnome-games-data gnome-icon-theme
  gnome-menus gnome-nettool gnome-power-manager gnome-session
  gnome-system-tools gnome-terminal gnome-terminal-data gnome-utils
  gnome-volume-manager gnopernicus gnupg gok grep groff-base grub
  gsfonts-x11 gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-ffmpeg
  gstreamer0.10-gnomevfs gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good
  gstreamer0.10-plugins-ugly gstreamer0.10-tools gstreamer0.10-x
  gtk2-engines-pixbuf gucharmap guile-1.6-libs gzip hal hal-device-manager
  hdparm hostname hwdata info initramfs-tools initscripts intltool-debian
  iproute irssi java-common java-gcj-compat klibc-utils klogd
  laptop-mode-tools less lftp liba52-0.7.4 libacl1 libao2
  libapache2-mod-php4 libapm1 libartsc0 libasound2 libaspell15 libatk1.0-0
  libatspi1.0-0 libattr1 libaudio2 libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-glib1 libavc1394-0 libbeagle0 libblkid1
  libbluetooth1 libbonobo2-0 libbonobo2-common libbonoboui2-0
  libbonoboui2-common libbrlapi1 libbz2-1.0 libcairo2 libcamel1.2-8
  libcdparanoia0 libcomerr2 libcompfaceg1 libconsole
  libcrypt-passwdmd5-perl libcupsimage2 libcupsys2 libcurl3 libcurl3-gnutls
  libdbd-mysql-perl libdbi-perl libdbus-1-2 libdbus-glib-1-2
  libdevmapper1.02 libdiscover1 libdjvulibre15 libdmx1 libdrm2 libdv4
  libdvbpsi4 libdvdread3 libebook1.2-5 libecal1.2-3 libedata-book1.2-2
  libedata-cal1.2-1 libedataserver1.2-7 libedataserverui1.2-6 libeel2-2
  libeel2-data libegroupwise1.2-9 libelfg0 libestools1.2 libevms-2.5
  libexchange-storage1.2-1 libexif12 libexpat1 libflac7 libfontconfig1
  libfontenc1 libfreetype6 libfribidi0 libfs6 libgail-common
  libgail-gnome-module libgail17 libgamin0 libgcc1 libgcj-common libgcj7
  libgcj7-jar libgd2-noxpm libgda2-3 libgda2-common libgdbm3 libgdl-1-0
  libgdl-1-common libgeoip1 libggi2 libgii0 libgii0-target-x
  libgl1-mesa-dri libglew1 libglib-perl libglibmm-2.4-1c2a libglu1-mesa
  libgnome-desktop-2 libgnome-menu2 libgnome2-0 libgnome2-canvas-perl
  libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomecanvas2-0
  libgnomecanvas2-common libgnomecups1.0-1 libgnomeprint2.2-0
  libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common
  libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin
  libgnomevfs2-common libgnomevfs2-extra libgnucrypto-java libgnutls12
  libgpg-error0 libgphoto2-2 libgphoto2-port0 libgpmg1 libgpod0
  libgsf-1-common libgstreamer-plugins-base0.10-0 libgstreamer0.10-0
  libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkmm-2.4-1c2a
  libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgucharmap4
  libguile-ltdl-1 libhal-storage1 libhal1 libhsqldb-java libidl0 libidn11
  libiw28 libjessie-java libjline-java libjpeg62 libklibc libkpathsea4
  libkrb53 liblcms1 libldap2 liblircclient0 libltdl3 libmagic1 libmagick9
  libmdbtools libmetacity0 libmms0 libmng1 libmusicbrainz4c2a
  libmysqlclient15off libnautilus-extension1 libncurses5 libncursesw5
  libnet-daemon-perl libnet-ssleay-perl libnetcdf3 libnm-util0 libnotify1
  libogg0 liboggflac3 liboil0.3 libopal-2.2.0 liborbit2 libpam-modules
  libpam-runtime libpam0g libpango1.0-0 libpango1.0-common libpaper1
  libparted1.6-13 libpcap0.8 libpcre3 libperl5.8 libpisock8 libpisync0
  libplrpc-perl libpng12-0 libpopt0 libpq4 libpt-1.10.0 libpt-plugins-alsa
  libpt-plugins-v4l libpt-plugins-v4l2 libqt3-mt libqthreads-12 libraptor1
  librasqal0 librdf0 libsane libsasl2 libsasl2-modules libscim8c2a
  libsdl1.2debian libsdl1.2debian-alsa libselinux1 libsepol1
  libservlet2.3-java libshout3 libslang2 libsndfile1 libsnmp-base libsnmp9
  libsoup2.2-8 libspeex1 libsqlite3-0 libss2 libssl0.9.8 libstdc++5
  libstdc++6 libstdc++6-4.0-dev libswfdec0.3 libsysfs2 libtag1c2a libtagc0
  libtasn1-2 libtheora0 libtiff4 libungif4g libuniconf4.2 libusb-0.1-4
  libuuid1 libvorbis0a libvorbisenc2 libvorbisfile3 libwnck-common
  libwnck18 libwpd8c2a libwrap0 libwvstreams4.2-base libwvstreams4.2-extras
  libwxgtk2.6-0 libx11-6 libxalan2-java libxau6 libxcursor1 libxdamage1
  libxdmcp6 libxerces2-java libxfixes3 libxfont1 libxft2 libxkbfile1
  libxklavier10 libxml2 libxml2-utils libxmlsec1 libxmlsec1-nss
  libxmlsec1-openssl libxosd2 libxp6 libxpm4 libxrandr2 libxrender1
  libxres1 libxslt1.1 libxss1 libxt-java libxt6 libxxf86dga1 libxxf86misc1
  libxxf86vm1 libzzip-0-12 linux-kernel-headers linux-sound-base login
  logrotate lsb-base lsb-release lsof ltrace lvm2 make makedev manpages
  mdadm menu-xdg mesa-utils metacity mime-support mkisofs module-init-tools
  mount mozilla-mplayer mtr-tiny mysql-admin mysql-admin-common
  mysql-client mysql-client-5.0 mysql-common mysql-server mysql-server-5.0
  nano nautilus nautilus-data nautilus-sendto ncurses-base ncurses-bin
  net-tools netbase netcat network-manager network-manager-gnome
  notification-daemon odbcinst1debian1 openssh-client openssl parted passwd
  patch pciutils pcmcia-cs pcmciautils perl perl-base perl-modules
  php4-common php4-mysql php5-cgi php5-common phpbb2 phpbb2-conf-mysql
  phpbb2-languages po-debconf popularity-contest powermgmt-base pppconfig
  pppoeconf procmail procps psmisc python-adns python-apt python-cddb
  python-epydoc python-gdbm python-gmenu python-gnupginterface
  python-htmltmpl python-jabber python-ldap python-libxml2 python-mysqldb
  python-netcdf python-newt python-numeric python-pam python-pexpect
  python-pgsql python-pisock python-pylibacl python-pyopenssl
  python-pyxattr python-reportlab python-simpletal python-syck python-tk
  python-unit python-xml python-xmpp python2.4 python2.4-adns python2.4-apt
  python2.4-dbus python2.4-examples python2.4-htmltmpl python2.4-jabber
  python2.4-ldap python2.4-librdf python2.4-libxml2 python2.4-libxslt1
  python2.4-minimal python2.4-mysqldb python2.4-numeric python2.4-pam
  python2.4-pexpect python2.4-pgsql python2.4-pycurl python2.4-pylibacl
  python2.4-pyopenssl python2.4-pyxattr python2.4-reportlab
  python2.4-simpletal python2.4-xml python2.4-xmpp rar rcconf reiserfsprogs
  reportbug rhythmbox rss-glx rsync scim scim-gtk2-immodule
  scim-modules-socket sed shared-mime-info slocate ssh-askpass-gnome strace
  streamripper sudo synaptic sysklogd system-tools-backends sysv-rc
  sysvinit tar tcl8.4 tcpd tcpdump tk8.4 ttf-arabeyes ttf-arphic-ukai
  ttf-bitstream-vera ttf-dejavu ttf-gentium ttf-kochi-gothic
  ttf-kochi-mincho ttf-thai-tlwg ucf unixodbc unrar unzip update-manager
  update-notifier util-linux vim vim-common vim-runtime vino vnc-common
  vncserver vorbis-tools webalizer whiptail whois wireless-tools
  wpasupplicant wvdial wwwconfig-common x-ttcidfont-conf
  x-window-system-core x11-common xbase-clients xcursor-themes
  xfonts-100dpi xfonts-75dpi xfonts-base xfonts-scalable xfonts-utils
  xfsprogs xml-core xmms xpmutils xresprobe xsane xsane-common
  xscreensaver-gl xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-elographics xserver-xorg-input-kbd
  xserver-xorg-input-mouse xserver-xorg-input-synaptics xsltproc xterm
  xutils xvncviewer yelp zenity zlib1g
0 packages upgraded, 0 newly installed, 0 to remove and 652 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-13 is installed.
  libc6: Depends: tzdata but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
tzdata [2006g-2 (testing)]

Upgrade the following packages:
libc6-i686 [2.3.6-0ubuntu20 (dapper, now) -> 2.3.6-13 (testing)]

Score is -72

Accept this solution? [Y/n/q/?] y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  libc6-i686 tzdata

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes
The following NEW packages will be automatically installed:
  tzdata
The following packages have been kept back:
  acpid adduser alacarte alsa-base alsa-utils apmd apt apt-utils aptitude
  aspell at at-spi atitvout base-files bash beep-media-player
  belocs-locales-bin binutils blt bluez-cups bluez-pcmcia-support bluez-pin
  bluez-utils brltty brltty-x11 bsdmainutils bsdutils bsh bug-buddy
  build-essential bzip2 capplets-data cdparanoia cdrdao cdrecord
  console-common console-data console-tools coreutils cpio cpp cpp-4.0 cron
  cupsys cupsys-bsd cupsys-client dbus dbus-1-utils debconf debconf-i18n
  debianutils dhcdbd dhcp3-client dhcp3-common dictionaries-common
  discover1 discover1-data dmidecode dmsetup doc-base doc-debian
  docbook-xml dpkg dpkg-dev dselect dvd+rw-tools e2fslibs e2fsprogs eject
  eog evms evms-ncurses evolution evolution-data-server evolution-plugins
  evolution-webcal fastjar file file-roller findutils firefox
  firefox-gnome-support flashplugin-nonfree fontconfig foo2zjs foomatic-db
  foomatic-db-engine foomatic-db-hpijs foomatic-filters
  foomatic-filters-ppds freeglut3 g++ g++-4.0 gaim gaim-data gamin
  gcalctool gcc gcc-3.3-base gcc-4.0 gcc-4.0-base gcj-4.1-base gconf-editor
  gdb gdebi gedit gedit-common gettext gettext-base gftp gftp-common
  gftp-gtk gftp-text gij-4.1 gksu gnome-about gnome-applets
  gnome-applets-data gnome-btdownload gnome-control-center
  gnome-desktop-data gnome-games gnome-games-data gnome-icon-theme
  gnome-menus gnome-nettool gnome-power-manager gnome-session
  gnome-system-tools gnome-terminal gnome-terminal-data gnome-utils
  gnome-volume-manager gnopernicus gnupg gok grep groff-base grub
  gsfonts-x11 gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-ffmpeg
  gstreamer0.10-gnomevfs gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good
  gstreamer0.10-plugins-ugly gstreamer0.10-tools gstreamer0.10-x
  gtk2-engines-pixbuf gucharmap guile-1.6-libs gzip hal hal-device-manager
  hdparm hostname hwdata info initramfs-tools initscripts intltool-debian
  iproute irssi java-common java-gcj-compat klibc-utils klogd
  laptop-mode-tools less lftp liba52-0.7.4 libacl1 libao2
  libapache2-mod-php4 libapm1 libartsc0 libasound2 libaspell15 libatk1.0-0
  libatspi1.0-0 libattr1 libaudio2 libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-glib1 libavc1394-0 libbeagle0 libblkid1
  libbluetooth1 libbonobo2-0 libbonobo2-common libbonoboui2-0
  libbonoboui2-common libbrlapi1 libbz2-1.0 libcairo2 libcamel1.2-8
  libcdparanoia0 libcomerr2 libcompfaceg1 libconsole
  libcrypt-passwdmd5-perl libcupsimage2 libcupsys2 libcurl3 libcurl3-gnutls
  libdbd-mysql-perl libdbi-perl libdbus-1-2 libdbus-glib-1-2
  libdevmapper1.02 libdiscover1 libdjvulibre15 libdmx1 libdrm2 libdv4
  libdvbpsi4 libdvdread3 libebook1.2-5 libecal1.2-3 libedata-book1.2-2
  libedata-cal1.2-1 libedataserver1.2-7 libedataserverui1.2-6 libeel2-2
  libeel2-data libegroupwise1.2-9 libelfg0 libestools1.2 libevms-2.5
  libexchange-storage1.2-1 libexif12 libexpat1 libflac7 libfontconfig1
  libfontenc1 libfreetype6 libfribidi0 libfs6 libgail-common
  libgail-gnome-module libgail17 libgamin0 libgcc1 libgcj-common libgcj7
  libgcj7-jar libgd2-noxpm libgda2-3 libgda2-common libgdbm3 libgdl-1-0
  libgdl-1-common libgeoip1 libggi2 libgii0 libgii0-target-x
  libgl1-mesa-dri libglew1 libglib-perl libglibmm-2.4-1c2a libglu1-mesa
  libgnome-desktop-2 libgnome-menu2 libgnome2-0 libgnome2-canvas-perl
  libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomecanvas2-0
  libgnomecanvas2-common libgnomecups1.0-1 libgnomeprint2.2-0
  libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common
  libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin
  libgnomevfs2-common libgnomevfs2-extra libgnucrypto-java libgnutls12
  libgpg-error0 libgphoto2-2 libgphoto2-port0 libgpmg1 libgpod0
  libgsf-1-common libgstreamer-plugins-base0.10-0 libgstreamer0.10-0
  libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkmm-2.4-1c2a
  libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgucharmap4
  libguile-ltdl-1 libhal-storage1 libhal1 libhsqldb-java libidl0 libidn11
  libiw28 libjessie-java libjline-java libjpeg62 libklibc libkpathsea4
  libkrb53 liblcms1 libldap2 liblircclient0 libltdl3 libmagic1 libmagick9
  libmdbtools libmetacity0 libmms0 libmng1 libmusicbrainz4c2a
  libmysqlclient15off libnautilus-extension1 libncurses5 libncursesw5
  libnet-daemon-perl libnet-ssleay-perl libnetcdf3 libnm-util0 libnotify1
  libogg0 liboggflac3 liboil0.3 libopal-2.2.0 liborbit2 libpam-modules
  libpam-runtime libpam0g libpango1.0-0 libpango1.0-common libpaper1
  libparted1.6-13 libpcap0.8 libpcre3 libperl5.8 libpisock8 libpisync0
  libplrpc-perl libpng12-0 libpopt0 libpq4 libpt-1.10.0 libpt-plugins-alsa
  libpt-plugins-v4l libpt-plugins-v4l2 libqt3-mt libqthreads-12 libraptor1
  librasqal0 librdf0 libsane libsasl2 libsasl2-modules libscim8c2a
  libsdl1.2debian libsdl1.2debian-alsa libselinux1 libsepol1
  libservlet2.3-java libshout3 libslang2 libsndfile1 libsnmp-base libsnmp9
  libsoup2.2-8 libspeex1 libsqlite3-0 libss2 libssl0.9.8 libstdc++5
  libstdc++6 libstdc++6-4.0-dev libswfdec0.3 libsysfs2 libtag1c2a libtagc0
  libtasn1-2 libtheora0 libtiff4 libungif4g libuniconf4.2 libusb-0.1-4
  libuuid1 libvorbis0a libvorbisenc2 libvorbisfile3 libwnck-common
  libwnck18 libwpd8c2a libwrap0 libwvstreams4.2-base libwvstreams4.2-extras
  libwxgtk2.6-0 libx11-6 libxalan2-java libxau6 libxcursor1 libxdamage1
  libxdmcp6 libxerces2-java libxfixes3 libxfont1 libxft2 libxkbfile1
  libxklavier10 libxml2 libxml2-utils libxmlsec1 libxmlsec1-nss
  libxmlsec1-openssl libxosd2 libxp6 libxpm4 libxrandr2 libxrender1
  libxres1 libxslt1.1 libxss1 libxt-java libxt6 libxxf86dga1 libxxf86misc1
  libxxf86vm1 libzzip-0-12 linux-kernel-headers linux-sound-base login
  logrotate lsb-base lsb-release lsof ltrace lvm2 make makedev manpages
  mdadm menu-xdg mesa-utils metacity mime-support mkisofs module-init-tools
  mount mozilla-mplayer mtr-tiny mysql-admin mysql-admin-common
  mysql-client mysql-client-5.0 mysql-common mysql-server mysql-server-5.0
  nano nautilus nautilus-data nautilus-sendto ncurses-base ncurses-bin
  net-tools netbase netcat network-manager network-manager-gnome
  notification-daemon odbcinst1debian1 openssh-client openssl parted passwd
  patch pciutils pcmcia-cs pcmciautils perl perl-base perl-modules
  php4-common php4-mysql php5-cgi php5-common phpbb2 phpbb2-conf-mysql
  phpbb2-languages po-debconf popularity-contest powermgmt-base pppconfig
  pppoeconf procmail procps psmisc python-adns python-apt python-cddb
  python-epydoc python-gdbm python-gmenu python-gnupginterface
  python-htmltmpl python-jabber python-ldap python-libxml2 python-mysqldb
  python-netcdf python-newt python-numeric python-pam python-pexpect
  python-pgsql python-pisock python-pylibacl python-pyopenssl
  python-pyxattr python-reportlab python-simpletal python-syck python-tk
  python-unit python-xml python-xmpp python2.4 python2.4-adns python2.4-apt
  python2.4-dbus python2.4-examples python2.4-htmltmpl python2.4-jabber
  python2.4-ldap python2.4-librdf python2.4-libxml2 python2.4-libxslt1
  python2.4-minimal python2.4-mysqldb python2.4-numeric python2.4-pam
  python2.4-pexpect python2.4-pgsql python2.4-pycurl python2.4-pylibacl
  python2.4-pyopenssl python2.4-pyxattr python2.4-reportlab
  python2.4-simpletal python2.4-xml python2.4-xmpp rar rcconf reiserfsprogs
  reportbug rhythmbox rss-glx rsync scim scim-gtk2-immodule
  scim-modules-socket sed shared-mime-info slocate ssh-askpass-gnome strace
  streamripper sudo synaptic sysklogd system-tools-backends sysv-rc
  sysvinit tar tcl8.4 tcpd tcpdump tk8.4 ttf-arabeyes ttf-arphic-ukai
  ttf-bitstream-vera ttf-dejavu ttf-gentium ttf-kochi-gothic
  ttf-kochi-mincho ttf-thai-tlwg ucf unixodbc unrar unzip update-manager
  update-notifier util-linux vim vim-common vim-runtime vino vnc-common
  vncserver vorbis-tools webalizer whiptail whois wireless-tools
  wpasupplicant wvdial wwwconfig-common x-ttcidfont-conf
  x-window-system-core x11-common xbase-clients xcursor-themes
  xfonts-100dpi xfonts-75dpi xfonts-base xfonts-scalable xfonts-utils
  xfsprogs xml-core xmms xpmutils xresprobe xsane xsane-common
  xscreensaver-gl xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-elographics xserver-xorg-input-kbd
  xserver-xorg-input-mouse xserver-xorg-input-synaptics xsltproc xterm
  xutils xvncviewer yelp zenity zlib1g
The following NEW packages will be installed:
  tzdata
The following packages will be upgraded:
  libc6-i686
1 packages upgraded, 1 newly installed, 0 to remove and 651 not upgraded.
Need to get 0B/1439kB of archives. After unpacking 6005kB will be used.
Do you want to continue? [Y/n/?] y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  libc6-i686 tzdata

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes
Writing extended state information... Done
(Reading database ... 113377 files and directories currently installed.)
Unpacking tzdata (from .../tzdata_2006g-2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/tzdata_2006g-2_all.deb (--unpack):
 trying to overwrite `/usr/share/zoneinfo/Africa/Algiers', which is also in package locales
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/tzdata_2006g-2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libc6:
 libc6 depends on tzdata; however:
  Package tzdata is not installed.
dpkg: error processing libc6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.3.6-13); however:
  Package libc6 is not configured yet.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6
 libc6-dev
john@ubuntu-box:~$


---

### Post by Ramses de Norre on 2006-06-23
sudo aptitude purge **package_name** ;) but I don't think it'll work.. I'm not sure what to do, I'll think about it.

---

### Post by Scorpuk on 2006-06-23
woops. I tried to rebuild the madwifi-tools and now get this:

> 
root@ubuntu-box:/home/john/madwifi# apt-get build-dep madwifi-tools
Reading package lists... Done
Building dependency tree... Done
E: Build-dependencies for madwifi-tools could not be satisfied.
root@ubuntu-box:/home/john/madwifi# ls
root@ubuntu-box:/home/john/madwifi# gedit /etc/apt/sources.list

(gedit:7766): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
root@ubuntu-box:/home/john/madwifi# apt-get update
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release [30.9kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Get: 5 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages [4571B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources [1478B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Sources
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages [37.7kB]
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Get: 9 [http://ftp.au.debian.org](http://ftp.au.debian.org) unstable Release.gpg [189B]
Get: 10 [http://ftp.au.debian.org](http://ftp.au.debian.org) testing Release.gpg [189B]
Get: 11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get: 12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources [22.1kB]
Get: 13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Get: 14 [http://ftp.au.debian.org](http://ftp.au.debian.org) unstable Release [38.3kB]
Ign [http://ftp.au.debian.org](http://ftp.au.debian.org) unstable Release
Get: 15 [http://ftp.au.debian.org](http://ftp.au.debian.org) testing Release [35.4kB]
Ign [http://ftp.au.debian.org](http://ftp.au.debian.org) testing Release
Get: 16 [http://ftp.au.debian.org](http://ftp.au.debian.org) unstable/main Packages [3168kB]
Get: 17 [http://ftp.au.debian.org](http://ftp.au.debian.org) unstable/contrib Packages [48.8kB]
Get: 18 [http://ftp.au.debian.org](http://ftp.au.debian.org) unstable/non-free Packages [65.8kB]
Get: 19 [http://ftp.au.debian.org](http://ftp.au.debian.org) unstable/main Sources [1198kB]
Get: 20 [http://ftp.au.debian.org](http://ftp.au.debian.org) unstable/contrib Sources [21.5kB]
Get: 21 [http://ftp.au.debian.org](http://ftp.au.debian.org) unstable/non-free Sources [27.1kB]
Get: 22 [http://ftp.au.debian.org](http://ftp.au.debian.org) testing/main Packages [3018kB]
Get: 23 [http://ftp.au.debian.org](http://ftp.au.debian.org) testing/contrib Packages [40.3kB]
Hit [http://ftp.au.debian.org](http://ftp.au.debian.org) testing/non-free Packages
Get: 24 [http://ftp.au.debian.org](http://ftp.au.debian.org) testing/main Sources [1144kB]
Get: 25 [http://ftp.au.debian.org](http://ftp.au.debian.org) testing/contrib Sources [17.6kB]
Hit [http://ftp.au.debian.org](http://ftp.au.debian.org) testing/non-free Sources
Fetched 8921kB in 4m6s (36.2kB/s)
Reading package lists... Error!
W: GPG error: [http://ftp.au.debian.org](http://ftp.au.debian.org) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 010908312D230C5F
W: GPG error: [http://ftp.au.debian.org](http://ftp.au.debian.org) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 010908312D230C5F
E: Dynamic MMap ran out of room
E: Error occurred while processing kbabel (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ftp.au.debian.org_debian_dists_testing_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
root@ubuntu-box:/home/john/madwifi# apt-get update -f
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release [30.9kB]
Get: 6 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Get: 7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [25.1kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages [4571B]
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Get: 9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources [1478B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Sources
Get: 10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages [37.7kB]
Get: 11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4253B]
Get: 12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [6227B]
Get: 13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [974B]
Get: 14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get: 15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources [22.1kB]
Get: 16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Get: 17 [http://ftp.au.debian.org](http://ftp.au.debian.org) unstable Release.gpg [189B]
Get: 18 [http://ftp.au.debian.org](http://ftp.au.debian.org) testing Release.gpg [189B]
Hit [http://ftp.au.debian.org](http://ftp.au.debian.org) unstable Release
Hit [http://ftp.au.debian.org](http://ftp.au.debian.org) testing Release
Get: 19 [http://ftp.au.debian.org](http://ftp.au.debian.org) unstable Release [38.3kB]
Ign [http://ftp.au.debian.org](http://ftp.au.debian.org) unstable Release
Get: 20 [http://ftp.au.debian.org](http://ftp.au.debian.org) testing Release [35.4kB]
Ign [http://ftp.au.debian.org](http://ftp.au.debian.org) testing Release
Hit [http://ftp.au.debian.org](http://ftp.au.debian.org) unstable/main Packages
Hit [http://ftp.au.debian.org](http://ftp.au.debian.org) unstable/contrib Packages
Hit [http://ftp.au.debian.org](http://ftp.au.debian.org) unstable/non-free Packages
Hit [http://ftp.au.debian.org](http://ftp.au.debian.org) unstable/main Sources
Hit [http://ftp.au.debian.org](http://ftp.au.debian.org) unstable/contrib Sources
Hit [http://ftp.au.debian.org](http://ftp.au.debian.org) unstable/non-free Sources
Hit [http://ftp.au.debian.org](http://ftp.au.debian.org) testing/main Packages
Hit [http://ftp.au.debian.org](http://ftp.au.debian.org) testing/contrib Packages
Hit [http://ftp.au.debian.org](http://ftp.au.debian.org) testing/non-free Packages
Hit [http://ftp.au.debian.org](http://ftp.au.debian.org) testing/main Sources
Hit [http://ftp.au.debian.org](http://ftp.au.debian.org) testing/contrib Sources
Hit [http://ftp.au.debian.org](http://ftp.au.debian.org) testing/non-free Sources
Fetched 239kB in 21s (11.4kB/s)
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing kbabel (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ftp.au.debian.org_debian_dists_testing_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


and then tried the purge again, doh!

> 
john@ubuntu-box:~$ sudo aptitude purge
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing kbabel (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ftp.au.debian.org_debian_dists_testing_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing kbabel (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ftp.au.debian.org_debian_dists_testing_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
john@ubuntu-box:~$


hmmm reinstall perhaps - bummer if I have to as I got phpBB2 runnin and not sure if I can resurrect it afterwards...

---

### Post by Ramses de Norre on 2006-06-23
As I said, you should give a package name after the purge option. 
And I see you are using ubuntu and debian testing repos together, that's asking for trouble..

---

### Post by tacubuntuforums on 2007-02-19
Hello:
I posted asking help for a similar problem.

[http://ubuntuforums.org/showpost.php?p=2181756&postcount=5](http://ubuntuforums.org/showpost.php?p=2181756&postcount=5)

It makes me wander:

How does one  solve broken packages?
Is there a way to solve them always?


Any ideas for my particular problem or for the general question?

---

