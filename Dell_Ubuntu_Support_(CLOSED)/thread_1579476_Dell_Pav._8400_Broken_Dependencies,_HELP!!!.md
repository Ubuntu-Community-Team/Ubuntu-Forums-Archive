---
title: "Dell Pav. 8400: Broken Dependencies, HELP!!!"
date: 2010-09-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dturne25 on 2010-09-21
I don't know what to do. I hope it's not the bios.  Can someone please help me fix this? This is what I tried and what it looks like.root@chrystal-desktop:/home/chrystal# sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python-crypto python-twisted-core java-common liblog4j1.2-java libfftw3-3
  icedtea-6-jre-cacao python-serial python-pam python-openssl
  openjdk-6-jre-headless tzdata-java python-twisted-conch python-pyopenssl
  openjdk-6-jre-lib libgtk1.2-common gocr tzdata default-jre-headless jackd
  ca-certificates-java python-twisted-bin
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  acl adduser aspell aspell-en binfmt-support busybox-initramfs
  ca-certificates ca-certificates-java conkeror conkeror-spawn-process-helper
  console-setup console-terminus consolekit coreutils cpio cpp cpp-4.3 dbus
  dbus-x11 debconf-i18n debianutils default-jre-headless defoma
  dictionaries-common dmsetup dpkg dvdauthor eject esound-clients espeak
  espeak-data file findutils fontconfig fontconfig-config gamin gawk
  gcc-4.3-base gconf2 gconf2-common geda-doc geda-gnetlist geda-symbols
  genisoimage gimp-data gnome-icon-theme gnome-keyring gnome-mime-data
  gnome-mount gnupg gpgv gsfonts gstreamer0.10-gnonlin
  gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-x
  guile-1.8-libs gvfs gvfs-backends hal hal-info hdparm hicolor-icon-theme
  hunspell-en-us icedtea-6-jre-cacao ifupdown imagemagick imagemagick-doc
  initramfs-tools kbd klibc-utils libaa1 libacl1 libarchive1 libasound2
  libaspell15 libatk1.0-0 libatk1.0-data libattr1 libaudio2 libaudiofile0
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-glib1
  libavc1394-0 libbabl-0.0-0 libbluetooth3 libbonobo2-0 libbonobo2-common
  libbonoboui2-common libburn4 libbz2-1.0 libc6 libcaca0 libcairo2 libcap2
  libcdio-cdda0 libcdio-paranoia0 libcdio7 libcdparanoia0 libcelt0
  libck-connector0 libcomerr2 libcroco3 libcryptui0 libcups2 libcurl3-gnutls
  libdatrie0 libdb4.6 libdb4.7 libdbus-1-3 libdbus-glib-1-2 libdevmapper1.02.1
  libdirectfb-1.0-0 libdjvulibre-text libdjvulibre21 libdrm-intel1 libdrm2
  libdv4 libdvdnav4 libdvdread4 libenca0 libenchant1c2a libesd-alsa0
  libespeak1 libexif12 libexpat1 libfaac0 libffi5 libflac8 libfontconfig1
  libfontenc1 libfreebob0 libfreetype6 libfribidi0 libgail-common libgail18
  libgamin0 libgcc1 libgconf2-4 libgcr0 libgcrypt11 libgd2-noxpm libgdbm3
  libgeda-common libgeda33 libgegl-0.0-0 libggi-target-x libggi2 libgif4
  libgii1 libgii1-target-x libgimp2.0 libgl1-mesa-glx libglade2-0 libglib2.0-0
  libglib2.0-data libglibmm-2.4-1c2a libglu1-mesa libgmp3c2 libgnome-keyring0
  libgnome2-0 libgnome2-common libgnomecanvas2-0 libgnomecanvas2-common
  libgnomekbd-common libgnomeui-0 libgnomeui-common libgnomevfs2-0
  libgnomevfs2-common libgnomevfs2-extra libgnutls26 libgomp1
  libgoocanvas-common libgoocanvas3 libgp11-0 libgpg-error0 libgpgme11
  libgphoto2-2 libgphoto2-port0 libgpm2 libgpod4-nogtk libgraphviz4
  libgsf-1-114 libgsf-1-common libgstreamer-plugins-base0.10-0
  libgstreamer0.10-0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libgtksourceview2.0-0 libgtksourceview2.0-common libgvfscommon0
  libhal-storage1 libhal1 libhunspell-1.2-0 libice6 libidl0 libidn11
  libiec61883-0 libieee1284-3 libilmbase6 libiso9660-5 libisofs6 libjack0
  libjasper1 libjpeg62 libkeyutils1 libklibc libkrb53 liblcms1 libldap-2.4-2
  liblircclient0 liblocale-gettext-perl libltdl7 liblzo2-2 libmad0 libmagic1
  libmagickwand1 libmng1 libmono-corlib2.0-cil libmono-data-tds2.0-cil
  libmono-i18n2.0-cil libmono-security2.0-cil libmono-system-data2.0-cil
  libmono-system2.0-cil libmono0 libmp3lame0 libmpcdec3 libnautilus-extension1
  libncurses5 libncursesw5 libnewt0.52 libnotify1 libnspr4-0d libnss3-1d
  libogg0 liboil0.3 libopenal1 libopenexr6 libopenobex1 liborbit2
  libpam-ck-connector libpam-gnome-keyring libpam-modules libpam-runtime
  libpam0g libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpci3
  libpciaccess0 libpcre3 libpixman-1-0 libpng12-0 libpolkit-dbus2
  libpolkit-gnome0 libpolkit-grant2 libpolkit2 libpoppler-glib4 libpoppler4
  libpopt0 libportaudio2 libproxy0 libpulse-browse0 libpulse0 libraw1394-8
  libreadline5 librsvg2-2 librsvg2-common libsamplerate0 libsane libsasl2-2
  libsasl2-modules libsdl1.2debian libsdl1.2debian-alsa libselinux1 libsepol1
  libsexy2 libsgutils1 libshout3 libsigc++-2.0-0c2a libslang2 libsm6
  libsmbclient libsmbios2 libsndfile1 libsoup-gnome2.4-1 libsoup2.4-1
  libspeex1 libsqlite3-0 libssl0.9.8 libstartup-notification0 libstdc++6
  libstroke0 libsvga1 libsysfs2 libtag1c2a libtalloc1 libtasn1-3
  libtext-charwidth-perl libtext-iconv-perl libthai-data libthai0 libtheora0
  libtiff4 libts-0.0-0 libtwolame0 libusb-0.1-4 libuuid1 libv4l-0 libvcdinfo0
  libvisual-0.4-0 libvisual-0.4-plugins libvolume-id1 libvorbis0a
  libvorbisenc2 libwavpack1 libwbclient0 libwmf0.2-7 libwnck-common libwnck22
  libwrap0 libx11-6 libx11-data libx264-65 libx86-1 libxau6 libxaw7
  libxcb-render-util0 libxcb-render0 libxcb1 libxcomposite1 libxcursor1
  libxdamage1 libxext6 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1
  libxkbfile1 libxklavier12 libxml++2.6-2 libxml2 libxmu6 libxpm4 libxrandr2
  libxrender1 libxres1 libxt6 libxv1 libxvidcore4 libxvmc1 libxxf86dga1
  libxxf86vm1 lsb-base lzma mencoder mime-support module-init-tools
  mono-2.0-runtime mono-common mono-gac mono-jit mount mplayer mplayer-skins
  ncurses-bin net-tools netbase notification-daemon obex-data-server
  openjdk-6-jre-headless openjdk-6-jre-lib openssl passwd pciutils perl
  perl-base perl-modules pm-utils policykit policykit-gnome powermgmt-base
  procps psmisc pulseaudio-utils python python-cairo python-central
  python-crypto python-dbus python-gconf python-glade2 python-gnomecanvas
  python-gobject python-gst0.10 python-gtk2 python-libxml2 python-minimal
  python-openssl python-pam python-pygoocanvas python-pyopenssl python-pyorbit
  python-serial python-setuptools python-support python-twisted-bin
  python-twisted-core python-zopeinterface python2.6 python2.6-minimal
  radeontool readline-common sed sg3-utils sgml-base smartdimmer
  ttf-bitstream-vera ttf-dejavu ttf-dejavu-core ttf-dejavu-extra tzdata
  tzdata-java ucf udev update-inetd usbutils uuid-runtime vbetool vcdimager
  whiptail x-ttcidfont-conf x11-common x11-xkb-utils xfonts-encodings
  xfonts-utils xkb-data xml-core xulrunner-1.9.2 zlib1g
Suggested packages:
  ecryptfs-utils aspell-doc spellutils emacs emacsen cpp-doc gcc-4.3-locales
  default-jre defoma-doc psfontmgr dfontmgr libft-perl ispell emacsen-common
  jed-extra apt cdtool setcd mlocate locate slocate wodim cdrkit-doc
  cryptsetup ntfs-3g gnupg-doc libpcsclite1 gnome-device-manager apmd hunspell
  openoffice.org-hunspell openoffice.org-core iproute dhcp3-client dhcp-client
  ppp transfig libasound2-plugins nas libbonobo2-bin glibc-doc libc6-i686
  cups-common libdv-bin libdvdcss2 wget debhelper fakeroot build-essential
  libenchant-voikko esound rng-tools libgd-tools libggi-target-emu
  libggi-target-monotext libggimisc2 desktop-base libgnomevfs2-bin gnutls-bin
  gpgsm gphoto2 gtkam gpm gstreamer-codec-install gnome-codec-install
  gstreamer0.10-tools gstreamer0.10-plugins libjasper-runtime krb5-doc
  krb5-user liblcms-utils lirc libgda2-3 libgdiplus libmono-winforms2.0-cil
  libpam-doc ttf-japanese-gothic ttf-japanese-mincho ttf-thryomanes
  ttf-baekmuk ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp
  ttf-arphic-bkai00mp pulseaudio libraw1394-doc librsvg2-bin hpoj hplip
  libsane-extras avahi-daemon libsasl2-modules-otp libsasl2-modules-ldap
  libsasl2-modules-sql libsasl2-modules-gssapi-mit
  libsasl2-modules-gssapi-heimdal libsmbios-doc speex libwmf0.2-7-gtk iso-cods
  w32codecs libdvdcss mplayer-doc nfs-common ladspa-sdk libnss-mdns
  sun-java6-fonts ttf-sazanami-gothic ttf-kochi-gothic ttf-sazanami-mincho
  ttf-kochi-mincho ttf-wqy-microhei ttf-wqy-zenhei ttf-indic-fonts-core
  ttf-telugu-fonts ttf-oriya-fonts ttf-kannada-fonts ttf-bengali-fonts
  openssl-doc bzip2 perl-doc libterm-readline-gnu-perl
  libterm-readline-perl-perl cpufrequtils python-doc python-tk python-profiler
  python-crypto-dbg python-dbus-doc python-dbus-dbg python-gconf-dbg
  python-gtk2-doc python-gnomecanvas-dbg python-gobject-dbg python-gst0.10-dbg
  python-numpy python-libxml2-dbg python-openssl-doc python-openssl-dbg
  python-pam-dbg python-pyorbit-dbg python-wxgtk2.8 python-wxgtk2.6
  python-wxgtk python-twisted-bin-dbg python-qt3 python-zopeinterface-dbg
  python2.6-doc python2.6-profiler binutils sgml-base-doc watershed
Recommended packages:
  www-browser
The following NEW packages will be installed:
  acl adduser aspell aspell-en binfmt-support busybox-initramfs
  ca-certificates ca-certificates-java conkeror conkeror-spawn-process-helper
  console-setup console-terminus consolekit coreutils cpio cpp cpp-4.3 dbus
  dbus-x11 debconf-i18n debianutils default-jre-headless defoma
  dictionaries-common dmsetup dpkg dvdauthor eject esound-clients espeak
  espeak-data file findutils fontconfig fontconfig-config gamin gawk
  gcc-4.3-base gconf2 gconf2-common geda-doc geda-gnetlist geda-symbols
  genisoimage gimp-data gnome-icon-theme gnome-keyring gnome-mime-data
  gnome-mount gnupg gpgv gsfonts gstreamer0.10-gnonlin
  gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-x
  guile-1.8-libs gvfs gvfs-backends hal hal-info hdparm hicolor-icon-theme
  hunspell-en-us icedtea-6-jre-cacao ifupdown imagemagick imagemagick-doc
  initramfs-tools kbd klibc-utils libaa1 libacl1 libarchive1 libasound2
  libaspell15 libatk1.0-0 libatk1.0-data libattr1 libaudio2 libaudiofile0
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-glib1
  libavc1394-0 libbabl-0.0-0 libbluetooth3 libbonobo2-0 libbonobo2-common
  libbonoboui2-common libburn4 libbz2-1.0 libc6 libcaca0 libcairo2 libcap2
  libcdio-cdda0 libcdio-paranoia0 libcdio7 libcdparanoia0 libcelt0
  libck-connector0 libcomerr2 libcroco3 libcryptui0 libcups2 libcurl3-gnutls
  libdatrie0 libdb4.6 libdb4.7 libdbus-1-3 libdbus-glib-1-2 libdevmapper1.02.1
  libdirectfb-1.0-0 libdjvulibre-text libdjvulibre21 libdrm-intel1 libdrm2
  libdv4 libdvdnav4 libdvdread4 libenca0 libenchant1c2a libesd-alsa0
  libespeak1 libexif12 libexpat1 libfaac0 libffi5 libflac8 libfontconfig1
  libfontenc1 libfreebob0 libfreetype6 libfribidi0 libgail-common libgail18
  libgamin0 libgcc1 libgconf2-4 libgcr0 libgcrypt11 libgd2-noxpm libgdbm3
  libgeda-common libgeda33 libgegl-0.0-0 libggi-target-x libggi2 libgif4
  libgii1 libgii1-target-x libgimp2.0 libgl1-mesa-glx libglade2-0 libglib2.0-0
  libglib2.0-data libglibmm-2.4-1c2a libglu1-mesa libgmp3c2 libgnome-keyring0
  libgnome2-0 libgnome2-common libgnomecanvas2-0 libgnomecanvas2-common
  libgnomekbd-common libgnomeui-0 libgnomeui-common libgnomevfs2-0
  libgnomevfs2-common libgnomevfs2-extra libgnutls26 libgomp1
  libgoocanvas-common libgoocanvas3 libgp11-0 libgpg-error0 libgpgme11
  libgphoto2-2 libgphoto2-port0 libgpm2 libgpod4-nogtk libgraphviz4
  libgsf-1-114 libgsf-1-common libgstreamer-plugins-base0.10-0
  libgstreamer0.10-0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libgtksourceview2.0-0 libgtksourceview2.0-common libgvfscommon0
  libhal-storage1 libhal1 libhunspell-1.2-0 libice6 libidl0 libidn11
  libiec61883-0 libieee1284-3 libilmbase6 libiso9660-5 libisofs6 libjack0
  libjasper1 libjpeg62 libkeyutils1 libklibc libkrb53 liblcms1 libldap-2.4-2
  liblircclient0 liblocale-gettext-perl libltdl7 liblzo2-2 libmad0 libmagic1
  libmagickwand1 libmng1 libmono-corlib2.0-cil libmono-data-tds2.0-cil
  libmono-i18n2.0-cil libmono-security2.0-cil libmono-system-data2.0-cil
  libmono-system2.0-cil libmono0 libmp3lame0 libmpcdec3 libnautilus-extension1
  libncurses5 libncursesw5 libnewt0.52 libnotify1 libnspr4-0d libnss3-1d
  libogg0 liboil0.3 libopenal1 libopenexr6 libopenobex1 liborbit2
  libpam-ck-connector libpam-gnome-keyring libpam-modules libpam-runtime
  libpam0g libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpci3
  libpciaccess0 libpcre3 libpixman-1-0 libpng12-0 libpolkit-dbus2
  libpolkit-gnome0 libpolkit-grant2 libpolkit2 libpoppler-glib4 libpoppler4
  libpopt0 libportaudio2 libproxy0 libpulse-browse0 libpulse0 libraw1394-8
  libreadline5 librsvg2-2 librsvg2-common libsamplerate0 libsane libsasl2-2
  libsasl2-modules libsdl1.2debian libsdl1.2debian-alsa libselinux1 libsepol1
  libsexy2 libsgutils1 libshout3 libsigc++-2.0-0c2a libslang2 libsm6
  libsmbclient libsmbios2 libsndfile1 libsoup-gnome2.4-1 libsoup2.4-1
  libspeex1 libsqlite3-0 libssl0.9.8 libstartup-notification0 libstdc++6
  libstroke0 libsvga1 libsysfs2 libtag1c2a libtalloc1 libtasn1-3
  libtext-charwidth-perl libtext-iconv-perl libthai-data libthai0 libtheora0
  libtiff4 libts-0.0-0 libtwolame0 libusb-0.1-4 libuuid1 libv4l-0 libvcdinfo0
  libvisual-0.4-0 libvisual-0.4-plugins libvolume-id1 libvorbis0a
  libvorbisenc2 libwavpack1 libwbclient0 libwmf0.2-7 libwnck-common libwnck22
  libwrap0 libx11-6 libx11-data libx264-65 libx86-1 libxau6 libxaw7
  libxcb-render-util0 libxcb-render0 libxcb1 libxcomposite1 libxcursor1
  libxdamage1 libxext6 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1
  libxkbfile1 libxklavier12 libxml++2.6-2 libxml2 libxmu6 libxpm4 libxrandr2
  libxrender1 libxres1 libxt6 libxv1 libxvidcore4 libxvmc1 libxxf86dga1
  libxxf86vm1 lsb-base lzma mencoder mime-support module-init-tools
  mono-2.0-runtime mono-common mono-gac mono-jit mount mplayer mplayer-skins
  ncurses-bin net-tools netbase notification-daemon obex-data-server
  openjdk-6-jre-headless openjdk-6-jre-lib openssl passwd pciutils perl
  perl-base perl-modules pm-utils policykit policykit-gnome powermgmt-base
  procps psmisc pulseaudio-utils python python-cairo python-central
  python-crypto python-dbus python-gconf python-glade2 python-gnomecanvas
  python-gobject python-gst0.10 python-gtk2 python-libxml2 python-minimal
  python-openssl python-pam python-pygoocanvas python-pyopenssl python-pyorbit
  python-serial python-setuptools python-support python-twisted-bin
  python-twisted-core python-zopeinterface python2.6 python2.6-minimal
  radeontool readline-common sed sg3-utils sgml-base smartdimmer
  ttf-bitstream-vera ttf-dejavu ttf-dejavu-core ttf-dejavu-extra tzdata
  tzdata-java ucf udev update-inetd usbutils uuid-runtime vbetool vcdimager
  whiptail x-ttcidfont-conf x11-common x11-xkb-utils xfonts-encodings
  xfonts-utils xkb-data xml-core xulrunner-1.9.2 zlib1g
0 upgraded, 444 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/174MB of archives.
After this operation, 654MB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Couldn't configure pre-depend libc6 for findutils, probably a dependency cycle.
[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by Loan_Refi on 2010-12-24
I just ran into the same problem;

Error message:

Couldn't configure pre-depend libc6 for findutils, probably a dependency cycle.

Did you solve your problem? I'm looking for a solution.

Thanks!

---

