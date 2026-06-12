---
title: "Ubuntu 13.04 mini: LXDE not working"
date: 2013-05-10
forum: Desktop Environments
---

### Post by Framba on 2013-05-10
Hi everybody!
Upgrading my Ubuntu 12.10 64 bit to 13.04 I had a problem with LXDE: it's not working any more. LXDM is working, but after login and password I obtain a solid background and the mouse pointer, nothing more. The mouse works, but mouse clicks don't (no OpenBox menu).
_Ubuntu was __installed __ starting from the mini iso_. Then ```
sudo apt-get install lxde
``` to add my favorite DE.
I tried purging and reinstalling all lxde related packages (at least the ones I could figure out) to clear the config with no success.
I also added a new user, same problem.
Then I tried a fresh install of 13.04 mini iso + lxde on another machine and obtained the same behaviour. Maybe it is a dependencies problem (I use LXDE on a standard Ubuntu install recently updated to 13.04 and on a Lubuntu machine without problems).

---

### Post by Framba on 2013-05-11
Update
Today I tried to replicate the problem with a virtual machine.

I used KVM to create a small vm (256 MB of ram and 1.5 GB of disk is enough). Ubuntu 13.04 amd64 mini iso, everything default during vm installation, no additional packages.
Update
```
sudo apt-get update && sudo apt-get upgrade
```
install acpi and ssh-server (to be able to connect via ssh or shutdown via virsh)
```
sudo apt-get install acpid openssh-server
```
install lxde
```
sudo apt-get install lxde
```
and start lxdm
```
sudo service lxdm start
```

Same problem: after logging in I only get a solid background and the mouse pointer.

This is the same procedure I used in the past for my minimal machine and it worked great with Ubuntu 12.10 amd64 mini iso. Any idea?

---

### Post by xoomer.ap on 2013-05-11
You should check logs, especially check Xorg log.
*ls /var/log/Xorg* -l*
choose recently changed log (in my case - /var/log/Xorg.0.log) and scan it for errors:
*sudo cat/var/log/Xorg.0.log | grep EE*
maybe you'll find something helpful.

---

### Post by Framba on 2013-05-11
Hi xoomer.ap, thank you very much for replying.

This is what i found in Xorg's logs on my virtual machine:
```
 sudo cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     6.996] Initializing built-in extension MIT-SCREEN-SAVER
[     7.016] (EE) open /dev/dri/card0: No such file or directory
[     7.017] (EE) open /dev/fb0: No such file or directory
```

And this is on the computer I first got the problem:
```
sudo cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.385] Initializing built-in extension MIT-SCREEN-SAVER
[    16.595] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    16.884] (EE) Failed to load module "fglrx" (module does not exist, 0)
```

I also tried with lxdm logs. On the vm:
```
sudo cat /var/log/lxdm.log
** Message: find greeter (nil)

** Message: find idle (nil)

** Message: add xserver watch


X.Org X Server 1.13.3
Release Date: 2013-03-07
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
Current Operating System: Linux mini 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:35:23 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=681029b7-4fd7-4c4f-a151-4d4ff27a47fa ro splash quiet vt.handoff=7
Build Date: 17 April 2013  10:43:13PM
xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.28.2
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat May 11 12:42:22 2013
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Initializing built-in extension Generic Event Extension
Initializing built-in extension SHAPE
Initializing built-in extension MIT-SHM
Initializing built-in extension XInputExtension
Initializing built-in extension XTEST
Initializing built-in extension BIG-REQUESTS
Initializing built-in extension SYNC
Initializing built-in extension XKEYBOARD
Initializing built-in extension XC-MISC
Initializing built-in extension SECURITY
Initializing built-in extension XINERAMA
Initializing built-in extension XFIXES
Initializing built-in extension RENDER
Initializing built-in extension RANDR
Initializing built-in extension COMPOSITE
Initializing built-in extension DAMAGE
Initializing built-in extension MIT-SCREEN-SAVER
Initializing built-in extension DOUBLE-BUFFER
Initializing built-in extension RECORD
Initializing built-in extension DPMS
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension SELinux
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
Loading extension GLX
error setting MTRR (base = 0xfc000000, size = 0x00100000, type = 1) Invalid argument (22)
** Message: add 0x23dfcc0

** Message: prepare greeter on :0

** Message: start greeter on :0

** Message: greeter 0 session 0x23dfcc0

** Message: user 0 session 0x23dfcc0 cmd USER_LIST

(II) VMWARE(0): vmmouse enable absolute mode
```
And the same on the real computer:
```
sudo cat /var/log/lxdm.log
** Message: find greeter (nil)

** Message: find idle (nil)

** Message: add xserver watch


X.Org X Server 1.13.3
Release Date: 2013-03-07
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
Current Operating System: Linux blackbox 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:35:23 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=34f1d5d1-ba5f-4097-baa9-8da8a7104021 ro splash quiet vt.handoff=7
Build Date: 17 April 2013  10:43:13PM
xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.28.2
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat May 11 13:01:07 2013
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Initializing built-in extension Generic Event Extension
Initializing built-in extension SHAPE
Initializing built-in extension MIT-SHM
Initializing built-in extension XInputExtension
Initializing built-in extension XTEST
Initializing built-in extension BIG-REQUESTS
Initializing built-in extension SYNC
Initializing built-in extension XKEYBOARD
Initializing built-in extension XC-MISC
Initializing built-in extension SECURITY
Initializing built-in extension XINERAMA
Initializing built-in extension XFIXES
Initializing built-in extension RENDER
Initializing built-in extension RANDR
Initializing built-in extension COMPOSITE
Initializing built-in extension DAMAGE
Initializing built-in extension MIT-SCREEN-SAVER
Initializing built-in extension DOUBLE-BUFFER
Initializing built-in extension RECORD
Initializing built-in extension DPMS
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension SELinux
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
Loading extension GLX
(II) [KMS] Kernel modesetting enabled.
** Message: add 0x1cdfbe0

** Message: prepare greeter on :0

** Message: start greeter on :0

** Message: greeter 0 session 0x1cdfbe0

** Message: user 0 session 0x1cdfbe0 cmd USER_LIST

```
Nothing seems very important, at least to me.
Any idea? Any other useful log?

---

### Post by xoomer.ap on 2013-05-11
Sorry, I thought your Xorg can not start. Seems, I was wrong because you have working lxdm.
Hmm, I don't how in upstart go to runlevel 3, but suggest if you run from tty2 (ctrl+alt+f2) *sudo init 3* - you'll get recommendations how to do that. Than, try *xinit /usr/bin/startlxde*.

p.s. there is meta-package lubuntu-desktop, try to execute *apt-get install lubuntu-desktop **-s*** for simulate install process on your system - you'll see what packages are installing.

Btw, disable fglrx module loading by system boot - in /etc/modprobe.d/blacklist.conf add line *blacklist fglrx*. But keep in mind if you will install proprietary drivers from AMD (Catalyst), you must remove that line.

---

### Post by Framba on 2013-05-11
> **xoomer.ap said:**
> Sorry, I thought your Xorg can not start. Seems, I was wrong because you have working lxdm.
Oh, don't mind. Actually thank you again for replying me.

> Hmm, I don't how in upstart go to runlevel 3, but suggest if you run from tty2 (ctrl+alt+f2) *sudo init 3* - you'll get recommendations how to do that. Than, try *xinit /usr/bin/startlxde*.

*sudo init 3* didn't work (at least I didn't see any change nor I received any reccomandation).  I tried with *sudo service lxdm stop*, I hope this is what  was expected.
I needed to install xinit, but it worked and LXDE started! :)
Anyway, if I restart LXDM the problem comes back. :(

> p.s. there is meta-package lubuntu-desktop, try to execute *apt-get install lubuntu-desktop **-s*** for simulate install process on your system - you'll see what packages are installing.

Now that I found LXDE is starting from runlevel 3 I don't think I'm missing a package, but this is the result of the simulate install: Lubuntu-desktop require 830 new packages to be installed.
Here it is the list, but I don't expect anyone to read it unless he knows what to look for:
```
sudo apt-get install lubuntu-desktop -s
Reading package lists...
Building dependency tree...
Reading state information...
The following extra packages will be installed:
  abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview
  account-plugin-facebook account-plugin-flickr account-plugin-generic-oauth
  account-plugin-google account-plugin-twitter ace-of-penguins acpi-support
  alsa-base alsa-utils anacron apg app-install-data appmenu-gtk appmenu-gtk3
  appmenu-qt appmenu-qt5 apport apport-gtk apport-symptoms aptdaemon
  aptdaemon-data apturl apturl-common aspell aspell-en audacious
  audacious-plugins audacious-plugins-data avahi-daemon avahi-utils bamfdaemon
  bc binutils blueman bluez bluez-alsa bluez-cups brasero-common compiz
  compiz-core compiz-gnome compiz-plugins-default cracklib-runtime cups
  cups-browsed cups-bsd cups-client cups-common cups-daemon
  cups-driver-gutenprint cups-filters cups-pk-helper cups-ppdc dc dconf-tools
  dialog diffstat dmz-cursor-theme dnsmasq-base docbook-xml dvd+rw-tools
  elementary-icon-theme enchant evince evince-common evolution-data-server
  evolution-data-server-common ffmpegthumbnailer file-roller firefox
  firefox-globalmenu fonts-freefont-ttf fonts-kacst fonts-kacst-one
  fonts-khmeros-core fonts-lao fonts-liberation fonts-lklug-sinhala fonts-lyx
  fonts-nanum fonts-sil-abyssinica fonts-sil-padauk fonts-takao-pgothic
  fonts-thai-tlwg fonts-tibetan-machine fonts-tlwg-garuda fonts-tlwg-kinnari
  fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa
  fonts-tlwg-sawasdee fonts-tlwg-typewriter fonts-tlwg-typist fonts-tlwg-typo
  fonts-tlwg-umpush fonts-tlwg-waree foomatic-db-compressed-ppds
  foomatic-filters freerdp-x11 friends friends-dispatcher friends-facebook
  friends-twitter gdb gdebi gdebi-core gecko-mediaplayer genisoimage geoclue
  geoclue-ubuntu-geoip gettext ghostscript ghostscript-cups ghostscript-x
  gir1.2-accounts-1.0 gir1.2-atk-1.0 gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0
  gir1.2-ebook-1.2 gir1.2-edataserver-1.2 gir1.2-freedesktop gir1.2-gdata-0.0
  gir1.2-gdkpixbuf-2.0 gir1.2-gnomebluetooth-1.0 gir1.2-goa-1.0
  gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0 gir1.2-gtk-3.0
  gir1.2-javascriptcoregtk-3.0 gir1.2-messagingmenu-1.0
  gir1.2-networkmanager-1.0 gir1.2-notify-0.7 gir1.2-packagekitglib-1.0
  gir1.2-pango-1.0 gir1.2-peas-1.0 gir1.2-rb-3.0 gir1.2-signon-1.0
  gir1.2-soup-2.4 gir1.2-unity-5.0 gir1.2-vte-2.90 gir1.2-webkit-3.0
  gir1.2-wnck-3.0 gkbd-capplet gnome-bluetooth gnome-control-center
  gnome-control-center-data gnome-control-center-signon
  gnome-control-center-unity gnome-desktop-data gnome-desktop3-data
  gnome-disk-utility gnome-icon-theme gnome-icon-theme-full
  gnome-icon-theme-symbolic gnome-menus gnome-mplayer gnome-session-bin
  gnome-settings-daemon gnome-system-tools gnome-time-admin gnome-user-guide
  gnome-user-share gnumeric gnumeric-common gnumeric-doc growisofs gsfonts
  gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gstreamer0.10-x gstreamer1.0-plugins-base
  gstreamer1.0-plugins-good gstreamer1.0-pulseaudio gstreamer1.0-x
  gtk3-engines-unico gucharmap guvcview gvfs-bin hardening-includes hardinfo
  hplip hplip-data hud humanity-icon-theme hunspell-en-us hwdata ibus ibus-gtk
  ibus-gtk3 im-config indicator-applet indicator-application
  indicator-application-gtk2 indicator-appmenu indicator-bluetooth
  indicator-datetime indicator-messages indicator-power indicator-printers
  indicator-session indicator-sound indicator-sync inputattach intltool-debian
  iputils-arping kerneloops-daemon language-selector-gnome libaa1 libaacs0
  libabiword-2.9 libaccount-plugin-1.0-0 libaccounts-glib0 libaccounts-qt1
  libappindicator1 libappindicator3-1 libapt-pkg-perl libarchive-zip-perl
  libart-2.0-2 libasound2-plugins libaspell15 libasprintf-dev libass4
  libasyncns0 libaudclient2 libaudcore1 libaudio2 libavahi-core7 libavc1394-0
  libavcodec53 libavformat53 libavutil51 libbamf3-1 libbinio1ldbl libbluray1
  libbrasero-media3-1 libbs2b0 libburn4 libcaca0 libcairo-perl libcamel-1.2-40
  libcanberra-pulse libcddb2 libcdparanoia0 libclone-perl libcolamd2.7.1
  libcolumbus0-0 libcolumbus0-0-common libcompfaceg1 libcompizconfig0
  libcrack2 libcue1 libcupscgi1 libcupsfilters1 libcupsimage2 libcupsmime1
  libcupsppdc1 libcurl3 libdaemon0 libdbusmenu-glib4 libdbusmenu-gtk3-4
  libdbusmenu-gtk4 libdbusmenu-qt2 libdbusmenu-qt5 libdca0 libdecoration0
  libdee-1.0-4 libdigest-hmac-perl libdirectfb-1.2-9 libdiscid0
  libdjvulibre-text libdjvulibre21 libdmapsharing-3.0-2 libdpkg-perl libdv4
  libdvdnav4 libdvdread4 libebackend-1.2-5 libebook-1.2-14 libecal-1.2-15
  libedata-book-1.2-15 libedata-cal-1.2-18 libedataserver-1.2-17 libelfg0
  libemail-valid-perl libenca0 libenchant1c2a libencode-locale-perl
  libevdocument3-4 libevent-2.0-5 libevview3-3 libexo-1-0 libexo-common
  libexo-helpers libfaad2 libfarstream-0.1-0 libffmpegthumbnailer4
  libfftw3-single3 libfile-copy-recursive-perl libfile-fcntllock-perl
  libfile-listing-perl libflac8 libfluidsynth1 libfont-afm-perl libfontembed1
  libframe6 libfreerdp-plugins-standard libfreerdp1 libfriends0 libfs6
  libgail-3-0 libgda-5.0-4 libgda-5.0-common libgdata-common libgdata13
  libgdome2-0 libgdome2-cpp-smart0c2a libgeis1 libgeoclue0 libgettextpo-dev
  libgettextpo0 libglew1.8 libglewmx1.8 libglib-perl libglib2.0-bin
  libglib2.0-data libglibmm-2.4-1c2a libglu1-mesa libgmime-2.6-0 libgmlib1
  libgmtk1 libgmtk1-data libgnome-bluetooth11 libgnome-control-center1
  libgnome-desktop-3-4 libgnome-menu-3-0 libgnomekbd-common libgnomekbd8
  libgoa-1.0-0 libgoa-1.0-common libgoffice-0.10-10 libgoffice-0.10-10-common
  libgomp1 libgpgme11 libgpm2 libgpod-common libgpod4 libgrail6 libgrip0
  libgs9 libgs9-common libgsf-1-114 libgsf-1-common libgsm1 libgssdp-1.0-3
  libgstreamer-plugins-base0.10-0 libgstreamer-plugins-base1.0-0
  libgstreamer-plugins-good1.0-0 libgstreamer0.10-0 libgstreamer1.0-0
  libgtk2-perl libgtkmathview0c2a libgtkspell0 libgucharmap-2-90-7 libguess1
  libgupnp-1.0-4 libgupnp-igd-1.0-4 libgutenprint2 libgweather-3-1
  libgweather-common libgxps2 libhpmud0 libhtml-form-perl libhtml-format-perl
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl
  libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libhunspell-1.3-0 libibus-1.0-0
  libical0 libido3-0.1-0 libiec61883-0 libijs-0.35 libindicator3-7
  libindicator7 libio-pty-perl libio-socket-inet6-perl libio-socket-ssl-perl
  libipc-run-perl libisofs6 libjack-jackd2-0 libjavascriptcoregtk-3.0-0
  libjbig2dec0 libjs-jquery libjson-glib-1.0-0 libjte1 libkpathsea6 liblcms1
  liblightdm-gobject-1-0 liblink-grammar4 liblircclient0 libloudmouth1-0
  liblua5.1-0 liblwp-mediatypes-perl liblwp-protocol-https-perl
  libmailtools-perl libmeanwhile1 libmessaging-menu0 libmetacity-private0a
  libmhash2 libminiupnpc8 libmms0 libmng1 libmodplug1 libmowgli2 libmp3lame0
  libmpg123-0 libmusicbrainz3-6 libmysqlclient18 libnatpmp1
  libnautilus-extension1a libneon27-gnutls libnet-dbus-perl libnet-dns-perl
  libnet-domain-tld-perl libnet-http-perl libnet-ip-perl libnet-ssleay-perl
  libnetfilter-conntrack3 libnice10 libnl-route-3-200 libnm-glib-vpn1
  libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify-bin
  libnss-mdns libnux-4.0-0 libnux-4.0-common liboauth0 libonig2 liboobs-1-5
  libopenobex1 libopts25 liborc-0.4-0 libots0 libpackagekit-glib2-14
  libpam-freerdp libpam-xdg-support libpanel-applet-4-0 libpango-perl
  libpaper-utils libpaper1 libpcsclite1 libpeas-1.0-0 libpeas-common
  libperl5.14 libpisock9 libpoppler-glib8 libpoppler28 libportaudio2
  libpostproc52 libprotobuf7 libpth20 libpulse-mainloop-glib0 libpulse0
  libpulsedsp libpurple-bin libpurple0 libpwquality1 libpython2.7 libpython3.3
  libqjson0 libqpdf10 libqt4-dbus libqt4-declarative libqt4-network
  libqt4-opengl libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite
  libqt4-test libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqtwebkit4
  libquvi-scripts libquvi7 libraptor2-0 librarian0 librasqal3 libraw1394-11
  librdf0 libreadline5 libresid-builder0c2a librest-0.7-0 librhythmbox-core6
  libsamplerate0 libsane-hpaio libschroedinger-1.0-0 libsdl1.2debian
  libsensors4 libsgutils2-2 libshout3 libsidplay2 libsignon-extension1
  libsignon-glib1 libsignon-plugins-common1 libsignon-qt1 libsndfile1
  libsnmp-base libsnmp15 libsocket6-perl libspectre1 libspeex1 libspeexdsp1
  libswscale2 libsysfs2 libsystemd-daemon0 libt1-5 libtag1-vanilla libtag1c2a
  libtelepathy-glib0 libtext-levenshtein-perl libtheora0 libtidy-0.99-0
  libtie-ixhash-perl libtimezonemap1 libtotem-plparser17 libts-0.0-0
  libuniconf4.6 libunistring0 libunity-common libunity-core-6.0-5
  libunity-misc4 libunity-protocol-private0 libunity-webapps0 libunity9
  libupower-glib1 liburi-perl libva1 libvdpau1 libvisual-0.4-0
  libvisual-0.4-plugins libvorbisenc2 libvpx1 libvte-2.90-9 libvte-2.90-common
  libwacom-common libwacom2 libwavpack1 libwebcam0 libwebkitgtk-3.0-0
  libwebkitgtk-3.0-common libwhoopsie0 libwmf0.2-7 libwnck-3-0
  libwnck-3-common libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwv-1.2-4
  libwvstreams4.6-base libwvstreams4.6-extras libwww-perl
  libwww-robotrules-perl libx86-1 libxfce4ui-1-0 libxfce4util-bin
  libxfce4util-common libxfce4util6 libxfconf-0-2 libxklavier16
  libxml-parser-perl libxml-twig-perl libxml-xpath-perl libxp6 libxslt1.1
  libxvidcore4 libyajl2 libyelp0 libzeitgeist-1.0-1 libzephyr4 lightdm
  lightdm-gtk-greeter lightdm-remote-session-freerdp
  lightdm-remote-session-uccsconfigure link-grammar-dictionaries-en lintian
  linux-sound-base lm-sensors lp-solve lubuntu-artwork lubuntu-artwork-13-04
  lubuntu-core lubuntu-default-session lubuntu-default-settings
  lubuntu-icon-theme lubuntu-lxpanel-icons lubuntu-software-center
  lxappearance-obconf lxkeymap lxlauncher lxpanel-indicator-applet-plugin
  lxtask make media-player-info metacity-common mobile-broadband-provider-info
  modemmanager mousetweaks mplayer2 mscompress mtpaint mysql-common
  nautilus-data network-manager network-manager-gnome network-manager-pptp
  network-manager-pptp-gnome ntp nux-tools obex-data-server obexd-client
  openprinting-ppds patch patchutils pcmciautils pidgin pidgin-data
  pidgin-libnotify pidgin-microblog plymouth-label plymouth-theme-lubuntu-logo
  plymouth-theme-lubuntu-text pm-utils policykit-desktop-privileges
  poppler-data poppler-utils pptp-linux printer-driver-c2esp
  printer-driver-foo2zjs printer-driver-gutenprint printer-driver-hpcups
  printer-driver-min12xxw printer-driver-pnm2ppa printer-driver-postscript-hp
  printer-driver-ptouch printer-driver-pxljr printer-driver-sag-gdi
  printer-driver-splix pulseaudio pulseaudio-module-x11 pulseaudio-utils
  python-appindicator python-aptdaemon python-aptdaemon.gtk3widgets
  python-cairo python-cups python-cupshelpers python-dbus python-dbus-dev
  python-defer python-dirspec python-gconf python-gi python-gnomekeyring
  python-gobject python-gobject-2 python-gtk2 python-ibus python-imaging
  python-imaging-compat python-libxml2 python-mako python-markupsafe
  python-notify python-pexpect python-pkg-resources python-pycurl
  python-pysqlite2 python-renderpm python-reportlab python-reportlab-accel
  python-smbc python-support python-xdg python-xklavier python-zeitgeist
  python3-apport python3-aptdaemon python3-aptdaemon.gtk3widgets
  python3-aptdaemon.pkcompat python3-crypto python3-defer python3-httplib2
  python3-oauthlib python3-pkg-resources python3-problem-report
  python3-software-properties python3-xdg python3-xkit qdbus qpdf qtchooser
  radeontool rarian-compat remote-login-service rfkill rhythmbox
  rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-zeitgeist rhythmbox-plugins rhythmbox-ubuntuone rtkit
  samba-common samba-common-bin sane-utils session-migration sessioninstaller
  sgml-data signon-keyring-extension signon-plugin-oauth2 signon-ui signond
  simple-scan smbclient software-properties-common software-properties-gtk
  ssl-cert sylpheed sylpheed-doc sylpheed-i18n sylpheed-plugins synaptic
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev system-tools-backends systemd-services
  systemd-shim t1utils thin-client-config-agent toshset transmission
  transmission-common transmission-gtk tsconf ttf-indic-fonts-core
  ttf-punjabi-fonts ttf-ubuntu-font-family ttf-wqy-microhei
  ubuntu-drivers-common ubuntu-extras-keyring ubuntu-release-upgrader-gtk
  ubuntu-system-service unattended-upgrades unity unity-asset-pool
  unity-common unity-greeter unity-lens-applications unity-lens-files
  unity-lens-friends unity-lens-music unity-lens-photos unity-lens-shopping
  unity-lens-video unity-scope-gdrive unity-scope-musicstores
  unity-scope-video-remote unity-services unity-webapps-service update-inetd
  update-manager update-notifier update-notifier-common upower usb-modeswitch
  usb-modeswitch-data uvcdynctrl uvcdynctrl-data vbetool whoopsie
  wireless-tools wpasupplicant wvdial x11-apps x11-session-utils x11-xfs-utils
  xdg-user-dirs xdg-user-dirs-gtk xfburn xfce-keyboard-shortcuts xfce4-notifyd
  xfce4-power-manager xfce4-power-manager-data xfconf xfonts-100dpi
  xfonts-scalable xinput xorg xorg-docs-core xpad xul-ext-ubufox yelp yelp-xsl
  zeitgeist zeitgeist-core zeitgeist-datahub zenity zenity-common zip
Suggested packages:
  apmd alsa-oss oss-compat default-mta mail-transport-agent libqt5core5
  libqt5dbus5 libqt5gui5 libqt5widgets5 aspell-doc spellutils avahi-autoipd
  binutils-doc bluez-hcidump cups-pdf xpp docbook docbook-dsssl docbook-xsl
  docbook-defguide cdrskin unrar nautilus evolution evolution-data-server-dbg
  arj lha lzip lzop ncompress rpm2cpio rzip sharutils unace unalz unar zoo
  latex-xft-fonts firefox-gnome-support libgraphite3 pango-graphite
  libgraphite2-2.0.0 hplip-cups printer-driver-all cjet gdb-doc gdbserver
  wodim cdrkit-doc gettext-doc hpijs nautilus-sendto libcanberra-gtk-module
  gnome-screensaver apache2.2-bin libapache2-mod-dnssd gnumeric-plugins-extra
  epiphany-browser ttf-liberation ttf-mscorefonts-installer mesa-utils
  hplip-gui hplip-doc system-config-printer hunspell openoffice.org-hunspell
  openoffice.org-core ibus-doc nas libbluray-bdj gstreamer1.0-plugins-bad
  gstreamer1.0-fluendo-mp3 gstreamer1.0-plugins-ugly cdrdao
  libfont-freetype-perl debian-keyring gcc c-compiler libdv-bin libdvdcss2
  debhelper fakeroot build-essential libenchant-voikko libfftw3-bin
  libfftw3-dev libgda-5.0-bin libgda-5.0-mysql libgda-5.0-postgres glew-utils
  libgmlib1-dbg libgmtk1-dbg gpgsm gpm fonts-droid gstreamer-codec-install
  gnome-codec-install gstreamer0.10-tools gstreamer1.0-tools libgtk2-perl-doc
  gutenprint-locales libdata-dump-perl jackd2 javascript-common liblcms-utils
  lirc libcrypt-ssleay-perl minissdpd natpmp-utils pcscd jpilot pilot-link
  kpilot gnome-pilot claws-mail tcl8.5 tk8.5
  libqt4-declarative-folderlistmodel libqt4-declarative-gestures
  libqt4-declarative-particles libqt4-declarative-shaders qt4-qmlviewer
  libqt4-dev qt4-qtconfig raptor2-utils rasqal-utils libraw1394-doc
  librdf-storage-postgresql librdf-storage-mysql librdf-storage-sqlite
  redland-utils sg3-utils snmp-mibs-downloader libspectre1-dbg speex
  nvidia-vdpau-driver vdpau-driver gstreamer1.0-ffmpeg libwmf0.2-7-gtk
  libauthen-ntlm-perl libunicode-map8-perl libunicode-string-perl
  xml-twig-tools binutils-multiarch dpkg-dev libperlio-gzip-perl
  libtext-template-perl fancontrol sensord read-edid i2c-tools amixer
  indicator-messages-gtk2 indicator-sound-gtk2 make-doc
  network-manager-openconnect-gnome network-manager-openvpn-gnome
  network-manager-vpnc-gnome ntp-doc hpijs-ppds diffutils-doc gnome-panel
  kdebase-workspace-bin docker cpufrequtils ethtool fonts-japanese-mincho
  fonts-ipafont-mincho fonts-japanese-gothic fonts-ipafont-gothic
  fonts-arphic-ukai fonts-arphic-uming fonts-unfonts-core psutils
  hannah-foo2zjs tk8.4 tix gutenprint-doc magicfilter apsfilter pavumeter
  paman pavucontrol paprefs pulseaudio-module-raop pulseaudio-esound-compat
  python-dbus-doc python-dbus-dbg python-gnome2-doc python-gi-cairo
  python-gobject-2-dbg python-gtk2-doc python-imaging-doc python-imaging-dbg
  python-beaker python-mako-doc python-distribute python-distribute-doc
  libcurl4-gnutls-dev python-pycurl-dbg python-pysqlite2-doc
  python-pysqlite2-dbg python-renderpm-dbg pdf-viewer
  python-egenix-mxtexttools python-reportlab-doc python3-launchpadlib
  python3-crypto-dbg python-crypto-doc python3-setuptools qt4-default
  qt5-default unpaper perlsgml w3-recs opensp libxml2-utils cifs-utils
  openssl-blacklist claws-mail-tools bogofilter bsfilter curl dwww deborphan
  x-ttcidfont-conf bsd-mailx comgt wpagui libengine-pkcs11-openssl
  xfce4-power-manager-plugins udisks xorg-docs xfonts-75dpi
Recommended packages:
  im-switch
The following NEW packages will be installed:
  abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview
  account-plugin-facebook account-plugin-flickr account-plugin-generic-oauth
  account-plugin-google account-plugin-twitter ace-of-penguins acpi-support
  alsa-base alsa-utils anacron apg app-install-data appmenu-gtk appmenu-gtk3
  appmenu-qt appmenu-qt5 apport apport-gtk apport-symptoms aptdaemon
  aptdaemon-data apturl apturl-common aspell aspell-en audacious
  audacious-plugins audacious-plugins-data avahi-daemon avahi-utils bamfdaemon
  bc binutils blueman bluez bluez-alsa bluez-cups brasero-common compiz
  compiz-core compiz-gnome compiz-plugins-default cracklib-runtime cups
  cups-browsed cups-bsd cups-client cups-common cups-daemon
  cups-driver-gutenprint cups-filters cups-pk-helper cups-ppdc dc dconf-tools
  dialog diffstat dmz-cursor-theme dnsmasq-base docbook-xml dvd+rw-tools
  elementary-icon-theme enchant evince evince-common evolution-data-server
  evolution-data-server-common ffmpegthumbnailer file-roller firefox
  firefox-globalmenu fonts-freefont-ttf fonts-kacst fonts-kacst-one
  fonts-khmeros-core fonts-lao fonts-liberation fonts-lklug-sinhala fonts-lyx
  fonts-nanum fonts-sil-abyssinica fonts-sil-padauk fonts-takao-pgothic
  fonts-thai-tlwg fonts-tibetan-machine fonts-tlwg-garuda fonts-tlwg-kinnari
  fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa
  fonts-tlwg-sawasdee fonts-tlwg-typewriter fonts-tlwg-typist fonts-tlwg-typo
  fonts-tlwg-umpush fonts-tlwg-waree foomatic-db-compressed-ppds
  foomatic-filters freerdp-x11 friends friends-dispatcher friends-facebook
  friends-twitter gdb gdebi gdebi-core gecko-mediaplayer genisoimage geoclue
  geoclue-ubuntu-geoip gettext ghostscript ghostscript-cups ghostscript-x
  gir1.2-accounts-1.0 gir1.2-atk-1.0 gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0
  gir1.2-ebook-1.2 gir1.2-edataserver-1.2 gir1.2-freedesktop gir1.2-gdata-0.0
  gir1.2-gdkpixbuf-2.0 gir1.2-gnomebluetooth-1.0 gir1.2-goa-1.0
  gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0 gir1.2-gtk-3.0
  gir1.2-javascriptcoregtk-3.0 gir1.2-messagingmenu-1.0
  gir1.2-networkmanager-1.0 gir1.2-notify-0.7 gir1.2-packagekitglib-1.0
  gir1.2-pango-1.0 gir1.2-peas-1.0 gir1.2-rb-3.0 gir1.2-signon-1.0
  gir1.2-soup-2.4 gir1.2-unity-5.0 gir1.2-vte-2.90 gir1.2-webkit-3.0
  gir1.2-wnck-3.0 gkbd-capplet gnome-bluetooth gnome-control-center
  gnome-control-center-data gnome-control-center-signon
  gnome-control-center-unity gnome-desktop-data gnome-desktop3-data
  gnome-disk-utility gnome-icon-theme gnome-icon-theme-full
  gnome-icon-theme-symbolic gnome-menus gnome-mplayer gnome-session-bin
  gnome-settings-daemon gnome-system-tools gnome-time-admin gnome-user-guide
  gnome-user-share gnumeric gnumeric-common gnumeric-doc growisofs gsfonts
  gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gstreamer0.10-x gstreamer1.0-plugins-base
  gstreamer1.0-plugins-good gstreamer1.0-pulseaudio gstreamer1.0-x
  gtk3-engines-unico gucharmap guvcview gvfs-bin hardening-includes hardinfo
  hplip hplip-data hud humanity-icon-theme hunspell-en-us hwdata ibus ibus-gtk
  ibus-gtk3 im-config indicator-applet indicator-application
  indicator-application-gtk2 indicator-appmenu indicator-bluetooth
  indicator-datetime indicator-messages indicator-power indicator-printers
  indicator-session indicator-sound indicator-sync inputattach intltool-debian
  iputils-arping kerneloops-daemon language-selector-gnome libaa1 libaacs0
  libabiword-2.9 libaccount-plugin-1.0-0 libaccounts-glib0 libaccounts-qt1
  libappindicator1 libappindicator3-1 libapt-pkg-perl libarchive-zip-perl
  libart-2.0-2 libasound2-plugins libaspell15 libasprintf-dev libass4
  libasyncns0 libaudclient2 libaudcore1 libaudio2 libavahi-core7 libavc1394-0
  libavcodec53 libavformat53 libavutil51 libbamf3-1 libbinio1ldbl libbluray1
  libbrasero-media3-1 libbs2b0 libburn4 libcaca0 libcairo-perl libcamel-1.2-40
  libcanberra-pulse libcddb2 libcdparanoia0 libclone-perl libcolamd2.7.1
  libcolumbus0-0 libcolumbus0-0-common libcompfaceg1 libcompizconfig0
  libcrack2 libcue1 libcupscgi1 libcupsfilters1 libcupsimage2 libcupsmime1
  libcupsppdc1 libcurl3 libdaemon0 libdbusmenu-glib4 libdbusmenu-gtk3-4
  libdbusmenu-gtk4 libdbusmenu-qt2 libdbusmenu-qt5 libdca0 libdecoration0
  libdee-1.0-4 libdigest-hmac-perl libdirectfb-1.2-9 libdiscid0
  libdjvulibre-text libdjvulibre21 libdmapsharing-3.0-2 libdpkg-perl libdv4
  libdvdnav4 libdvdread4 libebackend-1.2-5 libebook-1.2-14 libecal-1.2-15
  libedata-book-1.2-15 libedata-cal-1.2-18 libedataserver-1.2-17 libelfg0
  libemail-valid-perl libenca0 libenchant1c2a libencode-locale-perl
  libevdocument3-4 libevent-2.0-5 libevview3-3 libexo-1-0 libexo-common
  libexo-helpers libfaad2 libfarstream-0.1-0 libffmpegthumbnailer4
  libfftw3-single3 libfile-copy-recursive-perl libfile-fcntllock-perl
  libfile-listing-perl libflac8 libfluidsynth1 libfont-afm-perl libfontembed1
  libframe6 libfreerdp-plugins-standard libfreerdp1 libfriends0 libfs6
  libgail-3-0 libgda-5.0-4 libgda-5.0-common libgdata-common libgdata13
  libgdome2-0 libgdome2-cpp-smart0c2a libgeis1 libgeoclue0 libgettextpo-dev
  libgettextpo0 libglew1.8 libglewmx1.8 libglib-perl libglib2.0-bin
  libglib2.0-data libglibmm-2.4-1c2a libglu1-mesa libgmime-2.6-0 libgmlib1
  libgmtk1 libgmtk1-data libgnome-bluetooth11 libgnome-control-center1
  libgnome-desktop-3-4 libgnome-menu-3-0 libgnomekbd-common libgnomekbd8
  libgoa-1.0-0 libgoa-1.0-common libgoffice-0.10-10 libgoffice-0.10-10-common
  libgomp1 libgpgme11 libgpm2 libgpod-common libgpod4 libgrail6 libgrip0
  libgs9 libgs9-common libgsf-1-114 libgsf-1-common libgsm1 libgssdp-1.0-3
  libgstreamer-plugins-base0.10-0 libgstreamer-plugins-base1.0-0
  libgstreamer-plugins-good1.0-0 libgstreamer0.10-0 libgstreamer1.0-0
  libgtk2-perl libgtkmathview0c2a libgtkspell0 libgucharmap-2-90-7 libguess1
  libgupnp-1.0-4 libgupnp-igd-1.0-4 libgutenprint2 libgweather-3-1
  libgweather-common libgxps2 libhpmud0 libhtml-form-perl libhtml-format-perl
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl
  libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libhunspell-1.3-0 libibus-1.0-0
  libical0 libido3-0.1-0 libiec61883-0 libijs-0.35 libindicator3-7
  libindicator7 libio-pty-perl libio-socket-inet6-perl libio-socket-ssl-perl
  libipc-run-perl libisofs6 libjack-jackd2-0 libjavascriptcoregtk-3.0-0
  libjbig2dec0 libjs-jquery libjson-glib-1.0-0 libjte1 libkpathsea6 liblcms1
  liblightdm-gobject-1-0 liblink-grammar4 liblircclient0 libloudmouth1-0
  liblua5.1-0 liblwp-mediatypes-perl liblwp-protocol-https-perl
  libmailtools-perl libmeanwhile1 libmessaging-menu0 libmetacity-private0a
  libmhash2 libminiupnpc8 libmms0 libmng1 libmodplug1 libmowgli2 libmp3lame0
  libmpg123-0 libmusicbrainz3-6 libmysqlclient18 libnatpmp1
  libnautilus-extension1a libneon27-gnutls libnet-dbus-perl libnet-dns-perl
  libnet-domain-tld-perl libnet-http-perl libnet-ip-perl libnet-ssleay-perl
  libnetfilter-conntrack3 libnice10 libnl-route-3-200 libnm-glib-vpn1
  libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify-bin
  libnss-mdns libnux-4.0-0 libnux-4.0-common liboauth0 libonig2 liboobs-1-5
  libopenobex1 libopts25 liborc-0.4-0 libots0 libpackagekit-glib2-14
  libpam-freerdp libpam-xdg-support libpanel-applet-4-0 libpango-perl
  libpaper-utils libpaper1 libpcsclite1 libpeas-1.0-0 libpeas-common
  libperl5.14 libpisock9 libpoppler-glib8 libpoppler28 libportaudio2
  libpostproc52 libprotobuf7 libpth20 libpulse-mainloop-glib0 libpulse0
  libpulsedsp libpurple-bin libpurple0 libpwquality1 libpython2.7 libpython3.3
  libqjson0 libqpdf10 libqt4-dbus libqt4-declarative libqt4-network
  libqt4-opengl libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite
  libqt4-test libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqtwebkit4
  libquvi-scripts libquvi7 libraptor2-0 librarian0 librasqal3 libraw1394-11
  librdf0 libreadline5 libresid-builder0c2a librest-0.7-0 librhythmbox-core6
  libsamplerate0 libsane-hpaio libschroedinger-1.0-0 libsdl1.2debian
  libsensors4 libsgutils2-2 libshout3 libsidplay2 libsignon-extension1
  libsignon-glib1 libsignon-plugins-common1 libsignon-qt1 libsndfile1
  libsnmp-base libsnmp15 libsocket6-perl libspectre1 libspeex1 libspeexdsp1
  libswscale2 libsysfs2 libsystemd-daemon0 libt1-5 libtag1-vanilla libtag1c2a
  libtelepathy-glib0 libtext-levenshtein-perl libtheora0 libtidy-0.99-0
  libtie-ixhash-perl libtimezonemap1 libtotem-plparser17 libts-0.0-0
  libuniconf4.6 libunistring0 libunity-common libunity-core-6.0-5
  libunity-misc4 libunity-protocol-private0 libunity-webapps0 libunity9
  libupower-glib1 liburi-perl libva1 libvdpau1 libvisual-0.4-0
  libvisual-0.4-plugins libvorbisenc2 libvpx1 libvte-2.90-9 libvte-2.90-common
  libwacom-common libwacom2 libwavpack1 libwebcam0 libwebkitgtk-3.0-0
  libwebkitgtk-3.0-common libwhoopsie0 libwmf0.2-7 libwnck-3-0
  libwnck-3-common libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwv-1.2-4
  libwvstreams4.6-base libwvstreams4.6-extras libwww-perl
  libwww-robotrules-perl libx86-1 libxfce4ui-1-0 libxfce4util-bin
  libxfce4util-common libxfce4util6 libxfconf-0-2 libxklavier16
  libxml-parser-perl libxml-twig-perl libxml-xpath-perl libxp6 libxslt1.1
  libxvidcore4 libyajl2 libyelp0 libzeitgeist-1.0-1 libzephyr4 lightdm
  lightdm-gtk-greeter lightdm-remote-session-freerdp
  lightdm-remote-session-uccsconfigure link-grammar-dictionaries-en lintian
  linux-sound-base lm-sensors lp-solve lubuntu-artwork lubuntu-artwork-13-04
  lubuntu-core lubuntu-default-session lubuntu-default-settings
  lubuntu-desktop lubuntu-icon-theme lubuntu-lxpanel-icons
  lubuntu-software-center lxappearance-obconf lxkeymap lxlauncher
  lxpanel-indicator-applet-plugin lxtask make media-player-info
  metacity-common mobile-broadband-provider-info modemmanager mousetweaks
  mplayer2 mscompress mtpaint mysql-common nautilus-data network-manager
  network-manager-gnome network-manager-pptp network-manager-pptp-gnome ntp
  nux-tools obex-data-server obexd-client openprinting-ppds patch patchutils
  pcmciautils pidgin pidgin-data pidgin-libnotify pidgin-microblog
  plymouth-label plymouth-theme-lubuntu-logo plymouth-theme-lubuntu-text
  pm-utils policykit-desktop-privileges poppler-data poppler-utils pptp-linux
  printer-driver-c2esp printer-driver-foo2zjs printer-driver-gutenprint
  printer-driver-hpcups printer-driver-min12xxw printer-driver-pnm2ppa
  printer-driver-postscript-hp printer-driver-ptouch printer-driver-pxljr
  printer-driver-sag-gdi printer-driver-splix pulseaudio pulseaudio-module-x11
  pulseaudio-utils python-appindicator python-aptdaemon
  python-aptdaemon.gtk3widgets python-cairo python-cups python-cupshelpers
  python-dbus python-dbus-dev python-defer python-dirspec python-gconf
  python-gi python-gnomekeyring python-gobject python-gobject-2 python-gtk2
  python-ibus python-imaging python-imaging-compat python-libxml2 python-mako
  python-markupsafe python-notify python-pexpect python-pkg-resources
  python-pycurl python-pysqlite2 python-renderpm python-reportlab
  python-reportlab-accel python-smbc python-support python-xdg python-xklavier
  python-zeitgeist python3-apport python3-aptdaemon
  python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-crypto
  python3-defer python3-httplib2 python3-oauthlib python3-pkg-resources
  python3-problem-report python3-software-properties python3-xdg python3-xkit
  qdbus qpdf qtchooser radeontool rarian-compat remote-login-service rfkill
  rhythmbox rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-zeitgeist rhythmbox-plugins rhythmbox-ubuntuone rtkit
  samba-common samba-common-bin sane-utils session-migration sessioninstaller
  sgml-data signon-keyring-extension signon-plugin-oauth2 signon-ui signond
  simple-scan smbclient software-properties-common software-properties-gtk
  ssl-cert sylpheed sylpheed-doc sylpheed-i18n sylpheed-plugins synaptic
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev system-tools-backends systemd-services
  systemd-shim t1utils thin-client-config-agent toshset transmission
  transmission-common transmission-gtk tsconf ttf-indic-fonts-core
  ttf-punjabi-fonts ttf-ubuntu-font-family ttf-wqy-microhei
  ubuntu-drivers-common ubuntu-extras-keyring ubuntu-release-upgrader-gtk
  ubuntu-system-service unattended-upgrades unity unity-asset-pool
  unity-common unity-greeter unity-lens-applications unity-lens-files
  unity-lens-friends unity-lens-music unity-lens-photos unity-lens-shopping
  unity-lens-video unity-scope-gdrive unity-scope-musicstores
  unity-scope-video-remote unity-services unity-webapps-service update-inetd
  update-manager update-notifier update-notifier-common upower usb-modeswitch
  usb-modeswitch-data uvcdynctrl uvcdynctrl-data vbetool whoopsie
  wireless-tools wpasupplicant wvdial x11-apps x11-session-utils x11-xfs-utils
  xdg-user-dirs xdg-user-dirs-gtk xfburn xfce-keyboard-shortcuts xfce4-notifyd
  xfce4-power-manager xfce4-power-manager-data xfconf xfonts-100dpi
  xfonts-scalable xinput xorg xorg-docs-core xpad xul-ext-ubufox yelp yelp-xsl
  zeitgeist zeitgeist-core zeitgeist-datahub zenity zenity-common zip
0 upgraded, 830 newly installed, 0 to remove and 0 not upgraded.
Inst ace-of-penguins (1.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libdbusmenu-glib4 (12.10.3daily13.02.01-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libdbusmenu-gtk4 (12.10.3daily13.02.01-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst appmenu-gtk (12.10.3daily13.04.03-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libdbusmenu-gtk3-4 (12.10.3daily13.02.01-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst appmenu-gtk3 (12.10.3daily13.04.03-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst audacious-plugins-data (3.3.4-1ubuntu1 Ubuntu:13.04/raring [all])
Inst libaudcore1 (3.3.4-1 Ubuntu:13.04/raring [amd64])
Inst libavutil51 (6:0.8.6-1ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libgsm1 (1.0.13-4 Ubuntu:13.04/raring [amd64])
Inst liborc-0.4-0 (1:0.4.17-1 Ubuntu:13.04/raring [amd64])
Inst libschroedinger-1.0-0 (1.0.11-2 Ubuntu:13.04/raring [amd64])
Inst libspeex1 (1.2~rc1-7ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libtheora0 (1.1.1+dfsg.1-3.1 Ubuntu:13.04/raring [amd64])
Inst libva1 (1.0.15-4build1 Ubuntu:13.04/raring [amd64])
Inst libvorbisenc2 (1.3.2-1.3 Ubuntu:13.04/raring [amd64])
Inst libvpx1 (1.1.0-1 Ubuntu:13.04/raring [amd64])
Inst libavcodec53 (6:0.8.6-1ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libavformat53 (6:0.8.6-1ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libbinio1ldbl (1.4+dfsg1-1 Ubuntu:13.04/raring [amd64])
Inst libbs2b0 (3.1.0+dfsg-2ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libcddb2 (1.3.2-3fakesync1 Ubuntu:13.04/raring [amd64])
Inst libcue1 (1.4.0-1 Ubuntu:13.04/raring [amd64])
Inst libfaad2 (2.7-8 Ubuntu:13.04/raring [amd64])
Inst libflac8 (1.2.1-6build1 Ubuntu:13.04/raring [amd64])
Inst libsamplerate0 (0.1.8-5 Ubuntu:13.04/raring [amd64])
Inst libjack-jackd2-0 (1.9.9.5+20130127git15950eb1-1 Ubuntu:13.04/raring [amd64])
Inst libasyncns0 (0.8-4build1 Ubuntu:13.04/raring [amd64])
Inst libsndfile1 (1.0.25-5 Ubuntu:13.04/raring [amd64])
Inst libpulse0 (1:3.0-0ubuntu6 Ubuntu:13.04/raring [amd64])
Inst libfluidsynth1 (1.1.6-2 Ubuntu:13.04/raring [amd64])
Inst liblircclient0 (0.9.0-0ubuntu3 Ubuntu:13.04/raring [amd64])
Inst libmms0 (0.6.2-3 Ubuntu:13.04/raring [amd64])
Inst libmodplug1 (1:0.8.8.4-3 Ubuntu:13.04/raring [amd64])
Inst libmp3lame0 (3.99.5+repack1-3 Ubuntu:13.04/raring [amd64])
Inst libmpg123-0 (1.14.4-1 Ubuntu:13.04/raring [amd64])
Inst libneon27-gnutls (0.29.6-3 Ubuntu:13.04/raring [amd64])
Inst libresid-builder0c2a (2.1.1-14 Ubuntu:13.04/raring [amd64])
Inst libcaca0 (0.99.beta18-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libsdl1.2debian (1.2.15-5ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libsidplay2 (2.1.1-14 Ubuntu:13.04/raring [amd64])
Inst libwavpack1 (4.60.1-3 Ubuntu:13.04/raring [amd64])
Inst audacious-plugins (3.3.4-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst bluez (4.101-0ubuntu8b1 Ubuntu:13.04/raring [amd64])
Inst libcupscgi1 (1.6.2-1ubuntu5 Ubuntu:13.04/raring [amd64])
Inst libcupsfilters1 (1.0.34-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libcupsimage2 (1.6.2-1ubuntu5 Ubuntu:13.04/raring [amd64])
Inst libcupsmime1 (1.6.2-1ubuntu5 Ubuntu:13.04/raring [amd64])
Inst libcupsppdc1 (1.6.2-1ubuntu5 Ubuntu:13.04/raring [amd64])
Inst libpaper1 (1.1.24+nmu2ubuntu2 Ubuntu:13.04/raring [amd64])
Inst ssl-cert (1.0.32 Ubuntu:13.04/raring [all])
Inst bc (1.06.95-4ubuntu1 Ubuntu:13.04/raring [amd64])
Inst cups-daemon (1.6.2-1ubuntu5 Ubuntu:13.04/raring [amd64])
Inst libpoppler28 (0.20.5-1ubuntu3 Ubuntu:13.04/raring [amd64])
Inst poppler-utils (0.20.5-1ubuntu3 Ubuntu:13.04/raring [amd64])
Inst libijs-0.35 (0.35-8build1 Ubuntu:13.04/raring [amd64])
Inst libjbig2dec0 (0.11+20120125-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst poppler-data (0.4.6-2 Ubuntu:13.04/raring [all])
Inst libgs9-common (9.07~dfsg2-0ubuntu3 Ubuntu:13.04/raring [all])
Inst libgs9 (9.07~dfsg2-0ubuntu3 Ubuntu:13.04/raring [amd64])
Inst gsfonts (1:8.11+urwcyr1.0.7~pre44-4.2ubuntu1 Ubuntu:13.04/raring [all])
Inst ghostscript (9.07~dfsg2-0ubuntu3 Ubuntu:13.04/raring [amd64])
Inst cups-common (1.6.2-1ubuntu5 Ubuntu:13.04/raring [all])
Inst cups-client (1.6.2-1ubuntu5 Ubuntu:13.04/raring [amd64])
Inst cups-ppdc (1.6.2-1ubuntu5 Ubuntu:13.04/raring [amd64])
Inst libfontembed1 (1.0.34-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libqpdf10 (4.0.1-2 Ubuntu:13.04/raring [amd64])
Inst fonts-freefont-ttf (20120503-1 Ubuntu:13.04/raring [all])
Inst fonts-liberation (1.07.2-6ubuntu1 Ubuntu:13.04/raring [all])
Inst cups-filters (1.0.34-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst cups (1.6.2-1ubuntu5 Ubuntu:13.04/raring [amd64])
Inst sgml-data (2.0.8 Ubuntu:13.04/raring [all])
Inst docbook-xml (4.5-7.1 Ubuntu:13.04/raring [all])
Inst humanity-icon-theme (0.6.2 Ubuntu:13.04/raring [all]) []
Inst gnome-icon-theme (3.6.2-0ubuntu1 Ubuntu:13.04/raring [all])
Inst gnome-icon-theme-full (3.6.2-0ubuntu1 Ubuntu:13.04/raring [all])
Inst elementary-icon-theme (2.7.1-0ubuntu6 Ubuntu:13.04/raring [all])
Inst fonts-kacst (2.01+mry-9 Ubuntu:13.04/raring [all])
Inst fonts-kacst-one (5.0+svn11846-6 Ubuntu:13.04/raring [all])
Inst fonts-nanum (3.020-2 Ubuntu:13.04/raring [all])
Inst fonts-takao-pgothic (003.02.01-7ubuntu3 Ubuntu:13.04/raring [all])
Inst foomatic-filters (4.0.17-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libcrack2 (2.8.22-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libpwquality1 (1.1.1-1 Ubuntu:13.04/raring [amd64])
Inst gnome-disk-utility (3.6.1-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gnome-menus (3.6.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libgpm2 (1.20.4-6ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libaa1 (1.4p5-40 Ubuntu:13.04/raring [amd64])
Inst libraw1394-11 (2.0.9-1 Ubuntu:13.04/raring [amd64])
Inst libavc1394-0 (0.5.4-2 Ubuntu:13.04/raring [amd64])
Inst libdv4 (1.0.0-6 Ubuntu:13.04/raring [amd64])
Inst libgstreamer0.10-0 (0.10.36-1ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libgstreamer-plugins-base0.10-0 (0.10.36-1.1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libiec61883-0 (1.2.0-0.1ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libshout3 (2.3.1-1ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libtag1-vanilla (1.8-1 Ubuntu:13.04/raring [amd64])
Inst libtag1c2a (1.8-1 Ubuntu:13.04/raring [amd64])
Inst libcdparanoia0 (3.10.2+debian-11 Ubuntu:13.04/raring [amd64])
Inst libvisual-0.4-0 (0.4.0-5 Ubuntu:13.04/raring [amd64])
Inst gstreamer0.10-plugins-base (0.10.36-1.1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gstreamer0.10-plugins-good (0.10.31-3+nmu1ubuntu2 Ubuntu:13.04/raring [amd64])
Inst gvfs-bin (1.16.1-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libaacs0 (0.6.0-1 Ubuntu:13.04/raring [amd64])
Inst libaspell15 (0.60.7~20110707-1build1 Ubuntu:13.04/raring [amd64])
Inst libhunspell-1.3-0 (1.3.2-4ubuntu1 Ubuntu:13.04/raring [amd64])
Inst aspell (0.60.7~20110707-1build1 Ubuntu:13.04/raring [amd64])
Inst aspell-en (7.1-0-1 Ubuntu:13.04/raring [all])
Inst hunspell-en-us (20070829-4ubuntu3 Ubuntu:13.04/raring [all])
Inst libenchant1c2a (1.6.0-7build1 Ubuntu:13.04/raring [amd64])
Inst libgsf-1-common (1.14.26-1ubuntu1 Ubuntu:13.04/raring [all])
Inst libgsf-1-114 (1.14.26-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libxslt1.1 (1.1.27-1ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libyajl2 (2.0.4-2 Ubuntu:13.04/raring [amd64])
Inst libraptor2-0 (2.0.8-2 Ubuntu:13.04/raring [amd64])
Inst libmhash2 (0.9.9.9-1.1 Ubuntu:13.04/raring [amd64])
Inst librasqal3 (0.9.29-1 Ubuntu:13.04/raring [amd64])
Inst librdf0 (1.0.16-1 Ubuntu:13.04/raring [amd64])
Inst libwv-1.2-4 (1.2.9-3 Ubuntu:13.04/raring [amd64])
Inst libabiword-2.9 (2.9.2+svn20120603-8 Ubuntu:13.04/raring [amd64])
Inst libaccounts-glib0 (1.8-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libqtcore4 (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Inst libqt4-xml (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Inst libaccounts-qt1 (1.6bzr13.02.27-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libindicator7 (12.10.2daily13.04.10-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libappindicator1 (12.10.1daily13.04.15-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libindicator3-7 (12.10.2daily13.04.10-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libappindicator3-1 (12.10.1daily13.04.15-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libart-2.0-2 (2.3.21-2 Ubuntu:13.04/raring [amd64])
Inst libspeexdsp1 (1.2~rc1-7ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libasound2-plugins (1.0.25-2ubuntu3 Ubuntu:13.04/raring [amd64])
Inst libaudclient2 (3.3.4-1 Ubuntu:13.04/raring [amd64])
Inst libaudio2 (1.9.3-5 Ubuntu:13.04/raring [amd64])
Inst libavahi-core7 (0.6.31-1ubuntu3 Ubuntu:13.04/raring [amd64])
Inst libgeoclue0 (0.12.99-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libnm-util2 (0.9.8.0-0ubuntu6 Ubuntu:13.04/raring [amd64])
Inst libnm-glib4 (0.9.8.0-0ubuntu6 Ubuntu:13.04/raring [amd64])
Inst geoclue (0.12.99-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst geoclue-ubuntu-geoip (1.0.1-0ubuntu4 Ubuntu:13.04/raring [amd64])
Inst libjson-glib-1.0-0 (0.15.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libmessaging-menu0 (12.10.6daily13.04.09-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libtelepathy-glib0 (0.20.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libdee-1.0-4 (1.2.3~daily13.03.13.1-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libunity-protocol-private0 (6.90.2daily13.04.05-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libunity-common (6.90.2daily13.04.05-0ubuntu1 Ubuntu:13.04/raring [all])
Inst libunity9 (6.90.2daily13.04.05-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libwnck-3-common (3.4.5-0ubuntu1 Ubuntu:13.04/raring [all])
Inst libwnck-3-0 (3.4.5-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst unity-webapps-service (2.5.0~daily13.03.18-0ubuntu1 Ubuntu:13.04/raring [amd64]) []
Inst libpackagekit-glib2-14 (0.7.6-3ubuntu1 Ubuntu:13.04/raring [amd64]) []
Inst libunity-webapps0 (2.5.0~daily13.03.18-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst bamfdaemon (0.4.0daily13.04.03-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libbamf3-1 (0.4.0daily13.04.03-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libbluray1 (1:0.2.3-1 Ubuntu:13.04/raring [amd64])
Inst libcolumbus0-0-common (0.4.0daily13.04.16~13.04-0ubuntu1 Ubuntu:13.04/raring [all])
Inst libcolumbus0-0 (0.4.0daily13.04.16~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libcurl3 (7.29.0-1ubuntu3 Ubuntu:13.04/raring [amd64])
Inst libqt4-dbus (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Inst liblcms1 (1.19.dfsg-1.2ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libmng1 (1.0.10-3build1 Ubuntu:13.04/raring [amd64])
Inst libqt4-network (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Inst libqt4-script (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Inst libqt4-sql (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Inst libqt4-xmlpatterns (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Inst libqt4-declarative (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64]) []
Inst libqtgui4 (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Inst libdbusmenu-qt2 (0.9.2daily13.03.28-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libdbusmenu-qt5 (0.9.2daily13.03.28-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst tsconf (1.0-11 Ubuntu:13.04/raring [all])
Inst libts-0.0-0 (1.0-11 Ubuntu:13.04/raring [amd64])
Inst libdirectfb-1.2-9 (1.2.10.0-5 Ubuntu:13.04/raring [amd64])
Inst libdiscid0 (0.2.2-3build1 Ubuntu:13.04/raring [amd64])
Inst libdjvulibre-text (3.5.25.3-3 Ubuntu:13.04/raring [all])
Inst libdjvulibre21 (3.5.25.3-3 Ubuntu:13.04/raring [amd64])
Inst libdvdread4 (4.2.0+20121016-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libdvdnav4 (4.2.0+20130225-1 Ubuntu:13.04/raring [amd64])
Inst libelfg0 (0.8.13-4~1 Ubuntu:13.04/raring [amd64])
Inst libmailtools-perl (2.09-1 Ubuntu:13.04/raring [all])
Inst libdigest-hmac-perl (1.03+dfsg-1 Ubuntu:13.04/raring [all])
Inst libnet-ip-perl (1.26-1 Ubuntu:13.04/raring [all])
Inst libsocket6-perl (0.23-1build3 Ubuntu:13.04/raring [amd64])
Inst libio-socket-inet6-perl (2.69-2 Ubuntu:13.04/raring [all])
Inst libnet-dns-perl (0.68-1.1 Ubuntu:13.04/raring [amd64])
Inst libnet-domain-tld-perl (1.69-1 Ubuntu:13.04/raring [all])
Inst libemail-valid-perl (0.190-1 Ubuntu:13.04/raring [all])
Inst libevent-2.0-5 (2.0.19-stable-3 Ubuntu:13.04/raring [amd64])
Inst libxfce4util-common (4.10.0-1 Ubuntu:13.04/raring [all])
Inst libxfce4util6 (4.10.0-1 Ubuntu:13.04/raring [amd64])
Inst xfconf (4.10.0-1 Ubuntu:13.04/raring [amd64])
Inst libxfconf-0-2 (4.10.0-1 Ubuntu:13.04/raring [amd64])
Inst xfce-keyboard-shortcuts (4.10.0-1 Ubuntu:13.04/raring [all])
Inst libxfce4ui-1-0 (4.10.0-1 Ubuntu:13.04/raring [amd64])
Inst libexo-common (0.10.2-1 Ubuntu:13.04/raring [all])
Inst libexo-helpers (0.10.2-1 Ubuntu:13.04/raring [amd64])
Inst libexo-1-0 (0.10.2-1 Ubuntu:13.04/raring [amd64])
Inst libgssdp-1.0-3 (0.14.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libgupnp-1.0-4 (0.20.0-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libgupnp-igd-1.0-4 (0.2.1-2ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libnice10 (0.1.3-1 Ubuntu:13.04/raring [amd64])
Inst gstreamer0.10-nice (0.1.3-1 Ubuntu:13.04/raring [amd64])
Inst libfarstream-0.1-0 (0.1.2-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libgomp1 (4.7.3-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libfftw3-single3 (3.3.3-2ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libframe6 (2.5.0daily13.03.12-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libfreerdp1 (1.0.1-2ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libfreerdp-plugins-standard (1.0.1-2ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libfs6 (2:1.0.4-1 Ubuntu:13.04/raring [amd64])
Inst libgail-3-0 (3.6.4-0ubuntu8 Ubuntu:13.04/raring [amd64])
Inst libunistring0 (0.9.3-5build1 Ubuntu:13.04/raring [amd64])
Inst libgettextpo0 (0.18.1.1-10ubuntu3 Ubuntu:13.04/raring [amd64])
Inst libglew1.8 (1.9.0.is.1.8.0-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libglewmx1.8 (1.9.0.is.1.8.0-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libglib2.0-data (2.36.0-1ubuntu2 Ubuntu:13.04/raring [all])
Inst libglib2.0-bin (2.36.0-1ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libglibmm-2.4-1c2a (2.35.9-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libpulse-mainloop-glib0 (1:3.0-0ubuntu6 Ubuntu:13.04/raring [amd64])
Inst libgmlib1 (1.0.8-1 Ubuntu:13.04/raring [amd64])
Inst libgmtk1-data (1.0.8-1 Ubuntu:13.04/raring [all])
Inst libgmtk1 (1.0.8-1 Ubuntu:13.04/raring [amd64])
Inst librest-0.7-0 (0.7.90-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libjavascriptcoregtk-3.0-0 (1.10.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libgstreamer1.0-0 (1.0.6-1 Ubuntu:13.04/raring [amd64])
Inst libgstreamer-plugins-base1.0-0 (1.0.6-1 Ubuntu:13.04/raring [amd64])
Inst libwebkitgtk-3.0-common (1.10.2-0ubuntu1 Ubuntu:13.04/raring [all])
Inst libwebkitgtk-3.0-0 (1.10.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libgoa-1.0-common (3.6.2-1ubuntu1 Ubuntu:13.04/raring [all])
Inst libgoa-1.0-0 (3.6.2-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libgpod4 (0.8.2-7ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libgrail6 (3.1.0daily13.02.26-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libgeis1 (2.2.15daily13.04.03-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libgrip0 (0.3.6daily13.02.26-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libgutenprint2 (5.2.9-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libgxps2 (0.2.2-2ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libibus-1.0-0 (1.4.2-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libido3-0.1-0 (12.10.3daily13.03.01-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst liblua5.1-0 (5.1.5-4 Ubuntu:13.04/raring [amd64])
Inst libmowgli2 (1.0.0-1 Ubuntu:13.04/raring [amd64])
Inst mysql-common (5.5.31-0ubuntu0.13.04.1 Ubuntu:13.04/raring-updates [all])
Inst libmysqlclient18 (5.5.31-0ubuntu0.13.04.1 Ubuntu:13.04/raring-updates [amd64])
Inst libnl-route-3-200 (3.2.16-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libnux-4.0-common (4.0.1daily13.04.17~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libglu1-mesa (9.0.0-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libnux-4.0-0 (4.0.1daily13.04.17~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst liboauth0 (1.0.1-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libpam-xdg-support (0.2-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libpcsclite1 (1.8.6-3ubuntu1b1 Ubuntu:13.04/raring [amd64])
Inst libpoppler-glib8 (0.20.5-1ubuntu3 Ubuntu:13.04/raring [amd64])
Inst libportaudio2 (19+svn20111121-1build1 Ubuntu:13.04/raring [amd64])
Inst libpostproc52 (6:0.8.6-1ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libpulsedsp (1:3.0-0ubuntu6 Ubuntu:13.04/raring [amd64])
Inst libpython2.7 (2.7.4-2ubuntu3 Ubuntu:13.04/raring [amd64])
Inst libpython3.3 (3.3.1-1ubuntu5 Ubuntu:13.04/raring [amd64])
Inst libqjson0 (0.8.1-1 Ubuntu:13.04/raring [amd64])
Inst libqt4-opengl (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Inst libqt4-sql-mysql (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Inst libqt4-sql-sqlite (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Inst libqt4-test (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Inst libqtwebkit4 (2.3.0-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libreadline5 (5.2+dfsg-1 Ubuntu:13.04/raring [amd64])
Inst libsensors4 (1:3.3.2-2ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libsignon-extension1 (8.49-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libsignon-plugins-common1 (8.49-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst session-migration (0.2 Ubuntu:13.04/raring [amd64])
Inst signond (8.49-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libsignon-glib1 (1.9-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libspectre1 (0.2.7-2 Ubuntu:13.04/raring [amd64])
Inst libswscale2 (6:0.8.6-1ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libsysfs2 (2.1.0+repack-2 Ubuntu:13.04/raring [amd64])
Inst libunity-misc4 (4.0.5daily13.02.26-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libvdpau1 (0.4.1-8 Ubuntu:13.04/raring [amd64])
Inst libwacom-common (0.7-1 Ubuntu:13.04/raring [all])
Inst libwacom2 (0.7-1 Ubuntu:13.04/raring [amd64])
Inst libwmf0.2-7 (0.2.8.4-10.3ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libx86-1 (1.1+ds1-10 Ubuntu:13.04/raring [amd64])
Inst libxp6 (1:1.0.1-2build1 Ubuntu:13.04/raring [amd64])
Inst libxvidcore4 (2:1.3.2-9 Ubuntu:13.04/raring [amd64])
Inst lightdm (1.6.0-0ubuntu2.1 Ubuntu:13.04/raring-updates [amd64])
Inst libxklavier16 (5.2.1-1ubuntu2 Ubuntu:13.04/raring [amd64])
Inst liblightdm-gobject-1-0 (1.6.0-0ubuntu2.1 Ubuntu:13.04/raring-updates [amd64])
Inst lightdm-gtk-greeter (1.5.1-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gtk3-engines-unico (1.0.3daily12.12.12-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst lubuntu-artwork-13-04 (0.38.1 Ubuntu:13.04/raring [all])
Inst lubuntu-lxpanel-icons (0.38.1 Ubuntu:13.04/raring [all])
Inst lubuntu-artwork (0.38.1 Ubuntu:13.04/raring [all])
Inst gnome-icon-theme-symbolic (3.6.2-0ubuntu1 Ubuntu:13.04/raring [all])
Inst lubuntu-icon-theme (0.38.1 Ubuntu:13.04/raring [all])
Inst ttf-ubuntu-font-family (0.80-0ubuntu5 Ubuntu:13.04/raring [all])
Inst lubuntu-default-settings (0.31 Ubuntu:13.04/raring [all])
Inst wpasupplicant (1.0-3ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libnetfilter-conntrack3 (1.0.1-1 Ubuntu:13.04/raring [amd64])
Inst dnsmasq-base (2.65-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst iputils-arping (3:20101006-3ubuntu1 Ubuntu:13.04/raring [amd64])
Inst network-manager (0.9.8.0-0ubuntu6 Ubuntu:13.04/raring [amd64])
Inst libgnome-bluetooth11 (3.6.1-0ubuntu3 Ubuntu:13.04/raring [amd64])
Inst libnm-glib-vpn1 (0.9.8.0-0ubuntu6 Ubuntu:13.04/raring [amd64])
Inst libnm-gtk-common (0.9.8.0-1ubuntu2 Ubuntu:13.04/raring [all])
Inst libnm-gtk0 (0.9.8.0-1ubuntu2 Ubuntu:13.04/raring [amd64])
Inst network-manager-gnome (0.9.8.0-1ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libopts25 (1:5.17.1-1ubuntu2 Ubuntu:13.04/raring [amd64])
Inst ntp (1:4.2.6.p5+dfsg-2ubuntu1 Ubuntu:13.04/raring [amd64])
Inst nux-tools (4.0.1daily13.04.17~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst pcmciautils (018-8 Ubuntu:13.04/raring [amd64])
Inst python-gi (3.8.0-2 Ubuntu:13.04/raring [amd64])
Inst samba-common (2:3.6.9-1ubuntu1 Ubuntu:13.04/raring [all])
Inst samba-common-bin (2:3.6.9-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst smbclient (2:3.6.9-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libcompfaceg1 (1:1.5.2-5 Ubuntu:13.04/raring [amd64])
Inst libpth20 (2.0.7-16ubuntu4 Ubuntu:13.04/raring [amd64])
Inst libgpgme11 (1.2.0-1.4ubuntu4 Ubuntu:13.04/raring [amd64])
Inst libgtkspell0 (2.0.16-1ubuntu6 Ubuntu:13.04/raring [amd64])
Inst libonig2 (5.9.1-1 Ubuntu:13.04/raring [amd64])
Inst libpisock9 (0.12.5-5ubuntu1 Ubuntu:13.04/raring [amd64])
Inst sylpheed (3.3.0-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst sylpheed-plugins (3.3.0-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst liburi-perl (1.60-1 Ubuntu:13.04/raring [all])
Inst libencode-locale-perl (1.03-1 Ubuntu:13.04/raring [all])
Inst libhttp-date-perl (6.02-1 Ubuntu:13.04/raring [all])
Inst libfile-listing-perl (6.04-1 Ubuntu:13.04/raring [all])
Inst libhtml-tagset-perl (3.20-2 Ubuntu:13.04/raring [all])
Inst libhtml-parser-perl (3.69-2 Ubuntu:13.04/raring [amd64])
Inst libhtml-tree-perl (5.02-1 Ubuntu:13.04/raring [all])
Inst liblwp-mediatypes-perl (6.02-1 Ubuntu:13.04/raring [all])
Inst libhttp-message-perl (6.03-1 Ubuntu:13.04/raring [all])
Inst libhttp-cookies-perl (6.00-2 Ubuntu:13.04/raring [all])
Inst libhttp-negotiate-perl (6.00-2 Ubuntu:13.04/raring [all])
Inst libnet-ssleay-perl (1.48-1 Ubuntu:13.04/raring [amd64])
Inst libio-socket-ssl-perl (1.76-2ubuntu1 Ubuntu:13.04/raring [all])
Inst libnet-http-perl (6.03-2 Ubuntu:13.04/raring [all])
Inst liblwp-protocol-https-perl (6.03-1 Ubuntu:13.04/raring [all]) []
Inst libwww-robotrules-perl (6.01-1 Ubuntu:13.04/raring [all]) []
Inst libwww-perl (6.04-1 Ubuntu:13.04/raring [all])
Inst libxml-parser-perl (2.41-1build2 Ubuntu:13.04/raring [amd64])
Inst libxml-twig-perl (1:3.39-1ubuntu1 Ubuntu:13.04/raring [all])
Inst libnet-dbus-perl (1.0.0-2 Ubuntu:13.04/raring [amd64])
Inst system-tools-backends (2.10.2-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst python3-xkit (0.5.0ubuntu1 Ubuntu:13.04/raring [all])
Inst dialog (1.1-20120215-3 Ubuntu:13.04/raring [amd64])
Inst alsa-utils (1.0.25-4ubuntu2 Ubuntu:13.04/raring [amd64])
Inst ubuntu-drivers-common (1:0.2.76 Ubuntu:13.04/raring [amd64])
Inst unity-common (7.0.0daily13.04.18~13.04-0ubuntu1 Ubuntu:13.04/raring [all])
Inst patch (2.6.1-3ubuntu2 Ubuntu:13.04/raring [amd64])
Inst update-notifier-common (0.134 Ubuntu:13.04/raring [all])
Inst libwhoopsie0 (0.2.15 Ubuntu:13.04/raring [amd64])
Inst whoopsie (0.2.15 Ubuntu:13.04/raring [amd64])
Inst dconf-tools (0.16.0-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gnome-desktop3-data (3.6.3-0ubuntu1 Ubuntu:13.04/raring [all])
Inst libgnome-desktop-3-4 (3.6.3-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libgnomekbd-common (3.6.0-0ubuntu2 Ubuntu:13.04/raring [all])
Inst libgnomekbd8 (3.6.0-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libupower-glib1 (0.9.20-1 Ubuntu:13.04/raring [amd64])
Inst nautilus-data (1:3.6.3-0ubuntu16 Ubuntu:13.04/raring [all])
Inst gnome-settings-daemon (3.6.4-0ubuntu8 Ubuntu:13.04/raring [amd64])
Inst libenca0 (1.14-2 Ubuntu:13.04/raring [amd64])
Inst libass4 (0.10.1-1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-dee-1.0 (1.2.3~daily13.03.13.1-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-freedesktop (1.36.0-1 Ubuntu:13.04/raring [amd64])
Inst libcamel-1.2-40 (3.6.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst evolution-data-server-common (3.6.4-0ubuntu1 Ubuntu:13.04/raring [all])
Inst libedataserver-1.2-17 (3.6.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-edataserver-1.2 (3.6.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libebook-1.2-14 (3.6.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-ebook-1.2 (3.6.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-gdkpixbuf-2.0 (2.28.0-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-networkmanager-1.0 (0.9.8.0-0ubuntu6 Ubuntu:13.04/raring [amd64])
Inst gir1.2-notify-0.7 (0.7.5-2 Ubuntu:13.04/raring [amd64])
Inst gir1.2-signon-1.0 (1.9-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-soup-2.4 (2.40.3-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-accounts-1.0 (1.8-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst python3-pkg-resources (0.6.34-0ubuntu1 Ubuntu:13.04/raring [all])
Inst python3-crypto (2.6-4 Ubuntu:13.04/raring [amd64])
Inst python3-oauthlib (0.3.7-0ubuntu1 Ubuntu:13.04/raring [all])
Inst friends-dispatcher (0.1.3daily13.04.17.1~13.04-0ubuntu1 Ubuntu:13.04/raring [all])
Inst libfriends0 (0.1.2daily13.03.26-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libgstreamer-plugins-good1.0-0 (1.0.6-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libguess1 (1.1-1 Ubuntu:13.04/raring [amd64])
Inst libquvi-scripts (0.4.8-3 Ubuntu:13.04/raring [all])
Inst libquvi7 (0.4.1-1 Ubuntu:13.04/raring [amd64])
Inst libsystemd-daemon0 (198-0ubuntu11 Ubuntu:13.04/raring [amd64])
Inst systemd-services (198-0ubuntu11 Ubuntu:13.04/raring [amd64])
Inst usb-modeswitch-data (20120815-2 Ubuntu:13.04/raring [all])
Inst usb-modeswitch (1.2.3+repack0-1ubuntu3 Ubuntu:13.04/raring [amd64])
Inst libloudmouth1-0 (1.4.3-9 Ubuntu:13.04/raring [amd64])
Inst libots0 (0.5.0-2.1 Ubuntu:13.04/raring [amd64])
Inst libtidy-0.99-0 (20091223cvs-1.2 Ubuntu:13.04/raring [amd64])
Inst libwpd-0.9-9 (0.9.6-2 Ubuntu:13.04/raring [amd64])
Inst libwpg-0.2-2 (0.2.1-1build1 Ubuntu:13.04/raring [amd64])
Inst libwps-0.2-2 (0.2.7-1 Ubuntu:13.04/raring [amd64])
Inst abiword-common (2.9.2+svn20120603-8 Ubuntu:13.04/raring [all])
Inst abiword (2.9.2+svn20120603-8 Ubuntu:13.04/raring [amd64])
Inst link-grammar-dictionaries-en (4.7.4-2 Ubuntu:13.04/raring [all])
Inst liblink-grammar4 (4.7.4-2 Ubuntu:13.04/raring [amd64])
Inst abiword-plugin-grammar (2.9.2+svn20120603-8 Ubuntu:13.04/raring [amd64])
Inst libgdome2-0 (0.8.1+debian-4.1build1 Ubuntu:13.04/raring [amd64])
Inst libgdome2-cpp-smart0c2a (0.2.6-6build2 Ubuntu:13.04/raring [amd64])
Inst libt1-5 (5.1.2-3.6 Ubuntu:13.04/raring [amd64])
Inst libgtkmathview0c2a (0.8.0-8 Ubuntu:13.04/raring [amd64])
Inst fonts-lyx (2.0.3-3 Ubuntu:13.04/raring [all])
Inst abiword-plugin-mathview (2.9.2+svn20120603-8 Ubuntu:13.04/raring [amd64])
Inst libaccount-plugin-1.0-0 (0.1.6bzr13.04.05-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst signon-keyring-extension (0.4daily12.12.06-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libsignon-qt1 (8.49-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst signon-ui (0.14-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst signon-plugin-oauth2 (0.15-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst account-plugin-generic-oauth (0.10bzr13.03.26-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst unity-asset-pool (0.8.24daily13.04.24-0ubuntu1 Ubuntu:13.04/raring [all])
Inst account-plugin-facebook (0.10bzr13.03.26-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst account-plugin-flickr (0.10bzr13.03.26-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst account-plugin-google (0.10bzr13.03.26-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst account-plugin-twitter (0.10bzr13.03.26-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst pm-utils (1.4.1-9git1 Ubuntu:13.04/raring [all])
Inst acpi-support (0.141 Ubuntu:13.04/raring [amd64])
Inst linux-sound-base (1.0.25+dfsg-0ubuntu4 Ubuntu:13.04/raring [all])
Inst alsa-base (1.0.25+dfsg-0ubuntu4 Ubuntu:13.04/raring [all])
Inst anacron (2.3-19ubuntu2 Ubuntu:13.04/raring [amd64])
Inst apg (2.2.3.dfsg.1-2build1 Ubuntu:13.04/raring [amd64])
Inst app-install-data (13.04.3 Ubuntu:13.04/raring [all])
Inst appmenu-qt (0.2.7daily13.03.28-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst python3-problem-report (2.9.2-0ubuntu8 Ubuntu:13.04/raring [all])
Inst python3-apport (2.9.2-0ubuntu8 Ubuntu:13.04/raring [all])
Inst apport (2.9.2-0ubuntu8 Ubuntu:13.04/raring [all])
Inst gir1.2-atk-1.0 (2.8.0-1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-pango-1.0 (1.32.5-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-gtk-3.0 (3.6.4-0ubuntu8 Ubuntu:13.04/raring [amd64])
Inst gir1.2-wnck-3.0 (3.4.5-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst apport-gtk (2.9.2-0ubuntu8 Ubuntu:13.04/raring [all])
Inst apport-symptoms (0.19 Ubuntu:13.04/raring [all])
Inst apturl-common (0.5.2ubuntu1 Ubuntu:13.04/raring [amd64])
Inst unattended-upgrades (0.79.3ubuntu7 Ubuntu:13.04/raring [all])
Inst python3-software-properties (0.92.17 Ubuntu:13.04/raring [all])
Inst python3-defer (1.0.6-2 Ubuntu:13.04/raring [all])
Inst python3-aptdaemon (1.0-0ubuntu9 Ubuntu:13.04/raring [all])
Inst libvte-2.90-common (1:0.34.2-0ubuntu2 Ubuntu:13.04/raring [all])
Inst libvte-2.90-9 (1:0.34.2-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst gir1.2-vte-2.90 (1:0.34.2-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst aptdaemon-data (1.0-0ubuntu9 Ubuntu:13.04/raring [all])
Inst python3-aptdaemon.gtk3widgets (1.0-0ubuntu9 Ubuntu:13.04/raring [all])
Inst software-properties-common (0.92.17 Ubuntu:13.04/raring [all])
Inst software-properties-gtk (0.92.17 Ubuntu:13.04/raring [all])
Inst gir1.2-javascriptcoregtk-3.0 (1.10.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-webkit-3.0 (1.10.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst apturl (0.5.2ubuntu1 Ubuntu:13.04/raring [amd64])
Inst audacious (3.3.4-1 Ubuntu:13.04/raring [amd64])
Inst libdaemon0 (0.14-2build1 Ubuntu:13.04/raring [amd64])
Inst avahi-daemon (0.6.31-1ubuntu3 Ubuntu:13.04/raring [amd64])
Inst avahi-utils (0.6.31-1ubuntu3 Ubuntu:13.04/raring [amd64])
Inst binutils (2.23.2-2ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libopenobex1 (1.5-2build2 Ubuntu:13.04/raring [amd64])
Inst obex-data-server (0.4.6-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst python-cairo (1.8.8-1ubuntu4 Ubuntu:13.04/raring [amd64])
Inst python-gobject-2 (2.28.6-11 Ubuntu:13.04/raring [amd64])
Inst python-gtk2 (2.24.0-3ubuntu1 Ubuntu:13.04/raring [amd64])
Inst python-dbus-dev (1.1.1-1ubuntu3 Ubuntu:13.04/raring [all])
Inst python-dbus (1.1.1-1ubuntu3 Ubuntu:13.04/raring [amd64])
Inst python-gobject (3.8.0-2 Ubuntu:13.04/raring [all])
Inst python-notify (0.1.1-3ubuntu1 Ubuntu:13.04/raring [amd64])
Inst xfce4-notifyd (0.2.2-3 Ubuntu:13.04/raring [amd64])
Inst blueman (1.23-0ubuntu4 Ubuntu:13.04/raring [amd64])
Inst bluez-alsa (4.101-0ubuntu8b1 Ubuntu:13.04/raring [amd64])
Inst bluez-cups (4.101-0ubuntu8b1 Ubuntu:13.04/raring [amd64])
Inst brasero-common (3.6.1-0ubuntu2 Ubuntu:13.04/raring [all])
Inst compiz-core (1:0.9.9~daily13.04.18.1~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libdecoration0 (1:0.9.9~daily13.04.18.1~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst compiz-plugins-default (1:0.9.9~daily13.04.18.1~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libprotobuf7 (2.4.1-3ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libcompizconfig0 (1:0.9.9~daily13.04.18.1~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst metacity-common (1:2.34.13-0ubuntu1 Ubuntu:13.04/raring [all])
Inst libmetacity-private0a (1:2.34.13-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst compiz-gnome (1:0.9.9~daily13.04.18.1~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst compiz (1:0.9.9~daily13.04.18.1~13.04-0ubuntu1 Ubuntu:13.04/raring [all])
Inst cracklib-runtime (2.8.22-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst cups-browsed (1.0.34-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst ghostscript-cups (9.07~dfsg2-0ubuntu3 Ubuntu:13.04/raring [amd64])
Inst printer-driver-gutenprint (5.2.9-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst cups-driver-gutenprint (5.2.9-1ubuntu1 Ubuntu:13.04/raring [all])
Inst dc (1.06.95-4ubuntu1 Ubuntu:13.04/raring [amd64])
Inst diffstat (1.55-4 Ubuntu:13.04/raring [amd64])
Inst dmz-cursor-theme (0.4.3 Ubuntu:13.04/raring [all])
Inst genisoimage (9:1.1.11-2ubuntu3 Ubuntu:13.04/raring [amd64])
Inst growisofs (7.1-10build1 Ubuntu:13.04/raring [amd64])
Inst dvd+rw-tools (7.1-10build1 Ubuntu:13.04/raring [amd64])
Inst enchant (1.6.0-7build1 Ubuntu:13.04/raring [amd64])
Inst libkpathsea6 (2012.20120628-4 Ubuntu:13.04/raring [amd64])
Inst libevdocument3-4 (3.6.1-1ubuntu3 Ubuntu:13.04/raring [amd64])
Inst libevview3-3 (3.6.1-1ubuntu3 Ubuntu:13.04/raring [amd64])
Inst libnautilus-extension1a (1:3.6.3-0ubuntu16 Ubuntu:13.04/raring [amd64])
Inst evince-common (3.6.1-1ubuntu3 Ubuntu:13.04/raring [all])
Inst evince (3.6.1-1ubuntu3 Ubuntu:13.04/raring [amd64])
Inst libebackend-1.2-5 (3.6.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libical0 (0.48-2 Ubuntu:13.04/raring [amd64])
Inst libecal-1.2-15 (3.6.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libedata-book-1.2-15 (3.6.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libedata-cal-1.2-18 (3.6.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libgdata-common (0.13.2-2svn1 Ubuntu:13.04/raring [all])
Inst libgdata13 (0.13.2-2svn1 Ubuntu:13.04/raring [amd64])
Inst libgweather-common (3.6.2-0ubuntu1 Ubuntu:13.04/raring [all])
Inst libgweather-3-1 (3.6.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst evolution-data-server (3.6.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libffmpegthumbnailer4 (2.0.8-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst ffmpegthumbnailer (2.0.8-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst zip (3.0-6ubuntu1 Ubuntu:13.04/raring [amd64])
Inst file-roller (3.6.3-1ubuntu4 Ubuntu:13.04/raring [amd64])
Inst firefox (20.0+build1-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst firefox-globalmenu (20.0+build1-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst fonts-khmeros-core (5.0-5ubuntu1 Ubuntu:13.04/raring [all])
Inst fonts-lao (0.0.20060226-8 Ubuntu:13.04/raring [all])
Inst fonts-lklug-sinhala (0.6-2 Ubuntu:13.04/raring [all])
Inst fonts-sil-abyssinica (1.200-3 Ubuntu:13.04/raring [all])
Inst fonts-sil-padauk (2.80-1 Ubuntu:13.04/raring [all])
Inst fonts-tlwg-garuda (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Inst fonts-tlwg-kinnari (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Inst fonts-tlwg-loma (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Inst fonts-tlwg-mono (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Inst fonts-tlwg-norasi (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Inst fonts-tlwg-purisa (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Inst fonts-tlwg-sawasdee (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Inst fonts-tlwg-typewriter (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Inst fonts-tlwg-typist (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Inst fonts-tlwg-typo (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Inst fonts-tlwg-umpush (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Inst fonts-tlwg-waree (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Inst fonts-thai-tlwg (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Inst fonts-tibetan-machine (1.901b-4 Ubuntu:13.04/raring [all])
Inst foomatic-db-compressed-ppds (20130308-0ubuntu2 Ubuntu:13.04/raring [all])
Inst freerdp-x11 (1.0.1-2ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gdb (7.6~20130417-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gdebi-core (0.9~exp2 Ubuntu:13.04/raring [all])
Inst gdebi (0.9~exp2 Ubuntu:13.04/raring [all])
Inst libjs-jquery (1.7.2+debian-1ubuntu1 Ubuntu:13.04/raring [all])
Inst libgda-5.0-common (5.0.3-2ubuntu1 Ubuntu:13.04/raring [all])
Inst libgda-5.0-4 (5.0.3-2ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libmusicbrainz3-6 (3.0.2-2.1 Ubuntu:13.04/raring [amd64])
Inst libdca0 (0.0.5-5 Ubuntu:13.04/raring [amd64])
Inst mplayer2 (2.0-554-gf63dbad-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gnome-mplayer (1.0.8-1 Ubuntu:13.04/raring [amd64])
Inst gecko-mediaplayer (1.0.8-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libasprintf-dev (0.18.1.1-10ubuntu3 Ubuntu:13.04/raring [amd64])
Inst libgettextpo-dev (0.18.1.1-10ubuntu3 Ubuntu:13.04/raring [amd64])
Inst gettext (0.18.1.1-10ubuntu3 Ubuntu:13.04/raring [amd64])
Inst ghostscript-x (9.07~dfsg2-0ubuntu3 Ubuntu:13.04/raring [amd64])
Inst gir1.2-dbusmenu-glib-0.4 (12.10.3daily13.02.01-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-goa-1.0 (3.6.2-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-gdata-0.0 (0.13.2-2svn1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-gnomebluetooth-1.0 (3.6.1-0ubuntu3 Ubuntu:13.04/raring [amd64])
Inst gir1.2-gstreamer-1.0 (1.0.6-1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-gst-plugins-base-1.0 (1.0.6-1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-messagingmenu-1.0 (12.10.6daily13.04.09-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-packagekitglib-1.0 (0.7.6-3ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libpeas-common (1.6.2-0ubuntu1 Ubuntu:13.04/raring [all])
Inst libpeas-1.0-0 (1.6.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libgmime-2.6-0 (2.6.13-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libtotem-plparser17 (3.4.4-1 Ubuntu:13.04/raring [amd64])
Inst librhythmbox-core6 (2.98-0ubuntu5 Ubuntu:13.04/raring [amd64])
Inst gir1.2-rb-3.0 (2.98-0ubuntu5 Ubuntu:13.04/raring [amd64])
Inst gir1.2-unity-5.0 (6.90.2daily13.04.05-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gkbd-capplet (3.6.0-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst obexd-client (0.46-1ubuntu3 Ubuntu:13.04/raring [amd64])
Inst gnome-bluetooth (3.6.1-0ubuntu3 Ubuntu:13.04/raring [amd64])
Inst libgnome-control-center1 (1:3.6.3-0ubuntu24 Ubuntu:13.04/raring [amd64])
Inst libgnome-menu-3-0 (3.6.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gnome-control-center-data (1:3.6.3-0ubuntu24 Ubuntu:13.04/raring [all])
Inst gnome-control-center (1:3.6.3-0ubuntu24 Ubuntu:13.04/raring [amd64])
Inst gnome-control-center-signon (0.1.6bzr13.04.05-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gnome-control-center-unity (1.2daily13.04.09-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gnome-desktop-data (1:2.32.1-2ubuntu1 Ubuntu:13.04/raring [all])
Inst upower (0.9.20-1 Ubuntu:13.04/raring [amd64])
Inst gnome-session-bin (3.6.2-0ubuntu5 Ubuntu:13.04/raring [amd64])
Inst liboobs-1-5 (3.0.0-1 Ubuntu:13.04/raring [amd64])
Inst gnome-system-tools (3.0.0-2ubuntu2 Ubuntu:13.04/raring [amd64])
Inst gnome-time-admin (3.0.0-2ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libyelp0 (3.6.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst yelp-xsl (3.6.1-1 Ubuntu:13.04/raring [all])
Inst yelp (3.6.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gnome-user-guide (3.6.2-0ubuntu1 Ubuntu:13.04/raring [all])
Inst gnome-user-share (3.0.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libgoffice-0.10-10-common (0.10.1-1ubuntu2 Ubuntu:13.04/raring [all])
Inst libgoffice-0.10-10 (0.10.1-1ubuntu2 Ubuntu:13.04/raring [amd64])
Inst gnumeric-common (1.12.1-1ubuntu1 Ubuntu:13.04/raring [all])
Inst gnumeric (1.12.1-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gnumeric-doc (1.12.1-1ubuntu1 Ubuntu:13.04/raring [all])
Inst gstreamer0.10-pulseaudio (0.10.31-3+nmu1ubuntu2 Ubuntu:13.04/raring [amd64])
Inst gstreamer0.10-x (0.10.36-1.1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gstreamer1.0-plugins-base (1.0.6-1 Ubuntu:13.04/raring [amd64])
Inst gstreamer1.0-plugins-good (1.0.6-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gstreamer1.0-pulseaudio (1.0.6-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gstreamer1.0-x (1.0.6-1 Ubuntu:13.04/raring [amd64])
Inst libgucharmap-2-90-7 (1:3.6.1-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gucharmap (1:3.6.1-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst hardinfo (0.5.1-1.2ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libsnmp-base (5.4.3~dfsg-2.7ubuntu1 Ubuntu:13.04/raring [all])
Inst libperl5.14 (5.14.2-21 Ubuntu:13.04/raring [amd64])
Inst libsnmp15 (5.4.3~dfsg-2.7ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libhpmud0 (3.13.3-1 Ubuntu:13.04/raring [amd64])
Inst libsane-hpaio (3.13.3-1 Ubuntu:13.04/raring [amd64])
Inst hplip-data (3.13.3-1 Ubuntu:13.04/raring [all])
Inst printer-driver-hpcups (3.13.3-1 Ubuntu:13.04/raring [amd64])
Inst python-imaging-compat (1.1.7+2.0.0-1 Ubuntu:13.04/raring [all]) []
Inst python-imaging (1.1.7+2.0.0-1 Ubuntu:13.04/raring [amd64])
Inst python-pexpect (2.4-1 Ubuntu:13.04/raring [all])
Inst python-reportlab (2.6-1 Ubuntu:13.04/raring [all])
Inst hplip (3.13.3-1 Ubuntu:13.04/raring [amd64])
Inst hud (13.04.0daily13.04.03-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst hwdata (0.234-1 Ubuntu:13.04/raring [all])
Inst python-ibus (1.4.2-0ubuntu2 Ubuntu:13.04/raring [all])
Inst python-xdg (0.25-2 Ubuntu:13.04/raring [all])
Inst ibus (1.4.2-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst ibus-gtk (1.4.2-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst ibus-gtk3 (1.4.2-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst zenity-common (3.6.0-0ubuntu1 Ubuntu:13.04/raring [all])
Inst zenity (3.6.0-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst im-config (0.21ubuntu3 Ubuntu:13.04/raring [all])
Inst libpanel-applet-4-0 (1:3.6.2-0ubuntu3 Ubuntu:13.04/raring [amd64])
Inst python3-xdg (0.25-2 Ubuntu:13.04/raring [all])
Inst indicator-applet (12.10.2daily13.03.01-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst indicator-application (12.10.1daily13.01.25-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst indicator-application-gtk2 (12.10.0.1-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst indicator-appmenu (13.01.0daily13.03.28-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libtimezonemap1 (0.4.0 Ubuntu:13.04/raring [amd64])
Inst systemd-shim (2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst indicator-datetime (12.10.3daily13.03.26-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst indicator-messages (12.10.6daily13.04.09-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst indicator-power (12.10.6daily13.03.07-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst indicator-session (12.10.5daily13.03.08-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst indicator-sync (12.10.5daily13.03.28.1-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst intltool-debian (0.35.0+20060710.1 Ubuntu:13.04/raring [all])
Inst kerneloops-daemon (0.12+git20090217-3ubuntu3 Ubuntu:13.04/raring [amd64])
Inst aptdaemon (1.0-0ubuntu9 Ubuntu:13.04/raring [all])
Inst language-selector-gnome (0.110 Ubuntu:13.04/raring [all])
Inst libapt-pkg-perl (0.1.26 Ubuntu:13.04/raring [amd64])
Inst libarchive-zip-perl (1.30-6 Ubuntu:13.04/raring [all])
Inst libburn4 (1.2.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libjte1 (1.19-1build1 Ubuntu:13.04/raring [amd64])
Inst libisofs6 (1.2.6-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libbrasero-media3-1 (3.6.1-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libcairo-perl (1.103-1 Ubuntu:13.04/raring [amd64])
Inst pulseaudio (1:3.0-0ubuntu6 Ubuntu:13.04/raring [amd64])
Inst libcanberra-pulse (0.30-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libclone-perl (0.31-1build4 Ubuntu:13.04/raring [amd64])
Inst libcolamd2.7.1 (1:3.4.0-3ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libdmapsharing-3.0-2 (2.9.15-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libdpkg-perl (1.16.10ubuntu1 Ubuntu:13.04/raring [all])
Inst libfile-copy-recursive-perl (0.38-1 Ubuntu:13.04/raring [all])
Inst libfile-fcntllock-perl (0.14-2 Ubuntu:13.04/raring [amd64])
Inst libfont-afm-perl (1.20-1 Ubuntu:13.04/raring [all])
Inst libglib-perl (3:1.261-1 Ubuntu:13.04/raring [amd64])
Inst libsgutils2-2 (1.33-1build1 Ubuntu:13.04/raring [amd64])
Inst libgpod-common (0.8.2-7ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libpango-perl (1.224-1 Ubuntu:13.04/raring [amd64])
Inst libgtk2-perl (2:1.244-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libhtml-form-perl (6.03-1 Ubuntu:13.04/raring [all])
Inst libhtml-format-perl (2.10-1 Ubuntu:13.04/raring [all])
Inst libhttp-daemon-perl (6.01-1 Ubuntu:13.04/raring [all])
Inst libio-pty-perl (1:1.08-1build3 Ubuntu:13.04/raring [amd64])
Inst libipc-run-perl (0.92-1 Ubuntu:13.04/raring [all])
Inst libmeanwhile1 (1.0.2-4ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libminiupnpc8 (1.6-3ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libnatpmp1 (20110808-3ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libnotify-bin (0.7.5-2 Ubuntu:13.04/raring [amd64])
Inst libnss-mdns (0.10-3.2build1 Ubuntu:13.04/raring [amd64])
Inst libpaper-utils (1.1.24+nmu2ubuntu2 Ubuntu:13.04/raring [amd64])
Inst libpurple-bin (1:2.10.7-0ubuntu4.1 Ubuntu:13.04/raring [all])
Inst libzephyr4 (3.0.2-2 Ubuntu:13.04/raring [amd64])
Inst libpurple0 (1:2.10.7-0ubuntu4.1 Ubuntu:13.04/raring [amd64])
Inst libtext-levenshtein-perl (0.06~01-2 Ubuntu:13.04/raring [all])
Inst libtie-ixhash-perl (1.22-1 Ubuntu:13.04/raring [all])
Inst libwvstreams4.6-base (4.6.1-6 Ubuntu:13.04/raring [amd64])
Inst libwvstreams4.6-extras (4.6.1-6 Ubuntu:13.04/raring [amd64])
Inst libuniconf4.6 (4.6.1-6 Ubuntu:13.04/raring [amd64])
Inst unity-services (7.0.0daily13.04.18~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libunity-core-6.0-5 (7.0.0daily13.04.18~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libvisual-0.4-plugins (0.4.0.dfsg.1-7build1 Ubuntu:13.04/raring [amd64])
Inst libxfce4util-bin (4.10.0-1 Ubuntu:13.04/raring [amd64])
Inst libxml-xpath-perl (1.13-7 Ubuntu:13.04/raring [all])
Inst libzeitgeist-1.0-1 (0.3.18-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst make (3.81-8.2ubuntu2 Ubuntu:13.04/raring [amd64])
Inst hardening-includes (2.3 Ubuntu:13.04/raring [all])
Inst patchutils (0.3.2-1.1build1 Ubuntu:13.04/raring [amd64])
Inst t1utils (1.37-2 Ubuntu:13.04/raring [amd64])
Inst lintian (2.5.11ubuntu13 Ubuntu:13.04/raring [all])
Inst lp-solve (5.5.0.13-7 Ubuntu:13.04/raring [amd64])
Inst inputattach (1:1.4.3-1 Ubuntu:13.04/raring [amd64])
Inst openprinting-ppds (20130308-0ubuntu2 Ubuntu:13.04/raring [all])
Inst plymouth-label (0.8.8-0ubuntu6.1 Ubuntu:13.04/raring-updates [amd64])
Inst plymouth-theme-lubuntu-logo (0.38.1 Ubuntu:13.04/raring [all])
Inst plymouth-theme-lubuntu-text (0.38.1 Ubuntu:13.04/raring [all])
Inst printer-driver-pnm2ppa (1.13+nondbs-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst rfkill (0.4-2ubuntu1 Ubuntu:13.04/raring [amd64])
Inst ubuntu-extras-keyring (2010.09.27 Ubuntu:13.04/raring [all])
Inst wireless-tools (30~pre9-8ubuntu1 Ubuntu:13.04/raring [amd64])
Inst x11-apps (7.7~3ubuntu1 Ubuntu:13.04/raring [amd64])
Inst x11-session-utils (7.6+2build1 Ubuntu:13.04/raring [amd64])
Inst x11-xfs-utils (7.7~1 Ubuntu:13.04/raring [amd64])
Inst xorg-docs-core (1:1.6-1ubuntu2 Ubuntu:13.04/raring [all])
Inst xinput (1.6.0-1 Ubuntu:13.04/raring [amd64])
Inst xorg (1:7.7+1ubuntu4 Ubuntu:13.04/raring [amd64])
Inst lubuntu-core (0.48 Ubuntu:13.04/raring [amd64])
Inst lubuntu-default-session (0.31 Ubuntu:13.04/raring [all])
Inst guvcview (1.6.0-1~exp1build1 Ubuntu:13.04/raring [amd64])
Inst python-pysqlite2 (2.6.3-3 Ubuntu:13.04/raring [amd64])
Inst python-defer (1.0.6-2 Ubuntu:13.04/raring [all])
Inst python-pkg-resources (0.6.34-0ubuntu1 Ubuntu:13.04/raring [all])
Inst python-aptdaemon (1.0-0ubuntu9 Ubuntu:13.04/raring [all])
Inst python-aptdaemon.gtk3widgets (1.0-0ubuntu9 Ubuntu:13.04/raring [all])
Inst lubuntu-software-center (0.0.5~bzr159-0ubuntu1 Ubuntu:13.04/raring [all])
Inst lxappearance-obconf (0.2.0-4ubuntu1 Ubuntu:13.04/raring [amd64])
Inst python-support (1.0.15 Ubuntu:13.04/raring [all])
Inst python-xklavier (0.4-4 Ubuntu:13.04/raring [amd64])
Inst lxkeymap (0.8.0~bzr25+repack-0ubuntu1 Ubuntu:13.04/raring [all])
Inst lxlauncher (0.2.2-3ubuntu1 Ubuntu:13.04/raring [amd64])
Inst lxpanel-indicator-applet-plugin (0.5.12-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst lxtask (0.1.4-3ubuntu1 Ubuntu:13.04/raring [amd64])
Inst mobile-broadband-provider-info (20130312-1 Ubuntu:13.04/raring [all])
Inst modemmanager (0.6.0.0.really-0ubuntu5 Ubuntu:13.04/raring [amd64])
Inst mtpaint (3.40-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst pidgin-data (1:2.10.7-0ubuntu4.1 Ubuntu:13.04/raring [all])
Inst pidgin (1:2.10.7-0ubuntu4.1 Ubuntu:13.04/raring [amd64])
Inst pidgin-microblog (0.3.0-3 Ubuntu:13.04/raring [amd64])
Inst simple-scan (3.6.1-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst sylpheed-doc (20120629-1 Ubuntu:13.04/raring [all])
Inst sylpheed-i18n (3.3.0-1ubuntu1 Ubuntu:13.04/raring [all])
Inst synaptic (0.80~exp2 Ubuntu:13.04/raring [amd64])
Inst python-cups (1.9.62-0ubuntu3 Ubuntu:13.04/raring [amd64])
Inst python-smbc (1.0.13-0ubuntu4 Ubuntu:13.04/raring [amd64])
Inst python-pycurl (7.19.0-5ubuntu8 Ubuntu:13.04/raring [amd64])
Inst python-cupshelpers (1.3.12+20130308-0ubuntu4 Ubuntu:13.04/raring [all])
Inst system-config-printer-common (1.3.12+20130308-0ubuntu4 Ubuntu:13.04/raring [all])
Inst python-libxml2 (2.9.0+dfsg1-4ubuntu4.1 Ubuntu:13.04/raring-updates [amd64])
Inst python-gnomekeyring (2.32.0+dfsg-2ubuntu1 Ubuntu:13.04/raring [amd64])
Inst python3-aptdaemon.pkcompat (1.0-0ubuntu9 Ubuntu:13.04/raring [all])
Inst system-config-printer-gnome (1.3.12+20130308-0ubuntu4 Ubuntu:13.04/raring [all])
Inst transmission-common (2.77-0ubuntu1 Ubuntu:13.04/raring [all])
Inst transmission-gtk (2.77-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst transmission (2.77-0ubuntu1 Ubuntu:13.04/raring [all])
Inst ttf-wqy-microhei (0.2.0-beta-1.1ubuntu3 Ubuntu:13.04/raring [all])
Inst update-notifier (0.134 Ubuntu:13.04/raring [amd64]) []
Inst update-manager (1:0.186 Ubuntu:13.04/raring [all]) []
Inst ubuntu-release-upgrader-gtk (1:0.192.10 Ubuntu:13.04/raring [all])
Inst wvdial (1.61-4.1 Ubuntu:13.04/raring [amd64])
Inst xdg-user-dirs (0.14-0ubuntu5 Ubuntu:13.04/raring [amd64])
Inst xdg-user-dirs-gtk (0.10-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst xfburn (0.4.3-5ubuntu1 Ubuntu:13.04/raring [amd64])
Inst xfce4-power-manager-data (1.2.0-1ubuntu2 Ubuntu:13.04/raring [all])
Inst xfce4-power-manager (1.2.0-1ubuntu2 Ubuntu:13.04/raring [amd64])
Inst xpad (4.1-1ubuntu4 Ubuntu:13.04/raring [amd64])
Inst lubuntu-desktop (0.48 Ubuntu:13.04/raring [amd64])
Inst media-player-info (17-1 Ubuntu:13.04/raring [all])
Inst mousetweaks (3.6.0-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst pptp-linux (1.7.2-7 Ubuntu:13.04/raring [amd64])
Inst network-manager-pptp (0.9.6.0-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst network-manager-pptp-gnome (0.9.6.0-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst pidgin-libnotify (0.14-9ubuntu1 Ubuntu:13.04/raring [amd64])
Inst policykit-desktop-privileges (0.14 Ubuntu:13.04/raring [all])
Inst printer-driver-c2esp (26-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst mscompress (0.3-4 Ubuntu:13.04/raring [amd64])
Inst printer-driver-foo2zjs (20130306dfsg0-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst printer-driver-min12xxw (0.0.9-6ubuntu2 Ubuntu:13.04/raring [amd64])
Inst printer-driver-postscript-hp (3.13.3-1 Ubuntu:13.04/raring [all])
Inst printer-driver-ptouch (1.3-4ubuntu1 Ubuntu:13.04/raring [amd64])
Inst printer-driver-pxljr (1.3+repack0-2build1 Ubuntu:13.04/raring [amd64])
Inst printer-driver-sag-gdi (0.1-3 Ubuntu:13.04/raring [all])
Inst printer-driver-splix (2.0.0+svn308-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst pulseaudio-utils (1:3.0-0ubuntu6 Ubuntu:13.04/raring [amd64])
Inst pulseaudio-module-x11 (1:3.0-0ubuntu6 Ubuntu:13.04/raring [amd64])
Inst python-appindicator (12.10.1daily13.04.15-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst python-gconf (2.28.1+dfsg-1build1 Ubuntu:13.04/raring [amd64])
Inst python-markupsafe (0.15-1build3 Ubuntu:13.04/raring [amd64])
Inst python-mako (0.7.3-1 Ubuntu:13.04/raring [all])
Inst python-renderpm (2.6-1 Ubuntu:13.04/raring [amd64])
Inst python-reportlab-accel (2.6-1 Ubuntu:13.04/raring [amd64])
Inst python-zeitgeist (0.9.5-0ubuntu1 Ubuntu:13.04/raring [all])
Inst python3-httplib2 (0.7.7-1 Ubuntu:13.04/raring [all])
Inst qdbus (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Inst qpdf (4.0.1-2 Ubuntu:13.04/raring [amd64])
Inst radeontool (1.6.2-1.1build1 Ubuntu:13.04/raring [amd64])
Inst librarian0 (0.8.1-5build1 Ubuntu:13.04/raring [amd64])
Inst rarian-compat (0.8.1-5build1 Ubuntu:13.04/raring [amd64])
Inst rhythmbox-data (2.98-0ubuntu5 Ubuntu:13.04/raring [all])
Inst rhythmbox (2.98-0ubuntu5 Ubuntu:13.04/raring [amd64])
Inst rhythmbox-mozilla (2.98-0ubuntu5 Ubuntu:13.04/raring [amd64])
Inst rhythmbox-plugin-cdrecorder (2.98-0ubuntu5 Ubuntu:13.04/raring [amd64])
Inst gir1.2-peas-1.0 (1.6.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst zeitgeist-core (0.9.5-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst rhythmbox-plugin-zeitgeist (2.98-0ubuntu5 Ubuntu:13.04/raring [all])
Inst rhythmbox-plugins (2.98-0ubuntu5 Ubuntu:13.04/raring [amd64])
Inst rtkit (0.10-2build1 Ubuntu:13.04/raring [amd64])
Inst update-inetd (4.43 Ubuntu:13.04/raring [all])
Inst sane-utils (1.0.23-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst system-config-printer-udev (1.3.12+20130308-0ubuntu4 Ubuntu:13.04/raring [amd64])
Inst toshset (1.76-4 Ubuntu:13.04/raring [amd64])
Inst ttf-indic-fonts-core (1:0.5.11ubuntu1 Ubuntu:13.04/raring [all])
Inst ttf-punjabi-fonts (1:0.5.11ubuntu1 Ubuntu:13.04/raring [all])
Inst ubuntu-system-service (0.2.4 Ubuntu:13.04/raring [all])
Inst unity (7.0.0daily13.04.18~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst unity-greeter (13.04.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst unity-lens-applications (6.10.0daily13.04.18~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst unity-lens-files (7.0~daily13.04.15-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst unity-lens-music (6.8.1daily13.04.18~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst unity-lens-photos (0.9daily12.12.05-0ubuntu1 Ubuntu:13.04/raring [all])
Inst unity-lens-shopping (6.8.0daily13.03.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst unity-lens-video (0.3.14daily13.04.15-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst python-dirspec (4.2.0-0ubuntu1 Ubuntu:13.04/raring [all])
Inst rhythmbox-ubuntuone (4.2.0-0ubuntu1 Ubuntu:13.04/raring [all])
Inst unity-scope-musicstores (6.8.1daily13.04.18~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst unity-scope-video-remote (0.3.14daily13.04.15-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst vbetool (1.1-3 Ubuntu:13.04/raring [amd64])
Inst xfonts-100dpi (1:1.0.3 Ubuntu:13.04/raring [all])
Inst xfonts-scalable (1:1.0.3-1 Ubuntu:13.04/raring [all])
Inst xul-ext-ubufox (2.6-0ubuntu1 Ubuntu:13.04/raring [all])
Inst zeitgeist-datahub (0.9.5-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst zeitgeist (0.9.5-0ubuntu1 Ubuntu:13.04/raring [all])
Inst appmenu-qt5 (0.2.7daily13.03.28-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst cups-bsd (1.6.2-1ubuntu5 Ubuntu:13.04/raring [amd64])
Inst cups-pk-helper (0.2.4-0ubuntu5 Ubuntu:13.04/raring [amd64])
Inst friends (0.1.3daily13.04.17.1~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst friends-facebook (0.1.3daily13.04.17.1~13.04-0ubuntu1 Ubuntu:13.04/raring [all])
Inst friends-twitter (0.1.3daily13.04.17.1~13.04-0ubuntu1 Ubuntu:13.04/raring [all])
Inst indicator-bluetooth (0.0.6daily13.02.19-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst indicator-printers (0.1.7daily13.03.01-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst indicator-sound (12.10.2daily13.04.12-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libpam-freerdp (1.0.1-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libwebcam0 (0.2.2-1 Ubuntu:13.04/raring [amd64])
Inst lightdm-remote-session-freerdp (1.0-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst lightdm-remote-session-uccsconfigure (1.1-0ubuntu2 Ubuntu:13.04/raring [amd64])
Inst lm-sensors (1:3.3.2-2ubuntu1 Ubuntu:13.04/raring [amd64])
Inst qtchooser (0.0.1~git20121229.g8f08405-0ubuntu3 Ubuntu:13.04/raring [amd64])
Inst remote-login-service (1.0.0-0ubuntu3 Ubuntu:13.04/raring [amd64])
Inst sessioninstaller (0.20+bzr134-0ubuntu6 Ubuntu:13.04/raring [all])
Inst thin-client-config-agent (0.7 Ubuntu:13.04/raring [all])
Inst unity-lens-friends (0.1.1bzr13.04.12-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst unity-scope-gdrive (0.8daily13.04.15-0ubuntu1 Ubuntu:13.04/raring [all])
Inst uvcdynctrl-data (0.2.2-1 Ubuntu:13.04/raring [all])
Inst uvcdynctrl (0.2.2-1 Ubuntu:13.04/raring [amd64])
Conf ace-of-penguins (1.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libdbusmenu-glib4 (12.10.3daily13.02.01-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libdbusmenu-gtk4 (12.10.3daily13.02.01-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf appmenu-gtk (12.10.3daily13.04.03-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libdbusmenu-gtk3-4 (12.10.3daily13.02.01-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf appmenu-gtk3 (12.10.3daily13.04.03-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf audacious-plugins-data (3.3.4-1ubuntu1 Ubuntu:13.04/raring [all])
Conf libaudcore1 (3.3.4-1 Ubuntu:13.04/raring [amd64])
Conf libavutil51 (6:0.8.6-1ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libgsm1 (1.0.13-4 Ubuntu:13.04/raring [amd64])
Conf liborc-0.4-0 (1:0.4.17-1 Ubuntu:13.04/raring [amd64])
Conf libschroedinger-1.0-0 (1.0.11-2 Ubuntu:13.04/raring [amd64])
Conf libspeex1 (1.2~rc1-7ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libtheora0 (1.1.1+dfsg.1-3.1 Ubuntu:13.04/raring [amd64])
Conf libva1 (1.0.15-4build1 Ubuntu:13.04/raring [amd64])
Conf libvorbisenc2 (1.3.2-1.3 Ubuntu:13.04/raring [amd64])
Conf libvpx1 (1.1.0-1 Ubuntu:13.04/raring [amd64])
Conf libavcodec53 (6:0.8.6-1ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libavformat53 (6:0.8.6-1ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libbinio1ldbl (1.4+dfsg1-1 Ubuntu:13.04/raring [amd64])
Conf libbs2b0 (3.1.0+dfsg-2ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libcddb2 (1.3.2-3fakesync1 Ubuntu:13.04/raring [amd64])
Conf libcue1 (1.4.0-1 Ubuntu:13.04/raring [amd64])
Conf libfaad2 (2.7-8 Ubuntu:13.04/raring [amd64])
Conf libflac8 (1.2.1-6build1 Ubuntu:13.04/raring [amd64])
Conf libsamplerate0 (0.1.8-5 Ubuntu:13.04/raring [amd64])
Conf libjack-jackd2-0 (1.9.9.5+20130127git15950eb1-1 Ubuntu:13.04/raring [amd64])
Conf libasyncns0 (0.8-4build1 Ubuntu:13.04/raring [amd64])
Conf libsndfile1 (1.0.25-5 Ubuntu:13.04/raring [amd64])
Conf libpulse0 (1:3.0-0ubuntu6 Ubuntu:13.04/raring [amd64])
Conf libfluidsynth1 (1.1.6-2 Ubuntu:13.04/raring [amd64])
Conf liblircclient0 (0.9.0-0ubuntu3 Ubuntu:13.04/raring [amd64])
Conf libmms0 (0.6.2-3 Ubuntu:13.04/raring [amd64])
Conf libmodplug1 (1:0.8.8.4-3 Ubuntu:13.04/raring [amd64])
Conf libmp3lame0 (3.99.5+repack1-3 Ubuntu:13.04/raring [amd64])
Conf libmpg123-0 (1.14.4-1 Ubuntu:13.04/raring [amd64])
Conf libneon27-gnutls (0.29.6-3 Ubuntu:13.04/raring [amd64])
Conf libresid-builder0c2a (2.1.1-14 Ubuntu:13.04/raring [amd64])
Conf libcaca0 (0.99.beta18-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libsdl1.2debian (1.2.15-5ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libsidplay2 (2.1.1-14 Ubuntu:13.04/raring [amd64])
Conf libwavpack1 (4.60.1-3 Ubuntu:13.04/raring [amd64])
Conf audacious-plugins (3.3.4-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf bluez (4.101-0ubuntu8b1 Ubuntu:13.04/raring [amd64])
Conf libcupscgi1 (1.6.2-1ubuntu5 Ubuntu:13.04/raring [amd64])
Conf libcupsfilters1 (1.0.34-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libcupsimage2 (1.6.2-1ubuntu5 Ubuntu:13.04/raring [amd64])
Conf libcupsmime1 (1.6.2-1ubuntu5 Ubuntu:13.04/raring [amd64])
Conf libcupsppdc1 (1.6.2-1ubuntu5 Ubuntu:13.04/raring [amd64])
Conf libpaper1 (1.1.24+nmu2ubuntu2 Ubuntu:13.04/raring [amd64])
Conf ssl-cert (1.0.32 Ubuntu:13.04/raring [all])
Conf bc (1.06.95-4ubuntu1 Ubuntu:13.04/raring [amd64])
Conf cups-daemon (1.6.2-1ubuntu5 Ubuntu:13.04/raring [amd64])
Conf libpoppler28 (0.20.5-1ubuntu3 Ubuntu:13.04/raring [amd64])
Conf poppler-utils (0.20.5-1ubuntu3 Ubuntu:13.04/raring [amd64])
Conf libijs-0.35 (0.35-8build1 Ubuntu:13.04/raring [amd64])
Conf libjbig2dec0 (0.11+20120125-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf poppler-data (0.4.6-2 Ubuntu:13.04/raring [all])
Conf libgs9-common (9.07~dfsg2-0ubuntu3 Ubuntu:13.04/raring [all])
Conf libgs9 (9.07~dfsg2-0ubuntu3 Ubuntu:13.04/raring [amd64])
Conf gsfonts (1:8.11+urwcyr1.0.7~pre44-4.2ubuntu1 Ubuntu:13.04/raring [all])
Conf ghostscript (9.07~dfsg2-0ubuntu3 Ubuntu:13.04/raring [amd64])
Conf cups-common (1.6.2-1ubuntu5 Ubuntu:13.04/raring [all])
Conf cups-client (1.6.2-1ubuntu5 Ubuntu:13.04/raring [amd64])
Conf cups-ppdc (1.6.2-1ubuntu5 Ubuntu:13.04/raring [amd64])
Conf libfontembed1 (1.0.34-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libqpdf10 (4.0.1-2 Ubuntu:13.04/raring [amd64])
Conf fonts-freefont-ttf (20120503-1 Ubuntu:13.04/raring [all])
Conf fonts-liberation (1.07.2-6ubuntu1 Ubuntu:13.04/raring [all])
Conf cups-filters (1.0.34-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf cups (1.6.2-1ubuntu5 Ubuntu:13.04/raring [amd64])
Conf sgml-data (2.0.8 Ubuntu:13.04/raring [all])
Conf docbook-xml (4.5-7.1 Ubuntu:13.04/raring [all])
Conf humanity-icon-theme (0.6.2 Ubuntu:13.04/raring [all])
Conf gnome-icon-theme (3.6.2-0ubuntu1 Ubuntu:13.04/raring [all])
Conf gnome-icon-theme-full (3.6.2-0ubuntu1 Ubuntu:13.04/raring [all])
Conf elementary-icon-theme (2.7.1-0ubuntu6 Ubuntu:13.04/raring [all])
Conf fonts-kacst (2.01+mry-9 Ubuntu:13.04/raring [all])
Conf fonts-kacst-one (5.0+svn11846-6 Ubuntu:13.04/raring [all])
Conf fonts-nanum (3.020-2 Ubuntu:13.04/raring [all])
Conf fonts-takao-pgothic (003.02.01-7ubuntu3 Ubuntu:13.04/raring [all])
Conf foomatic-filters (4.0.17-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libcrack2 (2.8.22-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libpwquality1 (1.1.1-1 Ubuntu:13.04/raring [amd64])
Conf gnome-disk-utility (3.6.1-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gnome-menus (3.6.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libgpm2 (1.20.4-6ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libaa1 (1.4p5-40 Ubuntu:13.04/raring [amd64])
Conf libraw1394-11 (2.0.9-1 Ubuntu:13.04/raring [amd64])
Conf libavc1394-0 (0.5.4-2 Ubuntu:13.04/raring [amd64])
Conf libdv4 (1.0.0-6 Ubuntu:13.04/raring [amd64])
Conf libgstreamer0.10-0 (0.10.36-1ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libgstreamer-plugins-base0.10-0 (0.10.36-1.1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libiec61883-0 (1.2.0-0.1ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libshout3 (2.3.1-1ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libtag1-vanilla (1.8-1 Ubuntu:13.04/raring [amd64])
Conf libtag1c2a (1.8-1 Ubuntu:13.04/raring [amd64])
Conf libcdparanoia0 (3.10.2+debian-11 Ubuntu:13.04/raring [amd64])
Conf libvisual-0.4-0 (0.4.0-5 Ubuntu:13.04/raring [amd64])
Conf gstreamer0.10-plugins-base (0.10.36-1.1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gstreamer0.10-plugins-good (0.10.31-3+nmu1ubuntu2 Ubuntu:13.04/raring [amd64])
Conf gvfs-bin (1.16.1-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libaacs0 (0.6.0-1 Ubuntu:13.04/raring [amd64])
Conf libaspell15 (0.60.7~20110707-1build1 Ubuntu:13.04/raring [amd64])
Conf libhunspell-1.3-0 (1.3.2-4ubuntu1 Ubuntu:13.04/raring [amd64])
Conf aspell (0.60.7~20110707-1build1 Ubuntu:13.04/raring [amd64])
Conf aspell-en (7.1-0-1 Ubuntu:13.04/raring [all])
Conf hunspell-en-us (20070829-4ubuntu3 Ubuntu:13.04/raring [all])
Conf libenchant1c2a (1.6.0-7build1 Ubuntu:13.04/raring [amd64])
Conf libgsf-1-common (1.14.26-1ubuntu1 Ubuntu:13.04/raring [all])
Conf libgsf-1-114 (1.14.26-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libxslt1.1 (1.1.27-1ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libyajl2 (2.0.4-2 Ubuntu:13.04/raring [amd64])
Conf libraptor2-0 (2.0.8-2 Ubuntu:13.04/raring [amd64])
Conf libmhash2 (0.9.9.9-1.1 Ubuntu:13.04/raring [amd64])
Conf librasqal3 (0.9.29-1 Ubuntu:13.04/raring [amd64])
Conf librdf0 (1.0.16-1 Ubuntu:13.04/raring [amd64])
Conf libwv-1.2-4 (1.2.9-3 Ubuntu:13.04/raring [amd64])
Conf libabiword-2.9 (2.9.2+svn20120603-8 Ubuntu:13.04/raring [amd64])
Conf libaccounts-glib0 (1.8-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libqtcore4 (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Conf libqt4-xml (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Conf libaccounts-qt1 (1.6bzr13.02.27-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libindicator7 (12.10.2daily13.04.10-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libappindicator1 (12.10.1daily13.04.15-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libindicator3-7 (12.10.2daily13.04.10-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libappindicator3-1 (12.10.1daily13.04.15-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libart-2.0-2 (2.3.21-2 Ubuntu:13.04/raring [amd64])
Conf libspeexdsp1 (1.2~rc1-7ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libasound2-plugins (1.0.25-2ubuntu3 Ubuntu:13.04/raring [amd64])
Conf libaudclient2 (3.3.4-1 Ubuntu:13.04/raring [amd64])
Conf libaudio2 (1.9.3-5 Ubuntu:13.04/raring [amd64])
Conf libavahi-core7 (0.6.31-1ubuntu3 Ubuntu:13.04/raring [amd64])
Conf libgeoclue0 (0.12.99-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libnm-util2 (0.9.8.0-0ubuntu6 Ubuntu:13.04/raring [amd64])
Conf libnm-glib4 (0.9.8.0-0ubuntu6 Ubuntu:13.04/raring [amd64])
Conf geoclue (0.12.99-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf geoclue-ubuntu-geoip (1.0.1-0ubuntu4 Ubuntu:13.04/raring [amd64])
Conf libjson-glib-1.0-0 (0.15.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libmessaging-menu0 (12.10.6daily13.04.09-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libtelepathy-glib0 (0.20.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libdee-1.0-4 (1.2.3~daily13.03.13.1-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libunity-protocol-private0 (6.90.2daily13.04.05-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libunity-common (6.90.2daily13.04.05-0ubuntu1 Ubuntu:13.04/raring [all])
Conf libunity9 (6.90.2daily13.04.05-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libwnck-3-common (3.4.5-0ubuntu1 Ubuntu:13.04/raring [all])
Conf libwnck-3-0 (3.4.5-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libpackagekit-glib2-14 (0.7.6-3ubuntu1 Ubuntu:13.04/raring [amd64])
Conf unity-webapps-service (2.5.0~daily13.03.18-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libunity-webapps0 (2.5.0~daily13.03.18-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf bamfdaemon (0.4.0daily13.04.03-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libbamf3-1 (0.4.0daily13.04.03-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libbluray1 (1:0.2.3-1 Ubuntu:13.04/raring [amd64])
Conf libcolumbus0-0-common (0.4.0daily13.04.16~13.04-0ubuntu1 Ubuntu:13.04/raring [all])
Conf libcolumbus0-0 (0.4.0daily13.04.16~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libcurl3 (7.29.0-1ubuntu3 Ubuntu:13.04/raring [amd64])
Conf libqt4-dbus (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Conf liblcms1 (1.19.dfsg-1.2ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libmng1 (1.0.10-3build1 Ubuntu:13.04/raring [amd64])
Conf libqt4-network (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Conf libqt4-script (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Conf libqt4-sql (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Conf libqt4-xmlpatterns (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Conf libqt4-declarative (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Conf libqtgui4 (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Conf libdbusmenu-qt2 (0.9.2daily13.03.28-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libdbusmenu-qt5 (0.9.2daily13.03.28-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf tsconf (1.0-11 Ubuntu:13.04/raring [all])
Conf libts-0.0-0 (1.0-11 Ubuntu:13.04/raring [amd64])
Conf libdirectfb-1.2-9 (1.2.10.0-5 Ubuntu:13.04/raring [amd64])
Conf libdiscid0 (0.2.2-3build1 Ubuntu:13.04/raring [amd64])
Conf libdjvulibre-text (3.5.25.3-3 Ubuntu:13.04/raring [all])
Conf libdjvulibre21 (3.5.25.3-3 Ubuntu:13.04/raring [amd64])
Conf libdvdread4 (4.2.0+20121016-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libdvdnav4 (4.2.0+20130225-1 Ubuntu:13.04/raring [amd64])
Conf libelfg0 (0.8.13-4~1 Ubuntu:13.04/raring [amd64])
Conf libmailtools-perl (2.09-1 Ubuntu:13.04/raring [all])
Conf libdigest-hmac-perl (1.03+dfsg-1 Ubuntu:13.04/raring [all])
Conf libnet-ip-perl (1.26-1 Ubuntu:13.04/raring [all])
Conf libsocket6-perl (0.23-1build3 Ubuntu:13.04/raring [amd64])
Conf libio-socket-inet6-perl (2.69-2 Ubuntu:13.04/raring [all])
Conf libnet-dns-perl (0.68-1.1 Ubuntu:13.04/raring [amd64])
Conf libnet-domain-tld-perl (1.69-1 Ubuntu:13.04/raring [all])
Conf libemail-valid-perl (0.190-1 Ubuntu:13.04/raring [all])
Conf libevent-2.0-5 (2.0.19-stable-3 Ubuntu:13.04/raring [amd64])
Conf libxfce4util-common (4.10.0-1 Ubuntu:13.04/raring [all])
Conf libxfce4util6 (4.10.0-1 Ubuntu:13.04/raring [amd64])
Conf xfconf (4.10.0-1 Ubuntu:13.04/raring [amd64])
Conf libxfconf-0-2 (4.10.0-1 Ubuntu:13.04/raring [amd64])
Conf xfce-keyboard-shortcuts (4.10.0-1 Ubuntu:13.04/raring [all])
Conf libxfce4ui-1-0 (4.10.0-1 Ubuntu:13.04/raring [amd64])
Conf libexo-common (0.10.2-1 Ubuntu:13.04/raring [all])
Conf libexo-helpers (0.10.2-1 Ubuntu:13.04/raring [amd64])
Conf libexo-1-0 (0.10.2-1 Ubuntu:13.04/raring [amd64])
Conf libgssdp-1.0-3 (0.14.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libgupnp-1.0-4 (0.20.0-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libgupnp-igd-1.0-4 (0.2.1-2ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libnice10 (0.1.3-1 Ubuntu:13.04/raring [amd64])
Conf gstreamer0.10-nice (0.1.3-1 Ubuntu:13.04/raring [amd64])
Conf libfarstream-0.1-0 (0.1.2-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libgomp1 (4.7.3-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libfftw3-single3 (3.3.3-2ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libframe6 (2.5.0daily13.03.12-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libfreerdp1 (1.0.1-2ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libfreerdp-plugins-standard (1.0.1-2ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libfs6 (2:1.0.4-1 Ubuntu:13.04/raring [amd64])
Conf libgail-3-0 (3.6.4-0ubuntu8 Ubuntu:13.04/raring [amd64])
Conf libunistring0 (0.9.3-5build1 Ubuntu:13.04/raring [amd64])
Conf libgettextpo0 (0.18.1.1-10ubuntu3 Ubuntu:13.04/raring [amd64])
Conf libglew1.8 (1.9.0.is.1.8.0-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libglewmx1.8 (1.9.0.is.1.8.0-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libglib2.0-data (2.36.0-1ubuntu2 Ubuntu:13.04/raring [all])
Conf libglib2.0-bin (2.36.0-1ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libglibmm-2.4-1c2a (2.35.9-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libpulse-mainloop-glib0 (1:3.0-0ubuntu6 Ubuntu:13.04/raring [amd64])
Conf libgmlib1 (1.0.8-1 Ubuntu:13.04/raring [amd64])
Conf libgmtk1-data (1.0.8-1 Ubuntu:13.04/raring [all])
Conf libgmtk1 (1.0.8-1 Ubuntu:13.04/raring [amd64])
Conf librest-0.7-0 (0.7.90-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libjavascriptcoregtk-3.0-0 (1.10.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libgstreamer1.0-0 (1.0.6-1 Ubuntu:13.04/raring [amd64])
Conf libgstreamer-plugins-base1.0-0 (1.0.6-1 Ubuntu:13.04/raring [amd64])
Conf libwebkitgtk-3.0-common (1.10.2-0ubuntu1 Ubuntu:13.04/raring [all])
Conf libwebkitgtk-3.0-0 (1.10.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libgoa-1.0-common (3.6.2-1ubuntu1 Ubuntu:13.04/raring [all])
Conf libgoa-1.0-0 (3.6.2-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libgpod4 (0.8.2-7ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libgrail6 (3.1.0daily13.02.26-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libgeis1 (2.2.15daily13.04.03-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libgrip0 (0.3.6daily13.02.26-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libgutenprint2 (5.2.9-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libgxps2 (0.2.2-2ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libibus-1.0-0 (1.4.2-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libido3-0.1-0 (12.10.3daily13.03.01-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf liblua5.1-0 (5.1.5-4 Ubuntu:13.04/raring [amd64])
Conf libmowgli2 (1.0.0-1 Ubuntu:13.04/raring [amd64])
Conf mysql-common (5.5.31-0ubuntu0.13.04.1 Ubuntu:13.04/raring-updates [all])
Conf libmysqlclient18 (5.5.31-0ubuntu0.13.04.1 Ubuntu:13.04/raring-updates [amd64])
Conf libnl-route-3-200 (3.2.16-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libnux-4.0-common (4.0.1daily13.04.17~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libglu1-mesa (9.0.0-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libnux-4.0-0 (4.0.1daily13.04.17~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf liboauth0 (1.0.1-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libpam-xdg-support (0.2-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libpcsclite1 (1.8.6-3ubuntu1b1 Ubuntu:13.04/raring [amd64])
Conf libpoppler-glib8 (0.20.5-1ubuntu3 Ubuntu:13.04/raring [amd64])
Conf libportaudio2 (19+svn20111121-1build1 Ubuntu:13.04/raring [amd64])
Conf libpostproc52 (6:0.8.6-1ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libpulsedsp (1:3.0-0ubuntu6 Ubuntu:13.04/raring [amd64])
Conf libpython2.7 (2.7.4-2ubuntu3 Ubuntu:13.04/raring [amd64])
Conf libpython3.3 (3.3.1-1ubuntu5 Ubuntu:13.04/raring [amd64])
Conf libqjson0 (0.8.1-1 Ubuntu:13.04/raring [amd64])
Conf libqt4-opengl (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Conf libqt4-sql-mysql (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Conf libqt4-sql-sqlite (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Conf libqt4-test (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Conf libqtwebkit4 (2.3.0-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libreadline5 (5.2+dfsg-1 Ubuntu:13.04/raring [amd64])
Conf libsensors4 (1:3.3.2-2ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libsignon-extension1 (8.49-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libsignon-plugins-common1 (8.49-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf session-migration (0.2 Ubuntu:13.04/raring [amd64])
Conf signond (8.49-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libsignon-glib1 (1.9-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libspectre1 (0.2.7-2 Ubuntu:13.04/raring [amd64])
Conf libswscale2 (6:0.8.6-1ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libsysfs2 (2.1.0+repack-2 Ubuntu:13.04/raring [amd64])
Conf libunity-misc4 (4.0.5daily13.02.26-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libvdpau1 (0.4.1-8 Ubuntu:13.04/raring [amd64])
Conf libwacom-common (0.7-1 Ubuntu:13.04/raring [all])
Conf libwacom2 (0.7-1 Ubuntu:13.04/raring [amd64])
Conf libwmf0.2-7 (0.2.8.4-10.3ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libx86-1 (1.1+ds1-10 Ubuntu:13.04/raring [amd64])
Conf libxp6 (1:1.0.1-2build1 Ubuntu:13.04/raring [amd64])
Conf libxvidcore4 (2:1.3.2-9 Ubuntu:13.04/raring [amd64])
Conf lightdm (1.6.0-0ubuntu2.1 Ubuntu:13.04/raring-updates [amd64])
Conf libxklavier16 (5.2.1-1ubuntu2 Ubuntu:13.04/raring [amd64])
Conf liblightdm-gobject-1-0 (1.6.0-0ubuntu2.1 Ubuntu:13.04/raring-updates [amd64])
Conf lightdm-gtk-greeter (1.5.1-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gtk3-engines-unico (1.0.3daily12.12.12-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf lubuntu-artwork-13-04 (0.38.1 Ubuntu:13.04/raring [all])
Conf lubuntu-lxpanel-icons (0.38.1 Ubuntu:13.04/raring [all])
Conf lubuntu-artwork (0.38.1 Ubuntu:13.04/raring [all])
Conf gnome-icon-theme-symbolic (3.6.2-0ubuntu1 Ubuntu:13.04/raring [all])
Conf lubuntu-icon-theme (0.38.1 Ubuntu:13.04/raring [all])
Conf ttf-ubuntu-font-family (0.80-0ubuntu5 Ubuntu:13.04/raring [all])
Conf lubuntu-default-settings (0.31 Ubuntu:13.04/raring [all])
Conf wpasupplicant (1.0-3ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libnetfilter-conntrack3 (1.0.1-1 Ubuntu:13.04/raring [amd64])
Conf dnsmasq-base (2.65-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf iputils-arping (3:20101006-3ubuntu1 Ubuntu:13.04/raring [amd64])
Conf network-manager (0.9.8.0-0ubuntu6 Ubuntu:13.04/raring [amd64])
Conf libgnome-bluetooth11 (3.6.1-0ubuntu3 Ubuntu:13.04/raring [amd64])
Conf libnm-glib-vpn1 (0.9.8.0-0ubuntu6 Ubuntu:13.04/raring [amd64])
Conf libnm-gtk-common (0.9.8.0-1ubuntu2 Ubuntu:13.04/raring [all])
Conf libnm-gtk0 (0.9.8.0-1ubuntu2 Ubuntu:13.04/raring [amd64])
Conf network-manager-gnome (0.9.8.0-1ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libopts25 (1:5.17.1-1ubuntu2 Ubuntu:13.04/raring [amd64])
Conf ntp (1:4.2.6.p5+dfsg-2ubuntu1 Ubuntu:13.04/raring [amd64])
Conf nux-tools (4.0.1daily13.04.17~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf pcmciautils (018-8 Ubuntu:13.04/raring [amd64])
Conf python-gi (3.8.0-2 Ubuntu:13.04/raring [amd64])
Conf samba-common (2:3.6.9-1ubuntu1 Ubuntu:13.04/raring [all])
Conf samba-common-bin (2:3.6.9-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf smbclient (2:3.6.9-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libcompfaceg1 (1:1.5.2-5 Ubuntu:13.04/raring [amd64])
Conf libpth20 (2.0.7-16ubuntu4 Ubuntu:13.04/raring [amd64])
Conf libgpgme11 (1.2.0-1.4ubuntu4 Ubuntu:13.04/raring [amd64])
Conf libgtkspell0 (2.0.16-1ubuntu6 Ubuntu:13.04/raring [amd64])
Conf libonig2 (5.9.1-1 Ubuntu:13.04/raring [amd64])
Conf libpisock9 (0.12.5-5ubuntu1 Ubuntu:13.04/raring [amd64])
Conf sylpheed (3.3.0-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf sylpheed-plugins (3.3.0-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf liburi-perl (1.60-1 Ubuntu:13.04/raring [all])
Conf libencode-locale-perl (1.03-1 Ubuntu:13.04/raring [all])
Conf libhttp-date-perl (6.02-1 Ubuntu:13.04/raring [all])
Conf libfile-listing-perl (6.04-1 Ubuntu:13.04/raring [all])
Conf libhtml-tagset-perl (3.20-2 Ubuntu:13.04/raring [all])
Conf libhtml-parser-perl (3.69-2 Ubuntu:13.04/raring [amd64])
Conf libhtml-tree-perl (5.02-1 Ubuntu:13.04/raring [all])
Conf liblwp-mediatypes-perl (6.02-1 Ubuntu:13.04/raring [all])
Conf libhttp-message-perl (6.03-1 Ubuntu:13.04/raring [all])
Conf libhttp-cookies-perl (6.00-2 Ubuntu:13.04/raring [all])
Conf libhttp-negotiate-perl (6.00-2 Ubuntu:13.04/raring [all])
Conf libnet-ssleay-perl (1.48-1 Ubuntu:13.04/raring [amd64])
Conf libio-socket-ssl-perl (1.76-2ubuntu1 Ubuntu:13.04/raring [all])
Conf libnet-http-perl (6.03-2 Ubuntu:13.04/raring [all])
Conf libwww-robotrules-perl (6.01-1 Ubuntu:13.04/raring [all])
Conf liblwp-protocol-https-perl (6.03-1 Ubuntu:13.04/raring [all])
Conf libwww-perl (6.04-1 Ubuntu:13.04/raring [all])
Conf libxml-parser-perl (2.41-1build2 Ubuntu:13.04/raring [amd64])
Conf libxml-twig-perl (1:3.39-1ubuntu1 Ubuntu:13.04/raring [all])
Conf libnet-dbus-perl (1.0.0-2 Ubuntu:13.04/raring [amd64])
Conf system-tools-backends (2.10.2-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf python3-xkit (0.5.0ubuntu1 Ubuntu:13.04/raring [all])
Conf dialog (1.1-20120215-3 Ubuntu:13.04/raring [amd64])
Conf alsa-utils (1.0.25-4ubuntu2 Ubuntu:13.04/raring [amd64])
Conf ubuntu-drivers-common (1:0.2.76 Ubuntu:13.04/raring [amd64])
Conf unity-common (7.0.0daily13.04.18~13.04-0ubuntu1 Ubuntu:13.04/raring [all])
Conf patch (2.6.1-3ubuntu2 Ubuntu:13.04/raring [amd64])
Conf update-notifier-common (0.134 Ubuntu:13.04/raring [all])
Conf libwhoopsie0 (0.2.15 Ubuntu:13.04/raring [amd64])
Conf whoopsie (0.2.15 Ubuntu:13.04/raring [amd64])
Conf dconf-tools (0.16.0-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gnome-desktop3-data (3.6.3-0ubuntu1 Ubuntu:13.04/raring [all])
Conf libgnome-desktop-3-4 (3.6.3-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libgnomekbd-common (3.6.0-0ubuntu2 Ubuntu:13.04/raring [all])
Conf libgnomekbd8 (3.6.0-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libupower-glib1 (0.9.20-1 Ubuntu:13.04/raring [amd64])
Conf nautilus-data (1:3.6.3-0ubuntu16 Ubuntu:13.04/raring [all])
Conf gnome-settings-daemon (3.6.4-0ubuntu8 Ubuntu:13.04/raring [amd64])
Conf libenca0 (1.14-2 Ubuntu:13.04/raring [amd64])
Conf libass4 (0.10.1-1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-dee-1.0 (1.2.3~daily13.03.13.1-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-freedesktop (1.36.0-1 Ubuntu:13.04/raring [amd64])
Conf libcamel-1.2-40 (3.6.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf evolution-data-server-common (3.6.4-0ubuntu1 Ubuntu:13.04/raring [all])
Conf libedataserver-1.2-17 (3.6.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-edataserver-1.2 (3.6.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libebook-1.2-14 (3.6.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-ebook-1.2 (3.6.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-gdkpixbuf-2.0 (2.28.0-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-networkmanager-1.0 (0.9.8.0-0ubuntu6 Ubuntu:13.04/raring [amd64])
Conf gir1.2-notify-0.7 (0.7.5-2 Ubuntu:13.04/raring [amd64])
Conf gir1.2-signon-1.0 (1.9-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-soup-2.4 (2.40.3-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-accounts-1.0 (1.8-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf python3-pkg-resources (0.6.34-0ubuntu1 Ubuntu:13.04/raring [all])
Conf python3-crypto (2.6-4 Ubuntu:13.04/raring [amd64])
Conf python3-oauthlib (0.3.7-0ubuntu1 Ubuntu:13.04/raring [all])
Conf friends-dispatcher (0.1.3daily13.04.17.1~13.04-0ubuntu1 Ubuntu:13.04/raring [all])
Conf libfriends0 (0.1.2daily13.03.26-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libgstreamer-plugins-good1.0-0 (1.0.6-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libguess1 (1.1-1 Ubuntu:13.04/raring [amd64])
Conf libquvi-scripts (0.4.8-3 Ubuntu:13.04/raring [all])
Conf libquvi7 (0.4.1-1 Ubuntu:13.04/raring [amd64])
Conf libsystemd-daemon0 (198-0ubuntu11 Ubuntu:13.04/raring [amd64])
Conf systemd-services (198-0ubuntu11 Ubuntu:13.04/raring [amd64])
Conf usb-modeswitch-data (20120815-2 Ubuntu:13.04/raring [all])
Conf usb-modeswitch (1.2.3+repack0-1ubuntu3 Ubuntu:13.04/raring [amd64])
Conf libloudmouth1-0 (1.4.3-9 Ubuntu:13.04/raring [amd64])
Conf libots0 (0.5.0-2.1 Ubuntu:13.04/raring [amd64])
Conf libtidy-0.99-0 (20091223cvs-1.2 Ubuntu:13.04/raring [amd64])
Conf libwpd-0.9-9 (0.9.6-2 Ubuntu:13.04/raring [amd64])
Conf libwpg-0.2-2 (0.2.1-1build1 Ubuntu:13.04/raring [amd64])
Conf libwps-0.2-2 (0.2.7-1 Ubuntu:13.04/raring [amd64])
Conf abiword-common (2.9.2+svn20120603-8 Ubuntu:13.04/raring [all])
Conf abiword (2.9.2+svn20120603-8 Ubuntu:13.04/raring [amd64])
Conf link-grammar-dictionaries-en (4.7.4-2 Ubuntu:13.04/raring [all])
Conf liblink-grammar4 (4.7.4-2 Ubuntu:13.04/raring [amd64])
Conf abiword-plugin-grammar (2.9.2+svn20120603-8 Ubuntu:13.04/raring [amd64])
Conf libgdome2-0 (0.8.1+debian-4.1build1 Ubuntu:13.04/raring [amd64])
Conf libgdome2-cpp-smart0c2a (0.2.6-6build2 Ubuntu:13.04/raring [amd64])
Conf libt1-5 (5.1.2-3.6 Ubuntu:13.04/raring [amd64])
Conf libgtkmathview0c2a (0.8.0-8 Ubuntu:13.04/raring [amd64])
Conf fonts-lyx (2.0.3-3 Ubuntu:13.04/raring [all])
Conf abiword-plugin-mathview (2.9.2+svn20120603-8 Ubuntu:13.04/raring [amd64])
Conf libaccount-plugin-1.0-0 (0.1.6bzr13.04.05-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf signon-keyring-extension (0.4daily12.12.06-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libsignon-qt1 (8.49-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf signon-ui (0.14-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf signon-plugin-oauth2 (0.15-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf account-plugin-generic-oauth (0.10bzr13.03.26-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf unity-asset-pool (0.8.24daily13.04.24-0ubuntu1 Ubuntu:13.04/raring [all])
Conf account-plugin-facebook (0.10bzr13.03.26-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf account-plugin-flickr (0.10bzr13.03.26-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf account-plugin-google (0.10bzr13.03.26-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf account-plugin-twitter (0.10bzr13.03.26-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf pm-utils (1.4.1-9git1 Ubuntu:13.04/raring [all])
Conf acpi-support (0.141 Ubuntu:13.04/raring [amd64])
Conf linux-sound-base (1.0.25+dfsg-0ubuntu4 Ubuntu:13.04/raring [all])
Conf alsa-base (1.0.25+dfsg-0ubuntu4 Ubuntu:13.04/raring [all])
Conf anacron (2.3-19ubuntu2 Ubuntu:13.04/raring [amd64])
Conf apg (2.2.3.dfsg.1-2build1 Ubuntu:13.04/raring [amd64])
Conf app-install-data (13.04.3 Ubuntu:13.04/raring [all])
Conf appmenu-qt (0.2.7daily13.03.28-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf python3-problem-report (2.9.2-0ubuntu8 Ubuntu:13.04/raring [all])
Conf python3-apport (2.9.2-0ubuntu8 Ubuntu:13.04/raring [all])
Conf apport (2.9.2-0ubuntu8 Ubuntu:13.04/raring [all])
Conf gir1.2-atk-1.0 (2.8.0-1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-pango-1.0 (1.32.5-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-gtk-3.0 (3.6.4-0ubuntu8 Ubuntu:13.04/raring [amd64])
Conf gir1.2-wnck-3.0 (3.4.5-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf apport-gtk (2.9.2-0ubuntu8 Ubuntu:13.04/raring [all])
Conf apport-symptoms (0.19 Ubuntu:13.04/raring [all])
Conf apturl-common (0.5.2ubuntu1 Ubuntu:13.04/raring [amd64])
Conf unattended-upgrades (0.79.3ubuntu7 Ubuntu:13.04/raring [all])
Conf python3-software-properties (0.92.17 Ubuntu:13.04/raring [all])
Conf python3-defer (1.0.6-2 Ubuntu:13.04/raring [all])
Conf python3-aptdaemon (1.0-0ubuntu9 Ubuntu:13.04/raring [all])
Conf libvte-2.90-common (1:0.34.2-0ubuntu2 Ubuntu:13.04/raring [all])
Conf libvte-2.90-9 (1:0.34.2-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf gir1.2-vte-2.90 (1:0.34.2-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf aptdaemon-data (1.0-0ubuntu9 Ubuntu:13.04/raring [all])
Conf python3-aptdaemon.gtk3widgets (1.0-0ubuntu9 Ubuntu:13.04/raring [all])
Conf software-properties-common (0.92.17 Ubuntu:13.04/raring [all])
Conf software-properties-gtk (0.92.17 Ubuntu:13.04/raring [all])
Conf gir1.2-javascriptcoregtk-3.0 (1.10.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-webkit-3.0 (1.10.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf apturl (0.5.2ubuntu1 Ubuntu:13.04/raring [amd64])
Conf audacious (3.3.4-1 Ubuntu:13.04/raring [amd64])
Conf libdaemon0 (0.14-2build1 Ubuntu:13.04/raring [amd64])
Conf avahi-daemon (0.6.31-1ubuntu3 Ubuntu:13.04/raring [amd64])
Conf avahi-utils (0.6.31-1ubuntu3 Ubuntu:13.04/raring [amd64])
Conf binutils (2.23.2-2ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libopenobex1 (1.5-2build2 Ubuntu:13.04/raring [amd64])
Conf obex-data-server (0.4.6-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf python-cairo (1.8.8-1ubuntu4 Ubuntu:13.04/raring [amd64])
Conf python-gobject-2 (2.28.6-11 Ubuntu:13.04/raring [amd64])
Conf python-gtk2 (2.24.0-3ubuntu1 Ubuntu:13.04/raring [amd64])
Conf python-dbus-dev (1.1.1-1ubuntu3 Ubuntu:13.04/raring [all])
Conf python-dbus (1.1.1-1ubuntu3 Ubuntu:13.04/raring [amd64])
Conf python-gobject (3.8.0-2 Ubuntu:13.04/raring [all])
Conf python-notify (0.1.1-3ubuntu1 Ubuntu:13.04/raring [amd64])
Conf xfce4-notifyd (0.2.2-3 Ubuntu:13.04/raring [amd64])
Conf blueman (1.23-0ubuntu4 Ubuntu:13.04/raring [amd64])
Conf bluez-alsa (4.101-0ubuntu8b1 Ubuntu:13.04/raring [amd64])
Conf bluez-cups (4.101-0ubuntu8b1 Ubuntu:13.04/raring [amd64])
Conf brasero-common (3.6.1-0ubuntu2 Ubuntu:13.04/raring [all])
Conf compiz-core (1:0.9.9~daily13.04.18.1~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libdecoration0 (1:0.9.9~daily13.04.18.1~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf compiz-plugins-default (1:0.9.9~daily13.04.18.1~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libprotobuf7 (2.4.1-3ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libcompizconfig0 (1:0.9.9~daily13.04.18.1~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf metacity-common (1:2.34.13-0ubuntu1 Ubuntu:13.04/raring [all])
Conf libmetacity-private0a (1:2.34.13-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf compiz-gnome (1:0.9.9~daily13.04.18.1~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf compiz (1:0.9.9~daily13.04.18.1~13.04-0ubuntu1 Ubuntu:13.04/raring [all])
Conf cracklib-runtime (2.8.22-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf cups-browsed (1.0.34-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf ghostscript-cups (9.07~dfsg2-0ubuntu3 Ubuntu:13.04/raring [amd64])
Conf printer-driver-gutenprint (5.2.9-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf cups-driver-gutenprint (5.2.9-1ubuntu1 Ubuntu:13.04/raring [all])
Conf dc (1.06.95-4ubuntu1 Ubuntu:13.04/raring [amd64])
Conf diffstat (1.55-4 Ubuntu:13.04/raring [amd64])
Conf dmz-cursor-theme (0.4.3 Ubuntu:13.04/raring [all])
Conf genisoimage (9:1.1.11-2ubuntu3 Ubuntu:13.04/raring [amd64])
Conf growisofs (7.1-10build1 Ubuntu:13.04/raring [amd64])
Conf dvd+rw-tools (7.1-10build1 Ubuntu:13.04/raring [amd64])
Conf enchant (1.6.0-7build1 Ubuntu:13.04/raring [amd64])
Conf libkpathsea6 (2012.20120628-4 Ubuntu:13.04/raring [amd64])
Conf libevdocument3-4 (3.6.1-1ubuntu3 Ubuntu:13.04/raring [amd64])
Conf libevview3-3 (3.6.1-1ubuntu3 Ubuntu:13.04/raring [amd64])
Conf libnautilus-extension1a (1:3.6.3-0ubuntu16 Ubuntu:13.04/raring [amd64])
Conf evince-common (3.6.1-1ubuntu3 Ubuntu:13.04/raring [all])
Conf evince (3.6.1-1ubuntu3 Ubuntu:13.04/raring [amd64])
Conf libebackend-1.2-5 (3.6.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libical0 (0.48-2 Ubuntu:13.04/raring [amd64])
Conf libecal-1.2-15 (3.6.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libedata-book-1.2-15 (3.6.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libedata-cal-1.2-18 (3.6.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libgdata-common (0.13.2-2svn1 Ubuntu:13.04/raring [all])
Conf libgdata13 (0.13.2-2svn1 Ubuntu:13.04/raring [amd64])
Conf libgweather-common (3.6.2-0ubuntu1 Ubuntu:13.04/raring [all])
Conf libgweather-3-1 (3.6.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf evolution-data-server (3.6.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libffmpegthumbnailer4 (2.0.8-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf ffmpegthumbnailer (2.0.8-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf zip (3.0-6ubuntu1 Ubuntu:13.04/raring [amd64])
Conf file-roller (3.6.3-1ubuntu4 Ubuntu:13.04/raring [amd64])
Conf firefox (20.0+build1-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf firefox-globalmenu (20.0+build1-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf fonts-khmeros-core (5.0-5ubuntu1 Ubuntu:13.04/raring [all])
Conf fonts-lao (0.0.20060226-8 Ubuntu:13.04/raring [all])
Conf fonts-lklug-sinhala (0.6-2 Ubuntu:13.04/raring [all])
Conf fonts-sil-abyssinica (1.200-3 Ubuntu:13.04/raring [all])
Conf fonts-sil-padauk (2.80-1 Ubuntu:13.04/raring [all])
Conf fonts-tlwg-garuda (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Conf fonts-tlwg-kinnari (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Conf fonts-tlwg-loma (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Conf fonts-tlwg-mono (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Conf fonts-tlwg-norasi (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Conf fonts-tlwg-purisa (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Conf fonts-tlwg-sawasdee (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Conf fonts-tlwg-typewriter (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Conf fonts-tlwg-typist (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Conf fonts-tlwg-typo (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Conf fonts-tlwg-umpush (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Conf fonts-tlwg-waree (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Conf fonts-thai-tlwg (1:0.5.1-1ubuntu1 Ubuntu:13.04/raring [all])
Conf fonts-tibetan-machine (1.901b-4 Ubuntu:13.04/raring [all])
Conf foomatic-db-compressed-ppds (20130308-0ubuntu2 Ubuntu:13.04/raring [all])
Conf freerdp-x11 (1.0.1-2ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gdb (7.6~20130417-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gdebi-core (0.9~exp2 Ubuntu:13.04/raring [all])
Conf gdebi (0.9~exp2 Ubuntu:13.04/raring [all])
Conf libjs-jquery (1.7.2+debian-1ubuntu1 Ubuntu:13.04/raring [all])
Conf libgda-5.0-common (5.0.3-2ubuntu1 Ubuntu:13.04/raring [all])
Conf libgda-5.0-4 (5.0.3-2ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libmusicbrainz3-6 (3.0.2-2.1 Ubuntu:13.04/raring [amd64])
Conf libdca0 (0.0.5-5 Ubuntu:13.04/raring [amd64])
Conf mplayer2 (2.0-554-gf63dbad-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gnome-mplayer (1.0.8-1 Ubuntu:13.04/raring [amd64])
Conf gecko-mediaplayer (1.0.8-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libasprintf-dev (0.18.1.1-10ubuntu3 Ubuntu:13.04/raring [amd64])
Conf libgettextpo-dev (0.18.1.1-10ubuntu3 Ubuntu:13.04/raring [amd64])
Conf gettext (0.18.1.1-10ubuntu3 Ubuntu:13.04/raring [amd64])
Conf ghostscript-x (9.07~dfsg2-0ubuntu3 Ubuntu:13.04/raring [amd64])
Conf gir1.2-dbusmenu-glib-0.4 (12.10.3daily13.02.01-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-goa-1.0 (3.6.2-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-gdata-0.0 (0.13.2-2svn1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-gnomebluetooth-1.0 (3.6.1-0ubuntu3 Ubuntu:13.04/raring [amd64])
Conf gir1.2-gstreamer-1.0 (1.0.6-1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-gst-plugins-base-1.0 (1.0.6-1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-messagingmenu-1.0 (12.10.6daily13.04.09-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-packagekitglib-1.0 (0.7.6-3ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libpeas-common (1.6.2-0ubuntu1 Ubuntu:13.04/raring [all])
Conf libpeas-1.0-0 (1.6.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libgmime-2.6-0 (2.6.13-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libtotem-plparser17 (3.4.4-1 Ubuntu:13.04/raring [amd64])
Conf librhythmbox-core6 (2.98-0ubuntu5 Ubuntu:13.04/raring [amd64])
Conf gir1.2-rb-3.0 (2.98-0ubuntu5 Ubuntu:13.04/raring [amd64])
Conf gir1.2-unity-5.0 (6.90.2daily13.04.05-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gkbd-capplet (3.6.0-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf obexd-client (0.46-1ubuntu3 Ubuntu:13.04/raring [amd64])
Conf gnome-bluetooth (3.6.1-0ubuntu3 Ubuntu:13.04/raring [amd64])
Conf libgnome-control-center1 (1:3.6.3-0ubuntu24 Ubuntu:13.04/raring [amd64])
Conf libgnome-menu-3-0 (3.6.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gnome-control-center-data (1:3.6.3-0ubuntu24 Ubuntu:13.04/raring [all])
Conf gnome-control-center (1:3.6.3-0ubuntu24 Ubuntu:13.04/raring [amd64])
Conf gnome-control-center-signon (0.1.6bzr13.04.05-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gnome-control-center-unity (1.2daily13.04.09-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gnome-desktop-data (1:2.32.1-2ubuntu1 Ubuntu:13.04/raring [all])
Conf upower (0.9.20-1 Ubuntu:13.04/raring [amd64])
Conf gnome-session-bin (3.6.2-0ubuntu5 Ubuntu:13.04/raring [amd64])
Conf liboobs-1-5 (3.0.0-1 Ubuntu:13.04/raring [amd64])
Conf gnome-system-tools (3.0.0-2ubuntu2 Ubuntu:13.04/raring [amd64])
Conf gnome-time-admin (3.0.0-2ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libyelp0 (3.6.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf yelp-xsl (3.6.1-1 Ubuntu:13.04/raring [all])
Conf yelp (3.6.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gnome-user-guide (3.6.2-0ubuntu1 Ubuntu:13.04/raring [all])
Conf gnome-user-share (3.0.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libgoffice-0.10-10-common (0.10.1-1ubuntu2 Ubuntu:13.04/raring [all])
Conf libgoffice-0.10-10 (0.10.1-1ubuntu2 Ubuntu:13.04/raring [amd64])
Conf gnumeric-common (1.12.1-1ubuntu1 Ubuntu:13.04/raring [all])
Conf gnumeric (1.12.1-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gnumeric-doc (1.12.1-1ubuntu1 Ubuntu:13.04/raring [all])
Conf gstreamer0.10-pulseaudio (0.10.31-3+nmu1ubuntu2 Ubuntu:13.04/raring [amd64])
Conf gstreamer0.10-x (0.10.36-1.1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gstreamer1.0-plugins-base (1.0.6-1 Ubuntu:13.04/raring [amd64])
Conf gstreamer1.0-plugins-good (1.0.6-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gstreamer1.0-pulseaudio (1.0.6-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gstreamer1.0-x (1.0.6-1 Ubuntu:13.04/raring [amd64])
Conf libgucharmap-2-90-7 (1:3.6.1-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gucharmap (1:3.6.1-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf hardinfo (0.5.1-1.2ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libsnmp-base (5.4.3~dfsg-2.7ubuntu1 Ubuntu:13.04/raring [all])
Conf libperl5.14 (5.14.2-21 Ubuntu:13.04/raring [amd64])
Conf libsnmp15 (5.4.3~dfsg-2.7ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libhpmud0 (3.13.3-1 Ubuntu:13.04/raring [amd64])
Conf libsane-hpaio (3.13.3-1 Ubuntu:13.04/raring [amd64])
Conf hplip-data (3.13.3-1 Ubuntu:13.04/raring [all])
Conf printer-driver-hpcups (3.13.3-1 Ubuntu:13.04/raring [amd64])
Conf python-imaging-compat (1.1.7+2.0.0-1 Ubuntu:13.04/raring [all])
Conf python-imaging (1.1.7+2.0.0-1 Ubuntu:13.04/raring [amd64])
Conf python-pexpect (2.4-1 Ubuntu:13.04/raring [all])
Conf python-reportlab (2.6-1 Ubuntu:13.04/raring [all])
Conf hplip (3.13.3-1 Ubuntu:13.04/raring [amd64])
Conf hud (13.04.0daily13.04.03-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf hwdata (0.234-1 Ubuntu:13.04/raring [all])
Conf python-ibus (1.4.2-0ubuntu2 Ubuntu:13.04/raring [all])
Conf python-xdg (0.25-2 Ubuntu:13.04/raring [all])
Conf ibus (1.4.2-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf ibus-gtk (1.4.2-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf ibus-gtk3 (1.4.2-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf zenity-common (3.6.0-0ubuntu1 Ubuntu:13.04/raring [all])
Conf zenity (3.6.0-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf im-config (0.21ubuntu3 Ubuntu:13.04/raring [all])
Conf libpanel-applet-4-0 (1:3.6.2-0ubuntu3 Ubuntu:13.04/raring [amd64])
Conf python3-xdg (0.25-2 Ubuntu:13.04/raring [all])
Conf indicator-applet (12.10.2daily13.03.01-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf indicator-application (12.10.1daily13.01.25-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf indicator-application-gtk2 (12.10.0.1-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf indicator-appmenu (13.01.0daily13.03.28-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libtimezonemap1 (0.4.0 Ubuntu:13.04/raring [amd64])
Conf systemd-shim (2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf indicator-datetime (12.10.3daily13.03.26-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf indicator-messages (12.10.6daily13.04.09-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf indicator-power (12.10.6daily13.03.07-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf indicator-session (12.10.5daily13.03.08-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf indicator-sync (12.10.5daily13.03.28.1-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf intltool-debian (0.35.0+20060710.1 Ubuntu:13.04/raring [all])
Conf kerneloops-daemon (0.12+git20090217-3ubuntu3 Ubuntu:13.04/raring [amd64])
Conf aptdaemon (1.0-0ubuntu9 Ubuntu:13.04/raring [all])
Conf language-selector-gnome (0.110 Ubuntu:13.04/raring [all])
Conf libapt-pkg-perl (0.1.26 Ubuntu:13.04/raring [amd64])
Conf libarchive-zip-perl (1.30-6 Ubuntu:13.04/raring [all])
Conf libburn4 (1.2.4-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libjte1 (1.19-1build1 Ubuntu:13.04/raring [amd64])
Conf libisofs6 (1.2.6-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libbrasero-media3-1 (3.6.1-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libcairo-perl (1.103-1 Ubuntu:13.04/raring [amd64])
Conf pulseaudio (1:3.0-0ubuntu6 Ubuntu:13.04/raring [amd64])
Conf libcanberra-pulse (0.30-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libclone-perl (0.31-1build4 Ubuntu:13.04/raring [amd64])
Conf libcolamd2.7.1 (1:3.4.0-3ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libdmapsharing-3.0-2 (2.9.15-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libdpkg-perl (1.16.10ubuntu1 Ubuntu:13.04/raring [all])
Conf libfile-copy-recursive-perl (0.38-1 Ubuntu:13.04/raring [all])
Conf libfile-fcntllock-perl (0.14-2 Ubuntu:13.04/raring [amd64])
Conf libfont-afm-perl (1.20-1 Ubuntu:13.04/raring [all])
Conf libglib-perl (3:1.261-1 Ubuntu:13.04/raring [amd64])
Conf libsgutils2-2 (1.33-1build1 Ubuntu:13.04/raring [amd64])
Conf libgpod-common (0.8.2-7ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libpango-perl (1.224-1 Ubuntu:13.04/raring [amd64])
Conf libgtk2-perl (2:1.244-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libhtml-form-perl (6.03-1 Ubuntu:13.04/raring [all])
Conf libhtml-format-perl (2.10-1 Ubuntu:13.04/raring [all])
Conf libhttp-daemon-perl (6.01-1 Ubuntu:13.04/raring [all])
Conf libio-pty-perl (1:1.08-1build3 Ubuntu:13.04/raring [amd64])
Conf libipc-run-perl (0.92-1 Ubuntu:13.04/raring [all])
Conf libmeanwhile1 (1.0.2-4ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libminiupnpc8 (1.6-3ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libnatpmp1 (20110808-3ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libnotify-bin (0.7.5-2 Ubuntu:13.04/raring [amd64])
Conf libnss-mdns (0.10-3.2build1 Ubuntu:13.04/raring [amd64])
Conf libpaper-utils (1.1.24+nmu2ubuntu2 Ubuntu:13.04/raring [amd64])
Conf libpurple-bin (1:2.10.7-0ubuntu4.1 Ubuntu:13.04/raring [all])
Conf libzephyr4 (3.0.2-2 Ubuntu:13.04/raring [amd64])
Conf libpurple0 (1:2.10.7-0ubuntu4.1 Ubuntu:13.04/raring [amd64])
Conf libtext-levenshtein-perl (0.06~01-2 Ubuntu:13.04/raring [all])
Conf libtie-ixhash-perl (1.22-1 Ubuntu:13.04/raring [all])
Conf libwvstreams4.6-base (4.6.1-6 Ubuntu:13.04/raring [amd64])
Conf libwvstreams4.6-extras (4.6.1-6 Ubuntu:13.04/raring [amd64])
Conf libuniconf4.6 (4.6.1-6 Ubuntu:13.04/raring [amd64])
Conf unity-services (7.0.0daily13.04.18~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libunity-core-6.0-5 (7.0.0daily13.04.18~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libvisual-0.4-plugins (0.4.0.dfsg.1-7build1 Ubuntu:13.04/raring [amd64])
Conf libxfce4util-bin (4.10.0-1 Ubuntu:13.04/raring [amd64])
Conf libxml-xpath-perl (1.13-7 Ubuntu:13.04/raring [all])
Conf libzeitgeist-1.0-1 (0.3.18-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf make (3.81-8.2ubuntu2 Ubuntu:13.04/raring [amd64])
Conf hardening-includes (2.3 Ubuntu:13.04/raring [all])
Conf patchutils (0.3.2-1.1build1 Ubuntu:13.04/raring [amd64])
Conf t1utils (1.37-2 Ubuntu:13.04/raring [amd64])
Conf lintian (2.5.11ubuntu13 Ubuntu:13.04/raring [all])
Conf lp-solve (5.5.0.13-7 Ubuntu:13.04/raring [amd64])
Conf inputattach (1:1.4.3-1 Ubuntu:13.04/raring [amd64])
Conf openprinting-ppds (20130308-0ubuntu2 Ubuntu:13.04/raring [all])
Conf plymouth-label (0.8.8-0ubuntu6.1 Ubuntu:13.04/raring-updates [amd64])
Conf plymouth-theme-lubuntu-logo (0.38.1 Ubuntu:13.04/raring [all])
Conf plymouth-theme-lubuntu-text (0.38.1 Ubuntu:13.04/raring [all])
Conf printer-driver-pnm2ppa (1.13+nondbs-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf rfkill (0.4-2ubuntu1 Ubuntu:13.04/raring [amd64])
Conf ubuntu-extras-keyring (2010.09.27 Ubuntu:13.04/raring [all])
Conf wireless-tools (30~pre9-8ubuntu1 Ubuntu:13.04/raring [amd64])
Conf x11-apps (7.7~3ubuntu1 Ubuntu:13.04/raring [amd64])
Conf x11-session-utils (7.6+2build1 Ubuntu:13.04/raring [amd64])
Conf x11-xfs-utils (7.7~1 Ubuntu:13.04/raring [amd64])
Conf xorg-docs-core (1:1.6-1ubuntu2 Ubuntu:13.04/raring [all])
Conf xinput (1.6.0-1 Ubuntu:13.04/raring [amd64])
Conf xorg (1:7.7+1ubuntu4 Ubuntu:13.04/raring [amd64])
Conf lubuntu-core (0.48 Ubuntu:13.04/raring [amd64])
Conf lubuntu-default-session (0.31 Ubuntu:13.04/raring [all])
Conf guvcview (1.6.0-1~exp1build1 Ubuntu:13.04/raring [amd64])
Conf python-pysqlite2 (2.6.3-3 Ubuntu:13.04/raring [amd64])
Conf python-defer (1.0.6-2 Ubuntu:13.04/raring [all])
Conf python-pkg-resources (0.6.34-0ubuntu1 Ubuntu:13.04/raring [all])
Conf python-aptdaemon (1.0-0ubuntu9 Ubuntu:13.04/raring [all])
Conf python-aptdaemon.gtk3widgets (1.0-0ubuntu9 Ubuntu:13.04/raring [all])
Conf lubuntu-software-center (0.0.5~bzr159-0ubuntu1 Ubuntu:13.04/raring [all])
Conf lxappearance-obconf (0.2.0-4ubuntu1 Ubuntu:13.04/raring [amd64])
Conf python-support (1.0.15 Ubuntu:13.04/raring [all])
Conf python-xklavier (0.4-4 Ubuntu:13.04/raring [amd64])
Conf lxkeymap (0.8.0~bzr25+repack-0ubuntu1 Ubuntu:13.04/raring [all])
Conf lxlauncher (0.2.2-3ubuntu1 Ubuntu:13.04/raring [amd64])
Conf lxpanel-indicator-applet-plugin (0.5.12-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf lxtask (0.1.4-3ubuntu1 Ubuntu:13.04/raring [amd64])
Conf mobile-broadband-provider-info (20130312-1 Ubuntu:13.04/raring [all])
Conf modemmanager (0.6.0.0.really-0ubuntu5 Ubuntu:13.04/raring [amd64])
Conf mtpaint (3.40-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf pidgin-data (1:2.10.7-0ubuntu4.1 Ubuntu:13.04/raring [all])
Conf pidgin (1:2.10.7-0ubuntu4.1 Ubuntu:13.04/raring [amd64])
Conf pidgin-microblog (0.3.0-3 Ubuntu:13.04/raring [amd64])
Conf simple-scan (3.6.1-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf sylpheed-doc (20120629-1 Ubuntu:13.04/raring [all])
Conf sylpheed-i18n (3.3.0-1ubuntu1 Ubuntu:13.04/raring [all])
Conf synaptic (0.80~exp2 Ubuntu:13.04/raring [amd64])
Conf python-cups (1.9.62-0ubuntu3 Ubuntu:13.04/raring [amd64])
Conf python-smbc (1.0.13-0ubuntu4 Ubuntu:13.04/raring [amd64])
Conf python-pycurl (7.19.0-5ubuntu8 Ubuntu:13.04/raring [amd64])
Conf python-cupshelpers (1.3.12+20130308-0ubuntu4 Ubuntu:13.04/raring [all])
Conf system-config-printer-common (1.3.12+20130308-0ubuntu4 Ubuntu:13.04/raring [all])
Conf python-libxml2 (2.9.0+dfsg1-4ubuntu4.1 Ubuntu:13.04/raring-updates [amd64])
Conf python-gnomekeyring (2.32.0+dfsg-2ubuntu1 Ubuntu:13.04/raring [amd64])
Conf python3-aptdaemon.pkcompat (1.0-0ubuntu9 Ubuntu:13.04/raring [all])
Conf system-config-printer-gnome (1.3.12+20130308-0ubuntu4 Ubuntu:13.04/raring [all])
Conf transmission-common (2.77-0ubuntu1 Ubuntu:13.04/raring [all])
Conf transmission-gtk (2.77-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf transmission (2.77-0ubuntu1 Ubuntu:13.04/raring [all])
Conf ttf-wqy-microhei (0.2.0-beta-1.1ubuntu3 Ubuntu:13.04/raring [all])
Conf update-notifier (0.134 Ubuntu:13.04/raring [amd64])
Conf update-manager (1:0.186 Ubuntu:13.04/raring [all])
Conf ubuntu-release-upgrader-gtk (1:0.192.10 Ubuntu:13.04/raring [all])
Conf wvdial (1.61-4.1 Ubuntu:13.04/raring [amd64])
Conf xdg-user-dirs (0.14-0ubuntu5 Ubuntu:13.04/raring [amd64])
Conf xdg-user-dirs-gtk (0.10-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf xfburn (0.4.3-5ubuntu1 Ubuntu:13.04/raring [amd64])
Conf xfce4-power-manager-data (1.2.0-1ubuntu2 Ubuntu:13.04/raring [all])
Conf xfce4-power-manager (1.2.0-1ubuntu2 Ubuntu:13.04/raring [amd64])
Conf xpad (4.1-1ubuntu4 Ubuntu:13.04/raring [amd64])
Conf lubuntu-desktop (0.48 Ubuntu:13.04/raring [amd64])
Conf media-player-info (17-1 Ubuntu:13.04/raring [all])
Conf mousetweaks (3.6.0-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf pptp-linux (1.7.2-7 Ubuntu:13.04/raring [amd64])
Conf network-manager-pptp (0.9.6.0-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf network-manager-pptp-gnome (0.9.6.0-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf pidgin-libnotify (0.14-9ubuntu1 Ubuntu:13.04/raring [amd64])
Conf policykit-desktop-privileges (0.14 Ubuntu:13.04/raring [all])
Conf printer-driver-c2esp (26-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf mscompress (0.3-4 Ubuntu:13.04/raring [amd64])
Conf printer-driver-foo2zjs (20130306dfsg0-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf printer-driver-min12xxw (0.0.9-6ubuntu2 Ubuntu:13.04/raring [amd64])
Conf printer-driver-postscript-hp (3.13.3-1 Ubuntu:13.04/raring [all])
Conf printer-driver-ptouch (1.3-4ubuntu1 Ubuntu:13.04/raring [amd64])
Conf printer-driver-pxljr (1.3+repack0-2build1 Ubuntu:13.04/raring [amd64])
Conf printer-driver-sag-gdi (0.1-3 Ubuntu:13.04/raring [all])
Conf printer-driver-splix (2.0.0+svn308-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf pulseaudio-utils (1:3.0-0ubuntu6 Ubuntu:13.04/raring [amd64])
Conf pulseaudio-module-x11 (1:3.0-0ubuntu6 Ubuntu:13.04/raring [amd64])
Conf python-appindicator (12.10.1daily13.04.15-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf python-gconf (2.28.1+dfsg-1build1 Ubuntu:13.04/raring [amd64])
Conf python-markupsafe (0.15-1build3 Ubuntu:13.04/raring [amd64])
Conf python-mako (0.7.3-1 Ubuntu:13.04/raring [all])
Conf python-renderpm (2.6-1 Ubuntu:13.04/raring [amd64])
Conf python-reportlab-accel (2.6-1 Ubuntu:13.04/raring [amd64])
Conf python-zeitgeist (0.9.5-0ubuntu1 Ubuntu:13.04/raring [all])
Conf python3-httplib2 (0.7.7-1 Ubuntu:13.04/raring [all])
Conf qdbus (4:4.8.4+dfsg-0ubuntu9 Ubuntu:13.04/raring [amd64])
Conf qpdf (4.0.1-2 Ubuntu:13.04/raring [amd64])
Conf radeontool (1.6.2-1.1build1 Ubuntu:13.04/raring [amd64])
Conf librarian0 (0.8.1-5build1 Ubuntu:13.04/raring [amd64])
Conf rarian-compat (0.8.1-5build1 Ubuntu:13.04/raring [amd64])
Conf rhythmbox-data (2.98-0ubuntu5 Ubuntu:13.04/raring [all])
Conf rhythmbox (2.98-0ubuntu5 Ubuntu:13.04/raring [amd64])
Conf rhythmbox-mozilla (2.98-0ubuntu5 Ubuntu:13.04/raring [amd64])
Conf rhythmbox-plugin-cdrecorder (2.98-0ubuntu5 Ubuntu:13.04/raring [amd64])
Conf gir1.2-peas-1.0 (1.6.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf zeitgeist-core (0.9.5-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf rhythmbox-plugin-zeitgeist (2.98-0ubuntu5 Ubuntu:13.04/raring [all])
Conf rhythmbox-plugins (2.98-0ubuntu5 Ubuntu:13.04/raring [amd64])
Conf rtkit (0.10-2build1 Ubuntu:13.04/raring [amd64])
Conf update-inetd (4.43 Ubuntu:13.04/raring [all])
Conf sane-utils (1.0.23-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf system-config-printer-udev (1.3.12+20130308-0ubuntu4 Ubuntu:13.04/raring [amd64])
Conf toshset (1.76-4 Ubuntu:13.04/raring [amd64])
Conf ttf-indic-fonts-core (1:0.5.11ubuntu1 Ubuntu:13.04/raring [all])
Conf ttf-punjabi-fonts (1:0.5.11ubuntu1 Ubuntu:13.04/raring [all])
Conf ubuntu-system-service (0.2.4 Ubuntu:13.04/raring [all])
Conf unity (7.0.0daily13.04.18~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf unity-greeter (13.04.2-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf unity-lens-applications (6.10.0daily13.04.18~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf unity-lens-files (7.0~daily13.04.15-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf unity-lens-music (6.8.1daily13.04.18~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf unity-lens-photos (0.9daily12.12.05-0ubuntu1 Ubuntu:13.04/raring [all])
Conf unity-lens-shopping (6.8.0daily13.03.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf unity-lens-video (0.3.14daily13.04.15-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf python-dirspec (4.2.0-0ubuntu1 Ubuntu:13.04/raring [all])
Conf rhythmbox-ubuntuone (4.2.0-0ubuntu1 Ubuntu:13.04/raring [all])
Conf unity-scope-musicstores (6.8.1daily13.04.18~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf unity-scope-video-remote (0.3.14daily13.04.15-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf vbetool (1.1-3 Ubuntu:13.04/raring [amd64])
Conf xfonts-100dpi (1:1.0.3 Ubuntu:13.04/raring [all])
Conf xfonts-scalable (1:1.0.3-1 Ubuntu:13.04/raring [all])
Conf xul-ext-ubufox (2.6-0ubuntu1 Ubuntu:13.04/raring [all])
Conf zeitgeist-datahub (0.9.5-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf zeitgeist (0.9.5-0ubuntu1 Ubuntu:13.04/raring [all])
Conf appmenu-qt5 (0.2.7daily13.03.28-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf cups-bsd (1.6.2-1ubuntu5 Ubuntu:13.04/raring [amd64])
Conf cups-pk-helper (0.2.4-0ubuntu5 Ubuntu:13.04/raring [amd64])
Conf friends (0.1.3daily13.04.17.1~13.04-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf friends-facebook (0.1.3daily13.04.17.1~13.04-0ubuntu1 Ubuntu:13.04/raring [all])
Conf friends-twitter (0.1.3daily13.04.17.1~13.04-0ubuntu1 Ubuntu:13.04/raring [all])
Conf indicator-bluetooth (0.0.6daily13.02.19-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf indicator-printers (0.1.7daily13.03.01-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf indicator-sound (12.10.2daily13.04.12-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libpam-freerdp (1.0.1-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libwebcam0 (0.2.2-1 Ubuntu:13.04/raring [amd64])
Conf lightdm-remote-session-freerdp (1.0-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf lightdm-remote-session-uccsconfigure (1.1-0ubuntu2 Ubuntu:13.04/raring [amd64])
Conf lm-sensors (1:3.3.2-2ubuntu1 Ubuntu:13.04/raring [amd64])
Conf qtchooser (0.0.1~git20121229.g8f08405-0ubuntu3 Ubuntu:13.04/raring [amd64])
Conf remote-login-service (1.0.0-0ubuntu3 Ubuntu:13.04/raring [amd64])
Conf sessioninstaller (0.20+bzr134-0ubuntu6 Ubuntu:13.04/raring [all])
Conf thin-client-config-agent (0.7 Ubuntu:13.04/raring [all])
Conf unity-lens-friends (0.1.1bzr13.04.12-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf unity-scope-gdrive (0.8daily13.04.15-0ubuntu1 Ubuntu:13.04/raring [all])
Conf uvcdynctrl-data (0.2.2-1 Ubuntu:13.04/raring [all])
Conf uvcdynctrl (0.2.2-1 Ubuntu:13.04/raring [amd64])
```

> Btw, disable fglrx module loading by system boot - in /etc/modprobe.d/blacklist.conf add line *blacklist fglrx*. But keep in mind if you will install proprietary drivers from AMD (Catalyst), you must remove that line.
I added fglrx to the blacklist of my computer, thanks a lot.

---

### Post by xoomer.ap on 2013-05-11
Oh, wait, perhaps problem with your lxdm? I would have tried run lxde from good old gdm: *apt-get install gdm*. Note, after installing gdm you free for back to lxdm: *dpkg-reconfigure gdm*.
If your lxde successfully started - we will know where we have to dig.

---

### Post by Framba on 2013-05-11
Ok, let's try with gdm. I really appreciate your thinking of something I can get back from (well, I really appreciate all your help!), but remember that I have a virtual machine and an old notebook showing the problem. I can do whatever to track down what's wrong before doing anything on the pc I need to fix.

I installed gdm and configured it as default display manager. On the vm it doesn't seem to work, I only have a black background and a clock as mouse pointer, but on the notebook it works!!!

Thanks a lot. I still want to get lxdm working, but this is great. Thank you.

---

### Post by xoomer.ap on 2013-05-11
I am happy to help you. ^_^
Sorry, I am not familiar professionally with LXDE, so suggest you to read man page: [http://manpages.ubuntu.com/manpages/lucid/man1/lxdm.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/lxdm.1.html)
Post here what you have in /etc/lxdm/default.conf, perhaps something will be clearer.

---

### Post by Framba on 2013-05-11
Ok. While I read the man page, this is my /etc/lxdm/default.conf file:
```
[base]
## uncomment and set autologin username to enable autologin
# autologin=dgod

## uncomment and set timeout to enable timeout autologin,
## the value should >=5
# timeout=10

## default session or desktop used when no systemwide config
# session=/usr/bin/startlxde

## uncomment and set to set numlock on your keyboard
# numlock=0

## set this if you don't want to put xauth file at ~/.Xauthority
# xauth_path=/tmp

## greeter used to welcome the user
greeter=/usr/lib/lxdm/lxdm-greeter-gtk

[server]
## arg used to start xserver, not fully function
# arg=/usr/bin/X -background vt1

[display]
## gtk theme used by greeter
gtk_theme=Clearlooks

## background of the greeter
bg=/usr/share/backgrounds/default.png

## if show bottom pane
bottom_pane=1

## if show language select control
lang=1

## if show keyboard layout select control
keyboard=0

## the theme of greeter
theme=Industrial

[input]

[userlist]
## if disable the user list control at greeter
disable=0

## whitelist user
white=

## blacklist user
black=
```

Now that we know the problem is lxdm related I think I was able to find a couple of report of it with google.
I hope I can link this here: [https://bugs.launchpad.net/ubuntu/+source/lxdm/+bug/1103777](https://bugs.launchpad.net/ubuntu/+source/lxdm/+bug/1103777)
In .cache/lxsession/LXDE/run.log there are some (to me) strange errors:
```
Openbox-Message: Requested key "XF86Terminal" does not exist on the display

(xscreensaver-demo:1857): libglade-WARNING **: Could not load support for `gnome': libgnome.so: cannot open shared object file: No such file or directory
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 5890 requests (5890 known processed) with 2 events remaining.
pcmanfm: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

(notification-daemon:1790): Gdk-WARNING **: notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

(polkit-gnome-authentication-agent-1:1787): Gdk-WARNING **: polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.

```

---

### Post by xoomer.ap on 2013-05-11
**It is just my guess:** well, I remember lxde have block screen like from xdm or something else. Maybe it depends from libgnome.so.

Try to *dpkg -S libgnome.so* (there we are searching packet containing libgnome.so. [COLOR="#696969"]On the contrary if you want to know what provides some package you must run* dpkg -L some_package*[/COLOR])

So, when you find packet - try to install it. Desirable with options --no-install-recommends, because you want minimal system. So, hope for your success.

---

### Post by xoomer.ap on 2013-05-11
Upd:
> ## default session or desktop used when no systemwide config
# session=/usr/bin/startlxde
Do you have file "startlxde" in /usr/bin ?

---

### Post by Framba on 2013-05-11
> **xoomer.ap said:**
> Upd:

Do you have file "startlxde" in /usr/bin ?

Quick reply: Yes, I used it when you suggested to start LXDE using xinit from runlevel 3.

Now I start investigating libgnome.so

---

### Post by xoomer.ap on 2013-05-11
> **Framba said:**
> Quick reply: Yes, I used it when you suggested to start LXDE using xinit from runlevel 3.

:roll:

---

### Post by Framba on 2013-05-11
> **xoomer.ap said:**
> :roll:
Sorry, I just wanted to answer your question. I didn't mean to sound snob. :)

```
sudo dpkg -S libgnome.so
dpkg-query: no path found matching pattern *libgnome.so*
```

---

### Post by xoomer.ap on 2013-05-11
It's okay, nevermind too. ^^

Hmm, that time I was on Debian - there was this file in some package with name (if I correct) - gnomeui-0.
Now, when I am at Mint (that based on Ubuntu Quantal Quetzal) I got output of *dpkg -L libgnomeui-0*:
```
/.
/usr
/usr/lib
/usr/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu/libglade
/usr/lib/x86_64-linux-gnu/libglade/2.0
/usr/lib/x86_64-linux-gnu/libglade/2.0/libgnome.so
/usr/lib/x86_64-linux-gnu/libgnomeui-2.so.0.2400.5
/usr/share
/usr/share/doc
/usr/share/doc/libgnomeui-0
/usr/share/doc/libgnomeui-0/README
/usr/share/doc/libgnomeui-0/changelog.Debian.gz
/usr/share/doc/libgnomeui-0/AUTHORS
/usr/share/doc/libgnomeui-0/copyright
/usr/share/doc/libgnomeui-0/NEWS.gz
/usr/lib/x86_64-linux-gnu/libgnomeui-2.so.0
```

so, what if you have same? Than try:
*ln -s /usr/lib/x86_64-linux-gnu/libgnomeui-2.so.0 /usr/lib/x86_64-linux-gnu/libgnomeui.so.0*
or/and
*ln -s /usr/lib/x86_64-linux-gnu/libgnomeui-2.so.0 /usr/lib/x86_64-linux-gnu/libgnomeui.so*

Keep in mind that I don't know differences between /libgnomeui.so and libgnomeui-2.so, etc...

---

### Post by Framba on 2013-05-11
Mmm, no luck with sudo *dpkg -L libgnomeui-0*:
```
dpkg-query: package 'libgnomeui-0' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
```
The only libgnome* I can find in my /usr/lib/x86_*64-linux-gnu/* is libgnome-keyring.so.0

I tried installig libgnomeui-0 using aptitude. *dpkg -L libgnomeui-0 *output is now identical to your.
I also created the two suggested soft links, but the problem is always there.

From the bug report I linked before it seems the problem started with lxdm 0.4.1-0ubuntu6. I was thinking to try to downgrade the package, waiting for a fix.
*apt-cache showpkg lxdm*
```
Package: lxdm
Versions: 
0.4.1-0ubuntu6 (/var/lib/apt/lists/ch.archive.ubuntu.com_ubuntu_dists_raring_universe_binary-amd64_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/ch.archive.ubuntu.com_ubuntu_dists_raring_universe_binary-amd64_Packages
                  MD5: b8e3da45a6f996b0d98b1dc577c5d8a1
 Description Language: en
                 File: /var/lib/apt/lists/ch.archive.ubuntu.com_ubuntu_dists_raring_universe_i18n_Translation-en
                  MD5: b8e3da45a6f996b0d98b1dc577c5d8a1


Reverse Depends: 
  plymouth:i386,lxdm 0.4.1-0ubuntu2
  plymouth,lxdm 0.4.1-0ubuntu2
  lxdm:i386,lxdm
  plymouth:i386,lxdm 0.4.1-0ubuntu2
  lxde,lxdm
  plymouth,lxdm 0.4.1-0ubuntu2
Dependencies: 
0.4.1-0ubuntu6 - libc6 (2 2.14) libcairo2 (2 1.2.4) libck-connector0 (2 0.2.1) libdbus-1-3 (2 1.0.2) libgdk-pixbuf2.0-0 (2 2.22.0) libglib2.0-0 (2 2.24.0) libgtk2.0-0 (2 2.24.0) libpam0g (2 0.99.7.1) libpango1.0-0 (2 1.14.0) libx11-6 (0 (null)) libxcb1 (0 (null)) debconf (18 1.2.9) debconf-2.0 (0 (null)) upstart-job (0 (null)) x11-utils (16 (null)) xbase-clients (16 (null)) xmessage (0 (null)) lsb-base (2 3.0-6) gtk2-engines-pixbuf (0 (null)) librsvg2-common (0 (null)) libpam-runtime (2 0.76-14) libpam-modules (0 (null)) iso-codes (0 (null)) lxsession (2 0.4.0) lxde-common (0 (null)) locales-all (0 (null)) lxdm:i386 (0 (null)) 
Provides: 
0.4.1-0ubuntu6 - x-display-manager 
Reverse Provides:
```
Does the lack of "Reverse Provides" mean I can't go back to a previous version (at least not using apt-get or aptitude)?

---

### Post by xoomer.ap on 2013-05-11
> **Framba said:**
> 
Does the lack of "Reverse Provides" mean I can't go back to a previous version (at least not using apt-get or aptitude)?

I don't know what means that field... But [here]("http://www.howtogeek.com/117929/how-to-downgrade-packages-on-ubuntu/") is howto for downgrade package from CLI.

Uh, 00:05 at my clocks - sorry but I have to go to sleep. I'll check this thread tomorrow, maybe we can work something out.

Peace to you.

---

### Post by Framba on 2013-05-12
> **xoomer.ap said:**
> I don't know what means that field... But [here]("http://www.howtogeek.com/117929/how-to-downgrade-packages-on-ubuntu/") is howto for downgrade package from CLI.

Yes, this is the same page I read yesterday. Maybe the important field is "Provides" and not "Reverse Provides", but again I have no alternatives.

> Uh, 00:05 at my clocks - sorry but I have to go to sleep. I'll check this thread tomorrow, maybe we can work something out.

Peace to you.

Thank you very much for all your help.
At the moment I think I can work well using GDM: it's light and it works. I checked for LightDM but it would require about half a GB of additional packages (friends-facebook, friends-twitter... WTF!), so "No thanks!".

If you or anybody else wants to help me to dig deeper to find a fix I would be grateful, and maybe this can help somebody else, but now I can work again with this computer (a small "server" with a few virtual machines).

Thank you very much again!

---

### Post by xoomer.ap on 2013-05-12
It's my pleasure. I'll try repeat your doing and let you know today or tomorrow.

---

### Post by xoomer.ap on 2013-05-14
Sorry for late, **Framba**, I only just finished my try for reconstruct your situation. I got something similar, but there was dark-blue screen and of cource mouse pointer.
Before this I installed minimal system without any additional packages and executed *apt-get install lxde*. That's all.
[http://img856.imageshack.us/img856/6262/20130514215001.png]("http://img856.imageshack.us/img856/6262/20130514215001.png")

---

### Post by Framba on 2013-05-15
Yes, this is exactly what shows me when I use ldxm for logging in: dark blue background and mouse pointer.

---

### Post by Rexilion on 2013-05-15
I installed LXDE alongside a minimum install of Ubuntu with XFCE. I used the server iso with cli.seed. Here, LXDE misbehaved as well with a black background on startup. Once I changed the **icon set** (!) back to normal Gnome instead of Faenza (which was default) I had a desktop and a background.

I suggest you install the default Gnome icons and go from there. I know, it does not sound logical, but I ditched the software and went back to XFCE because of it. I disliked lxdesktop's very limited functionality.

---

### Post by Framba on 2013-05-16
> **Rexilion said:**
> I installed LXDE alongside a minimum install of Ubuntu with XFCE. I used the server iso with cli.seed. Here, LXDE misbehaved as well with a black background on startup. Once I changed the **icon set** (!) back to normal Gnome instead of Faenza (which was default) I had a desktop and a background.

I suggest you install the default Gnome icons and go from there. I know, it does not sound logical, but I ditched the software and went back to XFCE because of it. I disliked lxdesktop's very limited functionality.
Hi Rexilion, thank you for your hint. I tried to change icon set using "Customize Look and Feel", but when I use lxdm to log in I obtain only blue background and a mouse pointer, as usual.
Thanks to xoomer.ap I found that the problem is lxdm and not lxde as I thought at first. Using gdm everything works fine, now I'm just curious to understand what is wrong with lxdm. I just need a few workspaces and to be able to configure keyboard shortcuts, so lxde is even too much and I'm thinking to go back to plain Openbox (this gave me some stability problems with Ubuntu 12.10, maybe now it has been fixed).

---

### Post by Rexilion on 2013-05-16
> **Framba said:**
> Hi Rexilion, thank you for your hint. I tried to change icon set using "Customize Look and Feel", but when I use lxdm to log in I obtain only blue background and a mouse pointer, as usual.
Thanks to xoomer.ap I found that the problem is lxdm and not lxde as I thought at first. Using gdm everything works fine, now I'm just curious to understand what is wrong with lxdm. I just need a few workspaces and to be able to configure keyboard shortcuts, so lxde is even too much and I'm thinking to go back to plain Openbox (this gave me some stability problems with Ubuntu 12.10, maybe now it has been fixed).

I suggest you try looking at the environment variables of each session:

```
set
```

And compare the differences. Furthermore, I use startx as 'login manager' and it had issue's handling consolekit properly. I had to modify it's PAM file. To diagnose that, use:

```
ck-list-sessions
```

And, again, compare the output for each DM.

    Good luck!

---

### Post by Framba on 2013-05-17
Ok, I'm comparing the output of *set* and *ck-list-session* collected in tty1 while running gdm and lxdm.

*set* shows only two differences:
```
PIPESTATUS=([0]="1")   (gdm)
PIPESTATUS=([0]="0")   (lxdm)

XDG_SESSION_COOKIE=665...79_=']'   (gdm)
XDG_SESSION_COOKIE=665...25_=-lh   (lxdm)
```

*ck-list-session* with lxdm shows only a session (/dev/tty1), while with gdm I have 2 sessions, tty1 and X11.

I'm using google to look for PIPE_STATUS and XDG_SESSION_COOKIE details, but the absence of X11 session in *ck-list-session*'s output seems more interesting.

---

### Post by Rexilion on 2013-05-17
Provide us:

/etc/pam.d/lxde
/etc/pam.d/gdm

I'm not sure about the filenames, maybe they are prefixed or suffixed. But you should provide the pam configuration file that comes with the DM.

GDM handles ConsoleKit internally (without PAM) (or used to), but LXDE will have it's hooks in PAM (I guess).

My best bet is that this is the root of your problem.

---

### Post by Framba on 2013-05-17
```
cat /etc/pam.d/gdm
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required        pam_limits.so
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional        pam_gnome_keyring.so auto_start
session required        pam_env.so readenv=1
session required        pam_env.so readenv=1 user_readenv=1 envfile=/etc/default/locale
@include common-password

cat /etc/pam.d/lxdm
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required        pam_limits.so
@include common-session-noninteractive
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional        pam_gnome_keyring.so auto_start
@include common-password
```

---

### Post by Rexilion on 2013-05-18
Make sure you are comfortable with editing in a TTY (with a LiveCD). My modifications could (in worst case) lock you out of your own system. However my modification will, as far as I know, not do that. But be prepared!

Done with the disclaimer, moving on...

First, let's install what we need:

```
aptitude -yR install libpam-ck-connector
```

Inspecting your PAM, I see that it's using additional files. So:

```
@include common-session-noninteractive
```

Hence:

/etc/pam.d/common-session-noninteractive
```
< snip >
# and here are more per-package modules (the "Additional" block)
session	required	pam_unix.so 
# end of pam-auth-update config
```

Change it to:

```
< snip >
# and here are more per-package modules (the "Additional" block)
session	required	pam_unix.so 
[B]session optional	pam_loginuid.so
session	optional	pam_ck_connector.so nox11[/B]
# end of pam-auth-update config
```

If any of the bold lines is already there. No problem, just leave it there and add the additional line who is missing. If they are both already there let me know. However, **make sure you do loginuid first and then pam_ck_connector**.

EDIT1: Sidenote: Why is lxdm using the non-interactive version? :shock:

---

### Post by Framba on 2013-05-19
No problem with the TTYs here, thanks.
I don't know why lxdm is using the non-interactive version, but I added both lines: the behaviour is always the same.

Thank you anyway.

---

### Post by Rexilion on 2013-05-19
Could you please elaborate on exactly what is the same? The output of ck-list-sessions should now include an X11 entry under LXDE. Otherwise I failed to achieve behaviour I consider optimal for your situation.

---

### Post by Framba on 2013-05-19
I'm sorry, I'll try to be more precise.

Whenever I try to login using lxdm, after login and password I obtain a solid blue background and the mouse pointer. The pointer is moving, but clicks do nothing (no Openbox menu).
Xoomer.ap obtained the same with a virtual machine and posted a picture: [http://img856.imageshack.us/img856/6...0514215001.png]("http://img856.imageshack.us/img856/6262/20130514215001.png")
As I said in my first post, I had this problem after update from Ubuntu 12.10 64 bit to 13.04. I started from the mini iso and added lxde. The same occur if I start from the new 13.04 64 bit mini iso, in virtual machine or on another computer. With gdm everything works fine.

After the addition of the lines you suggested, the differences in the output of *set* disappeared, but with lxdm *ck-list-session* continues to show only the tty session (no X11).

---

### Post by Rexilion on 2013-05-19
When you start LXDE, do you see a process called 'ck-launch-session' ?

---

### Post by Framba on 2013-05-19
> **Rexilion said:**
> When you start LXDE, do you see a process called 'ck-launch-session' ?
No, I do not have any ck-launch-session running prior or after my login with lxdm.
The only new processes that showed up with a *ps -e* after loggin in (i.e. while I have the solid background and the mouse pointer) are:
```
gnome-keyring-d
lxdm-binary
PreLogin <defunct>
```
And after a minute or so I found also 'kworker/0:0'.

---

### Post by Rexilion on 2013-05-20
I'm trying this dirty hack just to test something. We create a file called startlxde_custom in /usr/bin. Modify /etc/lxdm/lxdm.conf to make that the default session.

/usr/bin/startlxde_custom
```
exec dbus-launch ck-launch-session /usr/bin/startlxde
```

```
chown 0:0 /usr/bin/startlxde_custom
chmod 755 /usr/bin/startlxde_custom
```

/etc/lxdm/lxdm.conf
Replace:
```
# session=/usr/bin/startlxde
```

with:
```
session=/usr/bin/startlxde_custom
```

Now try again please.

---

### Post by Framba on 2013-05-20
I always get the solid blue background, and also the same processes (no ck-launch-session).

---

### Post by Rexilion on 2013-05-20
Then it seems that lxdm did not use /usr/bin/startlxde_custom . Can you look for an 'default' option or something?

There should be a ck-launch-session and dbus-launch session when startlxde_custom is used as a session initiator.

---

### Post by Framba on 2013-05-20
Trying to get around this, I moved /usr/bin/startlxde to /usr/bin/startlxde_original and /usr/bin/startlxde_custom to /usr/bin/startlxde (and modified the last one to launch "original"), but nothing changed.

---

### Post by Framba on 2013-05-20
I'm going to try Ubuntu mini 12.10 in a vm to check the differences in config files.

---

### Post by Rexilion on 2013-05-20
Maybe try to look at /usr/share/xsessions and see what is in there.

---

### Post by Framba on 2013-05-20
I'm comparing 12.10 and 13.04.
/etc/pam.d/lxdm is equal (also the '@include common-session-noninteractive).
No differences with *ck-list-session*, while *set* has some:

 ```
diff set.lxdm.13.04.txt set.lxdm.12.10.txt 
10,12c10,12
< BASH_VERSINFO=([0]="4" [1]="2" [2]="45" [3]="1" [4]="release" [5]="x86_64-pc-linux-gnu")
< BASH_VERSION='4.2.45(1)-release'
< COLUMNS=128
---
> BASH_VERSINFO=([0]="4" [1]="2" [2]="37" [3]="1" [4]="release" [5]="x86_64-pc-linux-gnu")
> BASH_VERSION='4.2.37(1)-release'
> COLUMNS=100
18,19c18,19
< HISTFILESIZE=5000
< HISTSIZE=5000
---
> HISTFILESIZE=2000
> HISTSIZE=1000
29c29
< LINES=48
---
> LINES=37
39,41c39,40
< PIPESTATUS=([0]="**0**")
< PPID=863
< PROMPT_COMMAND='history -a'
---
> PIPESTATUS=([0]="**1**")
> PPID=747
49,50d47
< SSH_AGENT_PID=3385
< SSH_AUTH_SOCK=/tmp/ssh-jozqsA3384/agent.3384
54,56c51,53
< XDG_SESSION_COOKIE=6653bbde3e4a1159d6518b22518b7962-1368787107.532424-2038630725
< _=**-lh**
< __colormgr_commandlist=$'\n    create-device\n    create-profile\n    delete-device\n    delete-profile\n    device-add-profile\n    device-get-default-profile\n    device-get-profile-for-qualifier\n    device-inhibit\n    device-make-profile-default\n    device-set-kind\n    device-set-model\n    device-set-serial\n    device-set-vendor\n    **device-set-enabled\n**    find-device\n    find-device-by-property\n    find-profile\n    find-profile-by-filename\n    get-devices\n    get-devices-by-kind\n    get-profiles\n    get-sensor-reading\n    get-sensors\n    get-standard-space\n    profile-set-filename\n    profile-set-qualifier\n    sensor-lock\n    sensor-set-options\n    '
---
> XDG_SESSION_COOKIE=2735a62251d594061e8491e4519a0fa4-1369055538.889130-659026895
> _=**']'**
> __colormgr_commandlist=$'\n    create-device\n    create-profile\n    delete-device\n    delete-profile\n    device-add-profile\n    device-get-default-profile\n    device-get-profile-for-qualifier\n    device-inhibit\n    device-make-profile-default\n    device-set-kind\n    device-set-model\n    device-set-serial\n    device-set-vendor\n    find-device\n    find-device-by-property\n    find-profile\n    find-profile-by-filename\n    get-devices\n    get-devices-by-kind\n    get-profiles\n    get-sensor-reading\n    get-sensors\n    get-standard-space\n    profile-set-filename\n    profile-set-qualifier\n    sensor-lock\n    sensor-set-options\n    '
602,607d598
< **}**
< **_desktop_file_validate () **
< **{ **
<     **COMPRELY=();**
<     **cur=${COMP_WORDS[COMP_CWORD]};**
<     **_filedir '@(desktop)'**
```

---

### Post by Framba on 2013-05-20
> **Rexilion said:**
> Maybe try to look at /usr/share/xsessions and see what is in there.
I don't know what to look for, but there are 4 files:
LXDE.desktop
openbox.desktop
openbox-gnome.desktop
openbox-kde.desktop

These files are identical in 12.10 and 13.04.

---

