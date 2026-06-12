---
title: "I removed all meta-packes, how will apt-get dist-upgrade react?"
date: 2005-09-12
forum: Desktop Environments
---

### Post by Alex_Perry on 2005-09-12
I don't know if this belongs under the Kubuntu or Breezy forum, so if I posted in the wrong place, feel free to move my post mods.

I have Kubuntu Hoary 5.04 with all the latest updates (KDE, kernel) and do not have any of the meta-packages installed like kubuntu-desktop, etc... I have removes pretty much everything that I don't need to conserve space. When I do 'apt-get dist-upgrade' to update to Breezy when it comes out, what is going to happen? I know it will update all my currently installed packages, but are there any specific updates that have been done to Breezy that I will run into a problem with because of the missing meta-packages?

I'm hoping for an answer that doesn't involve re-installing the missing meta-packages, since that's all I could find in the search.

---

### Post by macgyver2 on 2005-09-12
[QUOTE=Alex_Perry]I'm hoping for an answer that doesn't involve re-installing the missing meta-packages, since that's all I could find in the search.[/QUOTE]
Hmm, sorry...but you really need to have those meta-packages in if you want the dist-upgrade to go smoothly.  Otherwise it might be (good chance, I think) that you end up with some mutant half-Hoary/half-Breezy system that will cause problems.

---

### Post by Alex_Perry on 2005-09-13
Damn. Just to give you an idea of what I've removed, take a look ('inst' is just an alias for 'sudo apt-get install');

```

alex@smokebox:~$ inst kubuntu-desktop
Ign http://wine.sourceforge.net binary/ Release.gpg
Get:1 http://security.ubuntu.com hoary-security Release.gpg [189B]
Ign http://kubuntu.org hoary-updates Release.gpg
Get:2 http://us.archive.ubuntu.com hoary Release.gpg [189B]
Get:3 http://us.archive.ubuntu.com hoary-updates Release.gpg [189B]
Ign http://debian.neo.pl unstable Release.gpg
Get:4 http://archive.ubuntu.com hoary Release.gpg [189B]
Hit http://security.ubuntu.com hoary-security Release
Hit http://wine.sourceforge.net binary/ Release
Ign http://kubuntu.org hoary-updates Release
Hit http://us.archive.ubuntu.com hoary Release
Hit http://debian.neo.pl unstable Release
Hit http://archive.ubuntu.com hoary Release
Ign http://kubuntu.org hoary-updates/main Packages
Hit http://us.archive.ubuntu.com hoary-updates Release
Ign http://wine.sourceforge.net binary/ Packages
Ign http://debian.neo.pl unstable/main Packages
Hit http://security.ubuntu.com hoary-security/main Packages
Hit http://kubuntu.org hoary-updates/main Packages
Ign http://debian.neo.pl unstable/contrib Packages
Ign http://debian.neo.pl unstable/non-free Packages
Hit http://wine.sourceforge.net binary/ Packages
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Hit http://us.archive.ubuntu.com hoary/universe Packages
Hit http://archive.ubuntu.com hoary/multiverse Packages
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://debian.neo.pl unstable/main Packages
Hit http://debian.neo.pl unstable/contrib Packages
Hit http://debian.neo.pl unstable/non-free Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release
Ign http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Fetched 4B in 5s (1B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  akode bicyclerepair blt bogofilter dc dcoprss dictionaries-common dirmngr
  diveintopython doc-base dvd+rw-tools fetchmail foomatic-db-gimp-print
  fortune-mod fortunes-min freeglut3 gnupg2 gpgsm ijsgimpprint imlib1
  irssi-text juk kaboodle kandy kaudiocreator kcoloredit kdegraphics kdelirc
  kdemultimedia kdenetwork kdepim kdepim-kfile-plugins kdessh kdeutils kdict
  kdvi kfax kget khexedit kiconedit kitchensync kleopatra kmid knewsticker
  kolourpaint konserve konversation kooka korn kpilot kpovmodeler kppp krec
  kregexpeditor kruler ksirc ksync ktimer kuickshow kwifimanager libadns1
  libao2 libarts1-audiofile libarts1-mpeglib libcurl3 libdb4.2++ libdb4.3
  libgd1-noxpm libgd2-noxpm libgdchart-gd1-noxpm libgeoip1 libglut3 libgsl0
  libieee1284-3 libijs-0.35 libiw27 libkgantt0 libksba8 libkscan1 libmal1
  libmusicbrainz2 libmyspell3 libmysqlclient10 libneon23 libnewt0.51
  libparted1.6-12 libpisock8 libpng10-0 libpq3 libraptor1 librasqal0 librdf0
  librecode0 librss1 libsane libsqlite0 libstartup-notification0
  libstlport4.6 libwvstreams3-base libxaw7 libxosd2 mpeglib netcdfg3
  networkstatus noatun openoffice.org openoffice.org-bin
  openoffice.org-debian-files openoffice.org-kde openoffice.org-l10n-en
  openssh-client openssh-server pnm2ppa powernowd ppp procmail python-adns
  python-apt python-cddb python-clientcookie python-crypto
  python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools
  python-egenix-mxtools python-epydoc python-eunuchs python-examples
  python-gadfly python-gd python-gdbm python-gdchart python-genetic
  python-geoip python-gnupginterface python-gst python-htmlgen
  python-htmltmpl python-id3lib python-imaging python-imaging-sane
  python-jabber python-kjbuckets python-ldap python-musicbrainz
  python-mysqldb python-netcdf python-newt python-numarray python-numeric
  python-opengl python-osd python-pam python-parted python-pexpect
  python-pgsql python-pisock python-pqueue python-pyao python-pylibacl
  python-pyogg python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr
  python-reportlab python-simpletal python-soappy python-sqlite python-stats
  python-syck python-tk python-twisted python-unit python-xdg python-xml
  python-xmpp python2.4-adns python2.4-clientcookie python2.4-crypto
  python2.4-dbus python2.4-dictclient python2.4-egenix-mxdatetime
  python2.4-egenix-mxproxy python2.4-egenix-mxstack
  python2.4-egenix-mxtexttools python2.4-egenix-mxtools python2.4-eunuchs
  python2.4-examples python2.4-gadfly python2.4-gd python2.4-gdbm
  python2.4-geoip python2.4-htmlgen python2.4-htmltmpl python2.4-id3lib
  python2.4-imaging python2.4-imaging-sane python2.4-jabber
  python2.4-kjbuckets python2.4-ldap python2.4-librdf python2.4-libxml2
  python2.4-libxslt1 python2.4-musicbrainz python2.4-mysqldb
  python2.4-numarray python2.4-numeric python2.4-opengl python2.4-osd
  python2.4-pam python2.4-pexpect python2.4-pgsql python2.4-pycurl
  python2.4-pylibacl python2.4-pyopenssl python2.4-pyorbit python2.4-pyxattr
  python2.4-reportlab python2.4-samba python2.4-simpletal python2.4-sqlite
  python2.4-syck python2.4-tk python2.4-twisted python2.4-twisted-bin
  python2.4-unit python2.4-xml python2.4-xmpp sane-utils screen smbclient ssh
  ttf-arabeyes ttf-arphic-bkai00mp ttf-arphic-bsmi00lp ttf-arphic-gbsn00lp
  ttf-arphic-gkai00mp ttf-baekmuk ttf-indic-fonts ttf-kochi-gothic
  ttf-kochi-mincho ttf-malayalam-fonts wvdial x-window-system-core
  xlibmesa-dri xorg-driver-synaptics xterm
Suggested packages:
  vim-python idle blt-demo ispell emacsen-common jed-extra dhelp dwww
  fetchmailconf exim4 mail-transport-agent resolvconf gnupg-doc xloadimage
  imlib-progs irssi-scripts kdegraphics-doc-html kdemultimedia-doc-html
  kdenetwork-doc-html kdepim-doc-html kdeutils-doc-html knewsticker-scripts
  libsoap-lite-perl povray libcurl3-gssapi libgd-tools geoip-bin
  gsl-ref-psdoc gsl-doc-pdf parted nparted libparted1.6-dev libparted1.6-i18n
  jpilot pilot-link malsync gnome-pilot evolution postgresql-doc
  postgresql-client libsane-extras xfonts-base-transcoded netcdf-doc
  noatun-plugins myspell-dictionary openoffice.org-help menu ooqstart-gnome
  oooqs-kde unixodbc openoffice.org-hyphenation openoffice.org-thesaurus
  openoffice.org-mimelnk openoffice.org-gtk-gnome openoffice.org-gnomevfs
  openclipart myspell-dictionary-en openoffice.org-hyphenation-en
  openoffice.org-thesaurus-en openoffice.org-help-en ssh-askpass magicfilter
  apsfilter libatm1 epydoc-doc python-imaging-doc python-egenix-mxdatetime
  python-numarray-doc python-numeric-tutorial python-reportlab-doc
  python-gtk2 python-glade2 python-glade-1.2 python-qt3 libwxgtk2.4-python
  python-profiler dictd python-ldap-doc mysql-server libcurl3-dev
  pyopenssl-doc tix8.1 python2.4-gtk2 python2.4-glade2 python2.4-qt3
  twisted-doc python2.4-twisted-conch python2.4-profiler smbfs
  tfm-arphic-bkai00mp tfm-arphic-bsmi00lp tfm-arphic-gbsn00lp
  tfm-arphic-gkai00mp libglide3 xfonts-cyrillic
Recommended packages:
  db4.3-util ca-certificates vorbis-tools ktalkd lisa tetex-bin ruby gocr
  libio-socket-ssl-perl libadns1-bin libreiserfs0.3-0 raptor-utils
  tetex-extra python-serial ttf-tamil-fonts ttf-bangla-fonts
The following NEW packages will be installed:
  akode bicyclerepair blt bogofilter dc dcoprss dictionaries-common dirmngr
  diveintopython doc-base dvd+rw-tools fetchmail foomatic-db-gimp-print
  fortune-mod fortunes-min freeglut3 gnupg2 gpgsm ijsgimpprint imlib1
  irssi-text juk kaboodle kandy kaudiocreator kcoloredit kdegraphics kdelirc
  kdemultimedia kdenetwork kdepim kdepim-kfile-plugins kdessh kdeutils kdict
  kdvi kfax kget khexedit kiconedit kitchensync kleopatra kmid knewsticker
  kolourpaint konserve konversation kooka korn kpilot kpovmodeler kppp krec
  kregexpeditor kruler ksirc ksync ktimer kubuntu-desktop kuickshow
  kwifimanager libadns1 libao2 libarts1-audiofile libarts1-mpeglib libcurl3
  libdb4.2++ libdb4.3 libgd1-noxpm libgd2-noxpm libgdchart-gd1-noxpm
  libgeoip1 libglut3 libgsl0 libieee1284-3 libijs-0.35 libiw27 libkgantt0
  libksba8 libkscan1 libmal1 libmusicbrainz2 libmyspell3 libmysqlclient10
  libneon23 libnewt0.51 libparted1.6-12 libpisock8 libpng10-0 libpq3
  libraptor1 librasqal0 librdf0 librecode0 librss1 libsane libsqlite0
  libstartup-notification0 libstlport4.6 libwvstreams3-base libxaw7 libxosd2
  mpeglib netcdfg3 networkstatus noatun openoffice.org openoffice.org-bin
  openoffice.org-debian-files openoffice.org-kde openoffice.org-l10n-en
  openssh-client openssh-server pnm2ppa powernowd ppp procmail python-adns
  python-apt python-cddb python-clientcookie python-crypto
  python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools
  python-egenix-mxtools python-epydoc python-eunuchs python-examples
  python-gadfly python-gd python-gdbm python-gdchart python-genetic
  python-geoip python-gnupginterface python-gst python-htmlgen
  python-htmltmpl python-id3lib python-imaging python-imaging-sane
  python-jabber python-kjbuckets python-ldap python-musicbrainz
  python-mysqldb python-netcdf python-newt python-numarray python-numeric
  python-opengl python-osd python-pam python-parted python-pexpect
  python-pgsql python-pisock python-pqueue python-pyao python-pylibacl
  python-pyogg python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr
  python-reportlab python-simpletal python-soappy python-sqlite python-stats
  python-syck python-tk python-twisted python-unit python-xdg python-xml
  python-xmpp python2.4-adns python2.4-clientcookie python2.4-crypto
  python2.4-dbus python2.4-dictclient python2.4-egenix-mxdatetime
  python2.4-egenix-mxproxy python2.4-egenix-mxstack
  python2.4-egenix-mxtexttools python2.4-egenix-mxtools python2.4-eunuchs
  python2.4-examples python2.4-gadfly python2.4-gd python2.4-gdbm
  python2.4-geoip python2.4-htmlgen python2.4-htmltmpl python2.4-id3lib
  python2.4-imaging python2.4-imaging-sane python2.4-jabber
  python2.4-kjbuckets python2.4-ldap python2.4-librdf python2.4-libxml2
  python2.4-libxslt1 python2.4-musicbrainz python2.4-mysqldb
  python2.4-numarray python2.4-numeric python2.4-opengl python2.4-osd
  python2.4-pam python2.4-pexpect python2.4-pgsql python2.4-pycurl
  python2.4-pylibacl python2.4-pyopenssl python2.4-pyorbit python2.4-pyxattr
  python2.4-reportlab python2.4-samba python2.4-simpletal python2.4-sqlite
  python2.4-syck python2.4-tk python2.4-twisted python2.4-twisted-bin
  python2.4-unit python2.4-xml python2.4-xmpp sane-utils screen smbclient ssh
  ttf-arabeyes ttf-arphic-bkai00mp ttf-arphic-bsmi00lp ttf-arphic-gbsn00lp
  ttf-arphic-gkai00mp ttf-baekmuk ttf-indic-fonts ttf-kochi-gothic
  ttf-kochi-mincho ttf-malayalam-fonts wvdial x-window-system-core
  xlibmesa-dri xorg-driver-synaptics xterm
0 upgraded, 249 newly installed, 0 to remove and 50 not upgraded.
Need to get 157MB of archives.
After unpacking 467MB of additional disk space will be used.
Do you want to continue [Y/n]? n

```

What would happen if I just replace my hoary repository source with breezy's and do 'sudo apt-get update; sudo apt-get upgrade' once breezy comes out? Shouldn't all the dependancies figure themselves out? Most major changes should occur in packages installed (ie kdebase, xorg) and just update to the newer package version, right? 

Anyone on Breezy's development know if there is there any *new* major packages in Breezy that wont get installed by just doing this method and effect how the system runs?

---

