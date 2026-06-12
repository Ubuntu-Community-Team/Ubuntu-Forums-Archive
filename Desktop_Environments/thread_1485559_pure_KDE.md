---
title: "pure KDE"
date: 2010-05-17
forum: Desktop Environments
---

### Post by Kubischbuntu on 2010-05-17
Hi,

since somehow my support had dried up on the other thread I thought I ask again here. I am sure somebody may be able to help me.

So here is my problem:

I originally installed Ubuntu Jaunty - and then decided to try the KDE  desktop so installed that. I have not used gnome since and actually ran  the update to Lucid in KDE. 

 I have now decided that I like KDE better so want to get rid of all the  gnomes. Given this history - how can I do  that - or do I need to do a clean Kubuntu install??

I go the advice to follow the method outlined here: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

I tried that and got:

sudo] password for kubisch: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz is not installed, so not removed
Package compiz-core is not installed, so not removed
Package compiz-fusion-plugins-main is not installed, so not removed
Package compiz-gnome is not installed, so not removed
Package compiz-plugins is not installed, so not removed
Package compizconfig-backend-gconf is not installed, so not removed
Package evolution is not installed, so not removed
Package evolution-couchdb is not installed, so not removed
Package evolution-exchange is not installed, so not removed
Package evolution-indicator is not installed, so not removed
Package evolution-plugins is not installed, so not removed
Package libcompizconfig0 is not installed, so not removed
Package notification-daemon is not installed, so not removed
Package scrollkeeper is not installed, so not removed
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxine1: Depends: libxine1-x (= 1.1.17-1ubuntu3) but it is not going  to be installed
E: Broken packages
kubisch@squarebear:~$ 

I then go the following advice:

Usually that kind  of error message indicates you have conflicting software sources  (otherwise known as software repositories--basically online servers  Ubuntu uses to fetch software you want to install).

Can you post the output of these commands?  	Code:
 	sudo apt-get update
cat /etc/apt/sources.list 

 		                   		  		  		 		 			 				So here it is:

For the first one I get:

kubisch@squarebear:~$ sudo apt-get update
[sudo] password for kubisch: 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid/main Translation-en_NZ
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid/restricted Translation-en_NZ
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid/universe Translation-en_NZ
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid/multiverse Translation-en_NZ
Get:1 [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid-updates/main Translation-en_NZ
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid-updates/restricted Translation-en_NZ
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid-updates/universe Translation-en_NZ
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid-updates/multiverse Translation-en_NZ
Get:2 [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid-security Release.gpg [189B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid-security/main Translation-en_NZ                                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid-security/restricted Translation-en_NZ                               
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid-security/universe Translation-en_NZ                                 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid-security/multiverse Translation-en_NZ                               
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid Release                                                                     
Get:3 [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid-updates Release [38.5kB]                                                  
Get:4 [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid-security Release [32.5kB]                                                 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid/main Packages                                                               
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid/restricted Packages                                                         
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid/main Sources                                                                
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid/restricted Sources                                                          
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid/universe Packages                                                           
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid/universe Sources                                                            
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid/multiverse Packages                                                         
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid/multiverse Sources                                                          
Get:5 [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid-updates/main Packages [115kB]                                             
Get:6 [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid-updates/restricted Packages [14B]                                         
Get:7 [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid-updates/main Sources [49.9kB]                                             
Get:8 [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid-updates/restricted Sources [14B]                                          
Get:9 [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid-updates/universe Packages [8,371B]                                        
Get:10 [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid-updates/universe Sources [2,392B]                                        
Get:11 [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid-updates/multiverse Packages [14B]                                        
Get:12 [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid-updates/multiverse Sources [14B]                                         
Get:13 [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid-security/main Packages [2,067B]                                          
Get:14 [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid-security/restricted Packages [14B]                                       
Get:15 [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid-security/main Sources [1,300B]                                           
Get:16 [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid-security/restricted Sources [14B]                                        
Get:17 [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid-security/universe Packages [815B]                                        
Get:18 [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid-security/universe Sources [780B]                                         
Get:19 [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid-security/multiverse Packages [14B]                                       
Get:20 [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  lucid-security/multiverse Sources [14B]                                        
Fetched 252kB in 16s (15.4kB/s)                                                                                 
Reading package lists... Done


For the second one I get: 
kubisch@squarebear:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386  (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for  how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the  Ubuntu
## team. Also, please note that software in universe WILL NOT receive  any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the  Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as  to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid-updates multiverse

## Uncomment the following two lines to add software from the  'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it  includes
## newer versions of some applications which may provide useful  features.
## Also, please note that software in backports WILL NOT receive any  review
## or updates from the Ubuntu security team.
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/)  jaunty-backports main restricted universe multiverse
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/)  jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and  the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)  jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)  jaunty partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid-security multiverse
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/)  karmic free non-free


Unfortunately the source of wisdom has not responded since - so if anybody else here is able to  shed some light on this I would be most grateful!

Thank you


__________________

---

### Post by Zorael on 2010-05-17
Try using **aptitude** instead of apt-get. It is much better at resolving dependencies.
```
$ sudo aptitude purge adium-theme-ubuntu aisleriot alacarte app-install-data-partner apport-gtk aptdaemon at-spi binfmt-support binutils bluez-gstreamer branding-ubuntu brasero brasero-common brltty-x11 capplets-data checkbox checkbox-gtk cli-common compiz compiz-core compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf computer-janitor computer-janitor-gtk couchdb-bin dcraw desktop-file-utils desktopcouch dmz-cursor-theme doc-base docbook-xml empathy empathy-common eog erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl esound-clients esound-common espeak espeak-data evince evolution evolution-common evolution-couchdb evolution-data-server evolution-data-server-common evolution-exchange evolution-indicator evolution-plugins evolution-webcal example-content f-spot file-roller firefox firefox-branding firefox-gnome-support gamin gbrainy gcalctool gcc gcc-4.4 gconf-defaults-service gconf-editor gdebi gdm gdm-guest-session gedit gedit-common gksu gnome-about gnome-accessibility-themes gnome-applets gnome-applets-data gnome-bluetooth gnome-codec-install gnome-control-center gnome-desktop-data gnome-disk-utility gnome-doc-utils gnome-games-common gnome-icon-theme gnome-mag gnome-mahjongg gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-power-manager gnome-screensaver gnome-session gnome-session-bin gnome-session-canberra gnome-settings-daemon gnome-sudoku gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu gnome-user-guide gnome-user-share gnome-utils gnomine gstreamer0.10-alsa gstreamer0.10-gnonlin gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse gwibber gwibber-service humanity-icon-theme ibus ibus-gtk ibus-m17n ibus-table imagemagick indicator-applet indicator-applet-session indicator-application indicator-me indicator-messages indicator-session indicator-sound jockey-gtk language-selector launchpad-integration libanthy0 libappindicator0 libart-2.0-2 libart2.0-cil libasound2-plugins libatspi1.0-0 libaudiofile0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrasero-media0 libc-dev-bin libc6-dev libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio10 libclutter-1.0-0 libclutter-gtk-0.10-0 libcompizconfig0 libcouchdb-glib-1.0-2 libcroco3 libcryptui0 libcurl3 libdbusmenu-gtk1 libdecoration0 libdesktopcouch-glib-1.0-2 libdevkit-power-gobject1 libdotconf1.0 libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13 libesd0 libespeak1 libevdocument2 libevent-1.4-2 libevview2 libexchange-storage1.2-3 libexempi3 libflickrnet2.2-cil libfreezethaw-perl libgail-common libgail-gnome-module libgail18 libgamin0 libgconf2.0-cil libgd2-xpm libgdata-common libgdata-google1.2-1 libgdata1.2-1 libgdata6 libgdict-1.0-6 libgdiplus libgdu-gtk0 libgdu0 libgksu2-0 libglade2.0-cil libglib-perl libglib2.0-cil libglib2.0-data libglibmm-2.4-1c2a libglitz-glx1 libglitz1 libgmime-2.4-2 libgmime2.4-cil libgnome-bluetooth7 libgnome-desktop-2-17 libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomekbd-common libgnomekbd4 libgnomepanel2.24-cil libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgoocanvas-common libgoocanvas3 libgraphviz4 libgsf-1-114 libgsf-1-common libgssdp-1.0-2 libgstfarsight0.10-0 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgupnp-1.0-3 libgupnp-igd-1.0-2 libgvfscommon0 libgweather-common libgweather1 libibus1 libido-0.1-0 libiec61883-0 libindicate-gtk2 libindicator0 libjson-glib-1.0-0 libkpathsea5 liblaunchpad-integration1 liblaunchpad-integration1.0-cil liblircclient0 liblouis-data liblouis0 liblpint-bonobo0 libm17n-0 libmagickcore2-extra libmetacity-private0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-i18n-west2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-runtime2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnice0 libnotify1 libnunit2.4-cil liboil0.3 liboobs-1-4 libotf0 libpanel-applet2-0 libpango-perl libpangomm-1.4-1 libpisock9 libpisync1 libpolkit-gtk-1-0 libpoppler-glib4 libportaudio2 libprotobuf5 libprotoc5 libproxy0 libpst4 libpulse-browse0 libpurple-bin libpurple0 librarian0 libraw1394-11 librsvg2-2 librsvg2-common libsctp1 libsdl1.2debian-pulseaudio libsexy2 libshout3 libsilc-1.1-2 libsilcclient-1.1-3 libsoup-gnome2.4-1 libsoup2.4-1 libspeechd2 libspeexdsp1 libsqlite0 libstartup-notification0 libtdb1 libtelepathy-farsight0 libtelepathy-glib0 libtie-ixhash-perl libtotem-plparser17 libubuntuone-1.0-1 libunique-1.0-0 libupower-glib1 libuuid-perl libvisual-0.4-0 libvisual-0.4-plugins libvte-common libvte9 libwebkit-1.0-2 libwebkit-1.0-common libwmf0.2-7 libwmf0.2-7-gtk libwnck-common libwnck22 libxcb-atom1 libxcb-aux0 libxcb-event1 libxml-twig-perl libxml-xpath-perl libxres1 libzephyr4 light-themes linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic linux-headers-generic linux-libc-dev lksctp-tools m17n-contrib m17n-db manpages-dev media-player-info metacity metacity-common mobile-broadband-provider-info mono-2.0-gac mono-gac mono-runtime mousetweaks nautilus nautilus-data nautilus-sendto nautilus-sendto-empathy nautilus-share network-manager-gnome notification-daemon notify-osd notify-osd-icons obexd-client onboard openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-style-human pitivi pkg-config plymouth-theme-ubuntu-logo policykit-1-gnome protobuf-compiler pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils python-appindicator python-aptdaemon python-aptdaemon-gtk python-avahi python-brlapi python-cairo python-configglue python-couchdb python-crypto python-desktopcouch python-desktopcouch-records python-egenix-mxdatetime python-egenix-mxtools python-farsight python-fstab python-gconf python-glade2 python-gmenu python-gnome2 python-gnomeapplet python-gnomecanvas python-gnomekeyring python-gst0.10 python-gtk2 python-gtksourceview2 python-gtkspell python-ibus python-indicate python-launchpad-integration python-libxml2 python-louis python-mako python-notify python-openssl python-pam python-papyon python-protobuf python-pyatspi python-pycurl python-pygoocanvas python-pyinotify python-pyorbit python-rdflib python-serial python-speechd python-telepathy python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntuone python-ubuntuone-client python-ubuntuone-storageprotocol python-virtkey python-vte python-webkit python-wnck quadrapassel rarian-compat rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins rhythmbox-ubuntuone-music-store rtkit screen-resolution-extra screensaver-default-images scrollkeeper seahorse sgml-data simple-scan software-center software-properties-gtk speech-dispatcher ssh-askpass-gnome synaptic system-config-printer-gnome system-tools-backends telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-mission-control-5 telepathy-salut tomboy totem totem-common totem-mozilla totem-plugins transmission-common transmission-gtk tsclient ttf-liberation ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono ubuntu-sounds ubuntu-system-service ubuntu-wallpapers ubuntuone-client ubuntuone-client-gnome update-manager update-notifier upower usb-creator-gtk vinagre vino whois xdg-user-dirs-gtk xscreensaver-data xscreensaver-gl xsltproc xulrunner-1.9.2 yelp zenity -P && sudo aptitude install kubuntu-desktop
```
It will list potential dependency issues and *suggest solutions*, which you can accept or refuse. As that psychocats page says this may remove stuff that you don't want it to. You could try to refuse the initial solutions and see if it suggests any better, perhaps keeping some applications by neglecting to remove some packages.

If you have any KDE3 applications still installed, they will be removed (due to **kdelibs4c2a** being purged). Likewise if you installed the **kscreensaver-xsavers** package to get more screensavers, it will be removed due to depending on **xscreensaver-data**.

Example of the first suggested solution on my machine;
```
The following actions will resolve these dependencies:
apt-file
arandr
build-essential
comix
curl
debhelper
devscripts
dpkg-dev
dshowserver
ffmpegthumbnailer
findimagedupes
g++
g++-4.4
gettext
gimp
gimp-resynthesizer
gparted
graphviz
gtkpod
intltool-debian
kamoso
kdelibs4c2a
kffmpegthumbnailer
kscreensaver-xsavers
kwavecontrol
libavcodec-extra-52
libavformat52
libdbusmenu-tools
libffmpegthumbnailer3
libffmpegthumbnailer4
libgcrypt11-dev
libgegl-0.0-0
libglib2.0-dev
libgnutls-dev
libgraphics-magick-perl
libgraphicsmagick3
libimobiledevice-dev
libiso9660-7
libplist-dev
libschroedinger-1.0-0
libstdc++6-4.4-dev
libvcdinfo0
libxine1-ffmpeg
libxml2-dev
lintian
mencoder
mplayer
mysql-admin
mysql-query-browser
phonon-backend-gstreamer
phonon-backend-mplayer
plasma-wallpaper-video
po-debconf
quilt
smplayer
smplayer-themes
uim
uim-anthy
uim-gtk2.0
vlc
vlc-nox
wine1.2
xrestop
zlib1g-dev

Score is -6251
```

At any rate it's a good start from which you can start reinstalling stuff.

---

### Post by Kubischbuntu on 2010-05-18
Hi,

here is what I get back:


The following packages are BROKEN:
  adobe-flashplugin apturl compiz-fusion-plugins-extra compiz-kde compizconfig-backend-kconfig 
  compizconfig-settings-manager dkms ekiga festival firefox-3.0 firefox-3.0-gnome-support firefox-3.5 
  gcc-4.3 gcompris gimp gir1.0-clutter-1.0 gir1.0-clutter-gtk-0.10 glchess glines gnect gnibbles gnobots2 
  gnome-games gnome-pilot gnome-pilot-conduits gnome-user-guide-en gnotravex gnotski gstreamer0.10-ffmpeg 
  gstreamer0.10-gnomevfs gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gtali human-theme iagno 
  kdelibs4c2a kinfocenter language-support-translations-en libdc1394-22 libemeraldengine0 libesd-alsa0 
  libestools1.2 libgegl-0.0-0 libgmime2.2a-cil libgnome-speech7 libgnomeprint2.2-0 libgnomeprintui2.2-0 
  libgnomevfs2-bin libgtkhtml2-0 libgtksourceview1.0-0 libiso9660-7 libmono-data2.0-cil 
  libmono-getoptions2.0-cil libmono-i18n2.0-cil libopal3.6.6 libschroedinger-1.0-0 libsdl1.2debian libseed0 
  libswfdec-0.8-0 libvcdinfo0 lightsoff mirage moovida-plugins-bad nvidia-173 nvidia-settings pcmanfm-nohal 
  pidgin pidgin-libnotify pysdm python-axiom python-bugbuddy python-coherence python-compizconfig 
  python-epsilon python-evince python-evolution python-gnome2-desktop python-gnomedesktop python-gnomeprint 
  python-gtop python-mediaprofiles python-metacity python-moovida python-nevow python-pgm python-rsvg 
  python-sexy python-totem-plparser python-twisted-conch python-twisted-web2 seahorse-plugins 
  soundconverter startupmanager swell-foop swfdec-mozilla tangerine-icon-theme thunderbird totem-gstreamer 
  tuxpaint usb-creator vlc vlc-nox wine1.2 
The following packages will be REMOVED:
  adium-theme-ubuntu{p} aisleriot{p} alacarte{p} app-install-data-partner{p} apport-gtk{p} aptdaemon{p} 
  at-spi{p} binfmt-support{p} binutils{p} bluez-gstreamer{p} branding-ubuntu{p} brasero{p} 
  brasero-common{p} brltty-x11{p} capplets-data{p} checkbox{p} checkbox-gtk{p} cli-common{p} compiz-core{p} 
  compiz-fusion-plugins-main{p} compiz-gnome{p} compiz-plugins{p} computer-janitor{p} 
  computer-janitor-gtk{p} couchdb-bin{p} dcraw{p} desktop-file-utils{p} desktopcouch{p} dmz-cursor-theme{p} 
  doc-base{p} docbook-xml{p} empathy{p} empathy-common{p} eog{p} erlang-base{p} erlang-crypto{p} 
  erlang-inets{p} erlang-mnesia{p} erlang-public-key{p} erlang-runtime-tools{p} erlang-ssl{p} 
  erlang-syntax-tools{p} erlang-xmerl{p} esound-clients{p} esound-common{p} espeak{p} espeak-data{p} 
  evince{p} evolution{p} evolution-common{p} evolution-data-server{p} evolution-data-server-common{p} 
  evolution-webcal{p} example-content{p} f-spot{p} file-roller{p} firefox{p} firefox-3.5-branding{u} 
  firefox-branding{p} firefox-gnome-support{p} gamin{p} gbrainy{p} gcalctool{p} gcc{p} gcc-4.4{p} 
  gconf-defaults-service{p} gconf-editor{p} gdebi{p} gdm{p} gdm-guest-session{p} gedit{p} gedit-common{p} 
  gksu{p} gnome-about{p} gnome-accessibility-themes{p} gnome-applets{p} gnome-applets-data{p} 
  gnome-bluetooth{p} gnome-codec-install{p} gnome-control-center{p} gnome-desktop-data{p} 
  gnome-disk-utility{p} gnome-doc-utils{p} gnome-games-common{p} gnome-icon-theme{p} gnome-mag{p} 
  gnome-mahjongg{p} gnome-media{p} gnome-media-common{p} gnome-menus{p} gnome-mime-data{p} gnome-nettool{p} 
  gnome-orca{p} gnome-panel{p} gnome-panel-data{p} gnome-power-manager{p} gnome-screensaver{p} 
  gnome-session{p} gnome-session-bin{p} gnome-session-canberra{p} gnome-settings-daemon{p} gnome-sudoku{p} 
  gnome-system-monitor{p} gnome-system-tools{p} gnome-terminal{p} gnome-terminal-data{p} 
  gnome-themes-selected{p} gnome-themes-ubuntu{p} gnome-user-guide{p} gnome-user-share{p} gnome-utils{p} 
  gnomine{p} gstreamer0.10-alsa{p} gstreamer0.10-gnonlin{p} gstreamer0.10-nice{p} 
  gstreamer0.10-plugins-base{p} gstreamer0.10-plugins-base-apps{p} gstreamer0.10-plugins-good{p} 
  gstreamer0.10-pulseaudio{p} gstreamer0.10-tools{p} gstreamer0.10-x{p} gtk2-engines{p} 
  gtk2-engines-murrine{p} gtk2-engines-pixbuf{p} gucharmap{p} guile-1.8-libs{p} gvfs{p} gvfs-backends{p} 
  gvfs-bin{p} gvfs-fuse{p} gwibber{p} gwibber-service{p} humanity-icon-theme{p} ibus{p} ibus-gtk{p} 
  ibus-m17n{p} ibus-table{p} imagemagick{p} indicator-applet{p} indicator-applet-session{p} 
  indicator-application{p} indicator-me{p} indicator-messages{p} indicator-session{p} indicator-sound{p} 
  java-common{u} jockey-gtk{p} language-selector{p} launchpad-integration{p} libanthy0{p} 
  libappindicator0{p} libart-2.0-2{p} libart2.0-cil{p} libasound2-plugins{p} libatspi1.0-0{p} 
  libaudiofile0{p} libavahi-glib1{p} libavahi-gobject0{p} libavahi-ui0{p} libavc1394-0{p} libbeagle1{p} 
  libbonobo2-0{p} libbonobo2-common{p} libbonoboui2-0{p} libbonoboui2-common{p} libbrasero-media0{p} 
  libc-dev-bin{p} libc6-dev{p} libcairo-perl{p} libcairomm-1.0-1{p} libcamel1.2-14{p} 
  libcanberra-gtk-module{p} libcanberra-gtk0{p} libcanberra-pulse{p} libcanberra0{p} libcdio-cdda0{p} 
  libcdio-paranoia0{p} libcdio10{p} libclutter-1.0-0{p} libclutter-gtk-0.10-0{p} libcompizconfig0{p} 
  libcouchdb-glib-1.0-2{pu} libcroco3{p} libcryptui0{p} libcurl3{p} libdbusmenu-gtk1{p} libdecoration0{p} 
  libdesktopcouch-glib-1.0-2{pu} libdevkit-power-gobject1{p} libdotconf1.0{p} libdv4{p} libebackend1.2-0{p} 
  libebook1.2-9{p} libecal1.2-7{p} libedata-book1.2-2{p} libedata-cal1.2-6{p} libedataserver1.2-11{p} 
  libedataserverui1.2-8{p} libegroupwise1.2-13{p} libesd0{p} libespeak1{p} libevdocument2{p} 
  libevent-1.4-2{p} libevview2{p} libexchange-storage1.2-3{p} libexempi3{p} libflickrnet2.2-cil{p} 
  libfreezethaw-perl{p} libgail-common{p} libgail-gnome-module{p} libgail18{p} libgamin0{p} 
  libgconf2.0-cil{p} libgd2-xpm{p} libgdata-common{p} libgdata-google1.2-1{p} libgdata1.2-1{p} libgdata6{p} 
  libgdict-1.0-6{p} libgdiplus{p} libgdu-gtk0{p} libgdu0{p} libgksu2-0{p} libglade2.0-cil{p} 
  libglib-perl{p} libglib2.0-cil{p} libglib2.0-data{p} libglibmm-2.4-1c2a{p} libglitz-glx1{p} libglitz1{p} 
  libgmime-2.4-2{p} libgmime2.4-cil{p} libgnome-bluetooth7{p} libgnome-desktop-2-17{p} 
  libgnome-keyring1.0-cil{p} libgnome-mag2{p} libgnome-media0{p} libgnome-menu2{p} libgnome-pilot2{p} 
  libgnome-vfs2.0-cil{p} libgnome-window-settings1{p} libgnome2-0{p} libgnome2-canvas-perl{p} 
  libgnome2-common{p} libgnome2-perl{p} libgnome2-vfs-perl{p} libgnome2.24-cil{p} libgnomecanvas2-0{p} 
  libgnomecanvas2-common{p} libgnomekbd-common{p} libgnomekbd4{p} libgnomepanel2.24-cil{p} libgnomeui-0{p} 
  libgnomeui-common{p} libgnomevfs2-0{p} libgnomevfs2-common{p} libgnomevfs2-extra{p} 
  libgoocanvas-common{p} libgoocanvas3{p} libgraphviz4{p} libgsf-1-114{p} libgsf-1-common{p} 
  libgssdp-1.0-2{p} libgstfarsight0.10-0{p} libgtk-vnc-1.0-0{p} libgtk2-perl{p} libgtk2.0-cil{p} 
  libgtkhtml-editor-common{p} libgtkhtml-editor0{p} libgtkhtml3.14-19{p} libgtkmm-2.4-1c2a{p} 
  libgtksourceview2.0-0{p} libgtksourceview2.0-common{p} libgtkspell0{p} libgtop2-7{p} libgtop2-common{p} 
  libgucharmap7{p} libgupnp-1.0-3{p} libgupnp-igd-1.0-2{p} libgvfscommon0{p} libgweather-common{p} 
  libgweather1{p} libibus1{p} libido-0.1-0{p} libiec61883-0{p} libindicate-gtk2{p} libindicator0{p} 
  libjson-glib-1.0-0{p} libkpathsea5{p} libksieve4{u} liblaunchpad-integration1{p} 
  liblaunchpad-integration1.0-cil{p} liblircclient0{p} liblouis-data{p} liblouis0{p} liblpint-bonobo0{p} 
  libm17n-0{p} libmagickcore2-extra{p} libmetacity-private0{p} libmimelib4{u} libmldbm-perl{p} 
  libmono-addins-gui0.2-cil{p} libmono-addins0.2-cil{p} libmono-cairo2.0-cil{p} libmono-corlib2.0-cil{p} 
  libmono-data-tds2.0-cil{p} libmono-i18n-west2.0-cil{p} libmono-posix2.0-cil{p} libmono-security2.0-cil{p} 
  libmono-sharpzip2.84-cil{p} libmono-sqlite2.0-cil{p} libmono-system-data2.0-cil{p} 
  libmono-system-runtime2.0-cil{p} libmono-system-web2.0-cil{p} libmono-system2.0-cil{p} libmono2.0-cil{p} 
  libnautilus-extension1{p} libndesk-dbus-glib1.0-cil{p} libndesk-dbus1.0-cil{p} libnet-dbus-perl{p} 
  libnice0{p} libnotify1{p} libnunit2.4-cil{p} liboil0.3{p} liboobs-1-4{p} libotf0{p} libpanel-applet2-0{p} 
  libpango-perl{p} libpangomm-1.4-1{p} libpisock9{p} libpisync1{p} libpolkit-gtk-1-0{p} libpoppler-glib4{p} 
  libportaudio2{p} libprotobuf5{p} libprotoc5{p} libproxy0{p} libpst4{pu} libpulse-browse0{p} 
  libpurple-bin{p} libpurple0{p} librarian0{p} libraw1394-11{p} librsvg2-2{p} librsvg2-common{p} 
  libsctp1{p} libsdl1.2debian-pulseaudio{p} libsexy2{p} libshout3{p} libsilc-1.1-2{p} 
  libsilcclient-1.1-3{p} libsoup-gnome2.4-1{p} libsoup2.4-1{p} libspeechd2{p} libspeexdsp1{p} libsqlite0{p} 
  libstartup-notification0{p} libtdb1{p} libtelepathy-farsight0{p} libtelepathy-glib0{p} 
  libtie-ixhash-perl{p} libtotem-plparser17{p} libubuntuone-1.0-1{p} libunique-1.0-0{p} libupower-glib1{p} 
  libuuid-perl{p} libvisual-0.4-0{p} libvisual-0.4-plugins{p} libvte-common{p} libvte9{p} 
  libwebkit-1.0-2{p} libwebkit-1.0-common{p} libwmf0.2-7{p} libwmf0.2-7-gtk{p} libwnck-common{p} 
  libwnck22{p} libxcb-atom1{p} libxcb-aux0{p} libxcb-event1{p} libxml-twig-perl{p} libxml-xpath-perl{p} 
  libxres1{p} libzephyr4{p} light-themes{p} linux-headers-2.6.32-21{p} linux-headers-2.6.32-21-generic{p} 
  linux-headers-generic{p} linux-libc-dev{p} lksctp-tools{p} m17n-contrib{p} m17n-db{p} manpages-dev{p} 
  media-player-info{p} metacity{p} metacity-common{p} mobile-broadband-provider-info{p} mono-2.0-gac{p} 
  mono-gac{p} mono-runtime{p} mousetweaks{p} nautilus{p} nautilus-data{p} nautilus-sendto{p} 
  nautilus-sendto-empathy{p} nautilus-share{p} network-manager-gnome{p} notify-osd{p} notify-osd-icons{p} 
  obexd-client{p} onboard{p} openoffice.org-gnome{p} openoffice.org-gtk{p} openoffice.org-help-en-us{p} 
  openoffice.org-style-human{p} pitivi{p} pkg-config{p} plymouth-theme-ubuntu-logo{p} policykit-1-gnome{p} 
  protobuf-compiler{p} pulseaudio{p} pulseaudio-esound-compat{p} pulseaudio-module-bluetooth{p} 
  pulseaudio-module-gconf{p} pulseaudio-module-x11{p} pulseaudio-utils{p} python-appindicator{p} 
  python-aptdaemon{p} python-aptdaemon-gtk{p} python-avahi{p} python-brlapi{p} python-cairo{p} 
  python-configglue{p} python-couchdb{p} python-crypto{p} python-desktopcouch{p} 
  python-desktopcouch-records{p} python-egenix-mxdatetime{p} python-egenix-mxtools{p} python-farsight{p} 
  python-fstab{p} python-gconf{p} python-glade2{p} python-gmenu{p} python-gnome2{p} python-gnomeapplet{p} 
  python-gnomecanvas{p} python-gnomekeyring{p} python-gst0.10{p} python-gtk2{p} python-gtksourceview2{p} 
  python-gtkspell{p} python-ibus{p} python-indicate{p} python-launchpad-integration{p} python-libxml2{p} 
  python-louis{p} python-mako{p} python-notify{p} python-openssl{p} python-pam{p} python-papyon{p} 
  python-protobuf{p} python-pyatspi{p} python-pycurl{p} python-pygoocanvas{p} python-pyinotify{p} 
  python-pyorbit{p} python-rdflib{p} python-serial{p} python-speechd{p} python-telepathy{p} 
  python-twisted-bin{p} python-twisted-core{p} python-twisted-names{p} python-twisted-web{p} 
  python-ubuntuone{p} python-ubuntuone-client{p} python-ubuntuone-storageprotocol{p} python-virtkey{p} 
  python-vte{p} python-webkit{p} python-wnck{p} quadrapassel{p} rarian-compat{p} rhythmbox{p} 
  rhythmbox-plugin-cdrecorder{p} rhythmbox-plugins{p} rhythmbox-ubuntuone-music-store{p} rtkit{p} 
  screen-resolution-extra{p} screensaver-default-images{p} seahorse{p} sgml-data{p} simple-scan{p} 
  software-center{p} software-properties-gtk{p} speech-dispatcher{p} ssh-askpass-gnome{p} synaptic{p} 
  system-config-printer-gnome{p} system-tools-backends{p} telepathy-butterfly{p} telepathy-gabble{p} 
  telepathy-haze{p} telepathy-idle{p} telepathy-mission-control-5{p} telepathy-salut{p} tomboy{p} totem{p} 
  totem-common{p} totem-mozilla{p} totem-plugins{p} transmission-common{p} transmission-gtk{p} tsclient{p} 
  ttf-liberation{p} ubufox{p} ubuntu-artwork{p} ubuntu-docs{p} ubuntu-mono{p} ubuntu-sounds{p} 
  ubuntu-system-service{p} ubuntu-wallpapers{p} ubuntuone-client{p} ubuntuone-client-gnome{p} 
  update-notifier{p} upower{p} usb-creator-gtk{p} vinagre{p} vino{p} whois{p} xdg-user-dirs-gtk{p} 
  xscreensaver-data{p} xscreensaver-gl{p} xsltproc{p} xulrunner-1.9.2{p} yelp{p} zenity{p} 
0 packages upgraded, 0 newly installed, 538 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 1,373MB will be freed.
The following packages have unmet dependencies:
  libsdl1.2debian: Depends: libsdl1.2debian-alsa (= 1.2.14-4ubuntu1) but it is not installable or
                            libsdl1.2debian-all (= 1.2.14-4ubuntu1) but it is not installable or
                            libsdl1.2debian-esd (= 1.2.14-4ubuntu1) but it is not installable or
                            libsdl1.2debian-oss (= 1.2.14-4ubuntu1) but it is not installable or
                            libsdl1.2debian-nas (= 1.2.14-4ubuntu1) but it is not installable or
                            libsdl1.2debian-pulseaudio (= 1.2.14-4ubuntu1) but it is not installable
  libmono-getoptions2.0-cil: Depends: libmono-corlib2.0-cil (>= 1.2.2.1) but it is not installable
                             Depends: libmono-system2.0-cil (>= 2.4.3) but it is not installable
  ekiga: Depends: libavahi-glib1 (>= 0.6.16) but it is not installable
         Depends: libebook1.2-9 (>= 2.28.2) but it is not installable
         Depends: libedataserver1.2-11 (>= 2.28.2) but it is not installable
         Depends: liblaunchpad-integration1 but it is not installable
         Depends: libnotify1 (>= 0.4.5) but it is not installable
         Depends: libnotify1-gtk2.10 which is a virtual package.
         Depends: evolution-data-server but it is not installable
  kdelibs4c2a: Depends: libart-2.0-2 (>= 2.3.18) but it is not installable
               Depends: launchpad-integration but it is not installable
  python-twisted-web2: Depends: python-twisted-core (>= 8.2.0-2) but it is not installable
  mirage: Depends: python-gtk2 but it is not installable
  libmono-i18n2.0-cil: Depends: libmono-corlib2.0-cil (>= 1.2.2.1) but it is not installable
                       Depends: libmono-i18n-west2.0-cil (>= 1.0) but it is not installable
  libdc1394-22: Depends: libraw1394-11 but it is not installable
  gtali: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installable
         Depends: gnome-games-common (>= 1:2.30.0-0ubuntu6) but it is not installable
  pidgin-libnotify: Depends: libindicate-gtk2 (>= 0.2.2) but it is not installable
                    Depends: libnotify1 (>= 0.4.5) but it is not installable
                    Depends: libnotify1-gtk2.10 which is a virtual package.
  gstreamer0.10-plugins-ugly: Depends: libcdio10 but it is not installable
                              Depends: liboil0.3 (>= 0.3.8) but it is not installable
  glchess: Depends: gnome-games-common (>= 1:2.30.0-0ubuntu6) but it is not installable
           Depends: python-gtk2 (>= 2.10.0) but it is not installable
           Depends: python-launchpad-integration but it is not installable
  libgegl-0.0-0: Depends: librsvg2-2 (>= 2.26.0) but it is not installable
  tangerine-icon-theme: Depends: gnome-icon-theme but it is not installable
  nvidia-173: Depends: linux-libc-dev but it is not installable
              Depends: libc6-dev but it is not installable
  python-evince: Depends: libevdocument2 (>= 2.29.5) but it is not installable
                 Depends: libevview2 (>= 2.29.5) but it is not installable
                 Depends: python-gtk2 but it is not installable
  libseed0: Depends: libsoup2.4-1 (>= 2.4.0) but it is not installable
            Depends: libwebkit-1.0-2 (>= 1.1.1) but it is not installable
  gnome-games: Depends: aisleriot but it is not installable
               Depends: gnome-mahjongg but it is not installable
               Depends: gnome-sudoku but it is not installable
               Depends: gnomine but it is not installable
               Depends: quadrapassel but it is not installable
  nvidia-settings: Depends: screen-resolution-extra (>= 0.12) but it is not installable
  gnobots2: Depends: libcanberra-gtk0 (>= 0.17) but it is not installable
            Depends: libcanberra0 (>= 0.2) but it is not installable
            Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installable
            Depends: librsvg2-2 (>= 2.26.0) but it is not installable
            Depends: gnome-games-common (>= 1:2.30.0-0ubuntu6) but it is not installable
  wine1.2: Depends: binfmt-support (>= 1.1.2) but it is not installable
           Depends: libesd0 (>= 0.2.35) but it is not installable
  thunderbird: Depends: libstartup-notification0 (>= 0.10) but it is not installable
  libgtksourceview1.0-0: Depends: libart-2.0-2 (>= 2.3.18) but it is not installable
  compiz-kde: Depends: compiz-core (= 1:0.8.4-0ubuntu15) but it is not installable
              Depends: compiz-plugins (= 1:0.8.4-0ubuntu15) but it is not installable
              Depends: libdecoration0 but it is not installable
  language-support-translations-en: Depends: openoffice.org-help-en-us but it is not installable
                                    Depends: evolution-documentation-en which is a virtual package.
  pysdm: Depends: python-gtk2 but it is not installable
         Depends: python-glade2 but it is not installable
  lightsoff: Depends: gnome-games-common (>= 1:2.30.0-0ubuntu6) but it is not installable
  libesd-alsa0: Depends: libesd0 (>= 0.2.41-6ubuntu1) but it is not installable
  gnome-pilot-conduits: Depends: libart-2.0-2 (>= 2.3.18) but it is not installable
                        Depends: libbonobo2-0 (>= 2.15.0) but it is not installable
                        Depends: libbonoboui2-0 (>= 2.15.1) but it is not installable
                        Depends: libgnome-pilot2 (>= 2.0.2) but it is not installable
                        Depends: libgnome2-0 (>= 2.17.3) but it is not installable
                        Depends: libgnomecanvas2-0 (>= 2.11.1) but it is not installable
                        Depends: libgnomeui-0 (>= 2.22.0) but it is not installable
                        Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
                        Depends: libpisock9 but it is not installable
                        Depends: libpisync1 but it is not installable
  gnome-pilot: Depends: libart-2.0-2 (>= 2.3.18) but it is not installable
               Depends: libbonobo2-0 (>= 2.15.0) but it is not installable
               Depends: libbonoboui2-0 (>= 2.15.1) but it is not installable
               Depends: libgnome-pilot2 (>= 2.0.2) but it is not installable
               Depends: libgnome2-0 (>= 2.17.3) but it is not installable
               Depends: libgnomecanvas2-0 (>= 2.11.1) but it is not installable
               Depends: libgnomeui-0 (>= 2.22.0) but it is not installable
               Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
               Depends: libpanel-applet2-0 (>= 2.26.0) but it is not installable
               Depends: libpisock9 but it is not installable
               Depends: libpisync1 but it is not installable
  python-moovida: Depends: python-gst0.10 but it is not installable
                  Depends: python-cairo but it is not installable
                  Depends: python-gtk2 but it is not installable
                  Depends: python-twisted-core (>= 2.2) but it is not installable
                  Depends: python-twisted-web but it is not installable
  seahorse-plugins: Depends: libbonobo2-0 (>= 2.15.0) but it is not installable
                    Depends: libbonoboui2-0 (>= 2.15.1) but it is not installable
                    Depends: libcryptui0 (>= 2.27.5) but it is not installable
                    Depends: libgtksourceview2.0-0 (>= 2.9.7) but it is not installable
                    Depends: libnautilus-extension1 (>= 1:2.29.1) but it is not installable
                    Depends: libnotify1 (>= 0.4.5) but it is not installable
                    Depends: libnotify1-gtk2.10 which is a virtual package.
                    Depends: libpanel-applet2-0 (>= 2.26.0) but it is not installable
  gnibbles: Depends: libcanberra-gtk0 (>= 0.17) but it is not installable
            Depends: libcanberra0 (>= 0.2) but it is not installable
            Depends: libclutter-1.0-0 but it is not installable
            Depends: libclutter-gtk-0.10-0 (>= 0.10.2) but it is not installable
            Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installable
            Depends: gnome-games-common (>= 1:2.30.0-0ubuntu6) but it is not installable
  startupmanager: Depends: python-glade2 (>= 2.12) but it is not installable
                  Depends: python-gnome2 (>= 2.20) but it is not installable
                  Depends: python-libxml2 (>= 2.6.30) but it is not installable
                  Depends: yelp but it is not installable
  gcc-4.3: Depends: binutils (>= 2.19.1) but it is not installable
  soundconverter: Depends: python-gnome2 but it is not installable
                  Depends: python-glade2 but it is not installable
                  Depends: python-gst0.10 but it is not installable
                  Depends: gstreamer0.10-plugins-good but it is not installable
                  Depends: gstreamer0.10-plugins-base but it is not installable
  python-gnomedesktop: Depends: libgnome-desktop-2-17 (>= 1:2.29.92) but it is not installable
                       Depends: libstartup-notification0 (>= 0.10) but it is not installable
                       Depends: python-gtk2 but it is not installable
  libopal3.6.6: Depends: libspeexdsp1 (>= 1.2~beta3.2-1) but it is not installable
  libschroedinger-1.0-0: Depends: liboil0.3 (>= 0.3.16) but it is not installable
  python-pgm: Depends: python-gst0.10 but it is not installable
              Depends: python-gtk2 but it is not installable
              Depends: python-cairo but it is not installable
              Depends: python-twisted-core but it is not installable
  human-theme: Depends: dmz-cursor-theme but it is not installable
               Depends: humanity-icon-theme but it is not installable
               Depends: gtk2-engines-murrine but it is not installable
  gstreamer0.10-ffmpeg: Depends: liboil0.3 (>= 0.3.6) but it is not installable
  swell-foop: Depends: gnome-games-common (>= 1:2.30.0-0ubuntu6) but it is not installable
  compizconfig-settings-manager: Depends: python-gtk2 but it is not installable
  vlc-nox: Depends: libavc1394-0 (>= 0.5.3) but it is not installable
           Depends: libcdio10 but it is not installable
           Depends: liblircclient0 but it is not installable
           Depends: libraw1394-11 but it is not installable
           Depends: libshout3 but it is not installable
  gcompris: Depends: librsvg2-2 (>= 2.26.0) but it is not installable
            Depends: python-gtk2 but it is not installable
            Depends: gstreamer0.10-plugins-base but it is not installable
            Depends: gstreamer0.10-plugins-good but it is not installable
            Depends: librsvg2-common (>= 2.18) but it is not installable
  adobe-flashplugin: Depends: libcurl3 but it is not installable
  python-compizconfig: Depends: libcompizconfig0 but it is not installable
                       Depends: libstartup-notification0 (>= 0.8-1) but it is not installable
  gnotski: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installable
           Depends: librsvg2-2 (>= 2.26.0) but it is not installable
           Depends: gnome-games-common (>= 1:2.30.0-0ubuntu6) but it is not installable
  python-gnomeprint: Depends: libart-2.0-2 (>= 2.3.18) but it is not installable
                     Depends: libgnomecanvas2-0 (>= 2.11.1) but it is not installable
                     Depends: python-gtk2 but it is not installable
  python-sexy: Depends: libsexy2 (>= 0.1.8) but it is not installable
               Depends: python-gtk2 (>= 2.6.2) but it is not installable
  dkms: Depends: gcc but it is not installable
  tuxpaint: Depends: librsvg2-2 (>= 2.26.0) but it is not installable
  python-metacity: Depends: libmetacity-private0 (>= 1:2.26.0) but it is not installable
                   Depends: python-gtk2 but it is not installable
  python-twisted-conch: Depends: python-crypto (>= 2.0.1+dfsg1-1.1) but it is not installable
                        Depends: python-twisted-core (>= 10.0.0-2ubuntu1) but it is not installable
  gnome-user-guide-en: Depends: gnome-user-guide (= 2.30.0+git20100403ubuntu2) but it is not installable
                       Depends: scrollkeeper but it is not installable
                       Depends: yelp but it is not installable
  gir1.0-clutter-1.0: Depends: libclutter-1.0-0 but it is not installable
  python-nevow: Depends: python-twisted-core (>= 2.4) but it is not installable
                Depends: python-twisted-web (>= 0.6) but it is not installable
  iagno: Depends: libcanberra-gtk0 (>= 0.17) but it is not installable
         Depends: libcanberra0 (>= 0.2) but it is not installable
         Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installable
         Depends: gnome-games-common (>= 1:2.30.0-0ubuntu6) but it is not installable
  python-rsvg: Depends: librsvg2-2 (>= 2.26.0) but it is not installable
               Depends: librsvg2-common but it is not installable
               Depends: python-gtk2 but it is not installable
  glines: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installable
          Depends: librsvg2-2 (>= 2.26.0) but it is not installable
          Depends: gnome-games-common (>= 1:2.30.0-0ubuntu6) but it is not installable
  apturl: Depends: gksu (>= 2.0.0-1ubuntu3) but it is not installable
          Depends: gnome-icon-theme (>= 2.14.0-1) but it is not installable
          Depends: python-glade2 (>= 2.6.3-2) but it is not installable
          Depends: python-gtk2 (>= 2.6.3-2) but it is not installable
          Depends: python-webkit but it is not installable
          Depends: python-vte (>= 1:0.11.15-4) but it is not installable
          Depends: software-properties-gtk but it is not installable
          Depends: synaptic but it is not installable
  libswfdec-0.8-0: Depends: liboil0.3 (>= 0.3.10) but it is not installable
                   Depends: libsoup2.4-1 (>= 2.4.0) but it is not installable
  libgtkhtml2-0: Depends: libgail18 (>= 1.18.0) but it is not installable
  python-mediaprofiles: Depends: libgnome-media0 but it is not installable
                        Depends: python-gtk2 but it is not installable
  totem-gstreamer: Depends: totem (>= 2.27.1) but it is not installable
  python-epsilon: Depends: python-twisted-core but it is not installable
                  Depends: python-openssl but it is not installable
  gstreamer0.10-plugins-bad: Depends: libexempi3 (>= 2.1.0) but it is not installable
                             Depends: liboil0.3 (>= 0.3.8) but it is not installable
                             Depends: librsvg2-2 (>= 2.26.0) but it is not installable
                             Depends: gstreamer0.10-plugins-base but it is not installable
  libiso9660-7: Depends: libcdio10 but it is not installable
  firefox-3.0: Depends: firefox but it is not installable
  libgnomevfs2-bin: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  firefox-3.5: Depends: firefox but it is not installable
  gimp: Depends: python-gtk2 (>= 2.8.0) but it is not installable
        Depends: libpoppler-glib4 (>= 0.12) but it is not installable
        Depends: librsvg2-2 (>= 2.26.0) but it is not installable
        Depends: libwebkit-1.0-2 (>= 1.1.1) but it is not installable
        Depends: libwmf0.2-7 (>= 0.2.8.4) but it is not installable
  libgnome-speech7: Depends: libbonobo2-0 (>= 2.15.0) but it is not installable
                    Depends: libespeak1 (>= 1.30) but it is not installable
                    Depends: pulseaudio-utils but it is not installable
  vlc: Depends: libnotify1 (>= 0.4.5) but it is not installable
       Depends: libnotify1-gtk2.10 which is a virtual package.
  kinfocenter: Depends: libraw1394-11 but it is not installable
  firefox-3.0-gnome-support: Depends: firefox-gnome-support but it is not installable
  python-axiom: Depends: python-twisted-core but it is not installable
  libmono-data2.0-cil: Depends: libmono-corlib2.0-cil (>= 1.2.2.1) but it is not installable
                       Depends: libmono-data-tds2.0-cil (>= 2.4.3) but it is not installable
                       Depends: libmono-system-data2.0-cil (>= 1.2.6) but it is not installable
                       Depends: libmono-system2.0-cil (>= 2.4.3) but it is not installable
  pcmanfm-nohal: Depends: libgamin0 but it is not installable or
                          libfam0 but it is not installable
                 Depends: libstartup-notification0 (>= 0.10) but it is not installable
                 Depends: gamin but it is not installable
                 Depends: desktop-file-utils but it is not installable
  python-bugbuddy: Depends: python-gtk2 but it is not installable
  compizconfig-backend-kconfig: Depends: libart-2.0-2 (>= 2.3.18) but it is not installable
                                Depends: libcompizconfig0 but it is not installable
                                Depends: libstartup-notification0 (>= 0.8-1) but it is not installable
  python-totem-plparser: Depends: libtotem-plparser17 (>= 2.29.1) but it is not installable
                         Depends: python-gtk2 but it is not installable
  python-coherence: Depends: python-gst0.10 but it is not installable
  swfdec-mozilla: Depends: liboil0.3 (>= 0.3.1) but it is not installable
  gnotravex: Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installable
             Depends: gnome-games-common (>= 1:2.30.0-0ubuntu6) but it is not installable
  gnect: Depends: libcanberra-gtk0 (>= 0.17) but it is not installable
         Depends: libcanberra0 (>= 0.2) but it is not installable
         Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installable
         Depends: gnome-games-common (>= 1:2.30.0-0ubuntu6) but it is not installable
  python-evolution: Depends: libbonobo2-0 (>= 2.15.0) but it is not installable
                    Depends: libebook1.2-9 (>= 2.28.3.1) but it is not installable
                    Depends: libecal1.2-7 (>= 2.28.3.1) but it is not installable
                    Depends: libedataserver1.2-11 (>= 2.28.3.1) but it is not installable
                    Depends: libsoup2.4-1 (>= 2.4.0) but it is not installable
                    Depends: python-gtk2 but it is not installable
  pidgin: Depends: libgtkspell0 (>= 2.0.10) but it is not installable
          Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installable
          Depends: libpurple0 (>= 1:2.6.0) but it is not installable
          Depends: libstartup-notification0 (>= 0.10) but it is not installable
  gir1.0-clutter-gtk-0.10: Depends: libclutter-gtk-0.10-0 (>= 0.10.2) but it is not installable
  festival: Depends: libaudiofile0 (>= 0.2.3-4) but it is not installable
  compiz-fusion-plugins-extra: Depends: libstartup-notification0 (>= 0.10) but it is not installable
                               Depends: compiz-core but it is not installable
                               Depends: compiz-core-abiversion-20090619 which is a virtual package.
  libemeraldengine0: Depends: libdecoration0 but it is not installable
                     Depends: libwnck22 (>= 2.22.0) but it is not installable
  libgmime2.2a-cil: Depends: cli-common (>= 0.5.1) but it is not installable
                    Depends: libglib2.0-cil (>= 2.12.9) but it is not installable
                    Depends: libmono-corlib2.0-cil (>= 1.2.2.1) but it is not installable
  gstreamer0.10-gnomevfs: Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
  python-gnome2-desktop: Depends: python-gnomeapplet (>= 2.30.0-0ubuntu1) but it is not installable
                         Depends: python-gnomekeyring (>= 2.30.0-0ubuntu1) but it is not installable
                         Depends: python-wnck (>= 2.30.0-0ubuntu1) but it is not installable
  libgnomeprint2.2-0: Depends: libart-2.0-2 (>= 2.3.18) but it is not installable
  libvcdinfo0: Depends: libcdio10 but it is not installable
  libestools1.2: Depends: libesd0 (>= 0.2.35) but it is not installable
  moovida-plugins-bad: Depends: gstreamer0.10-plugins-base but it is not installable
                       Depends: gstreamer0.10-plugins-good but it is not installable
                       Depends: python-avahi but it is not installable
                       Depends: python-openssl but it is not installable
                       Depends: ttf-liberation but it is not installable
  libgnomeprintui2.2-0: Depends: libart-2.0-2 (>= 2.3.18) but it is not installable
                        Depends: libgnomecanvas2-0 (>= 2.11.1) but it is not installable
  usb-creator: Depends: usb-creator-gtk (= 0.2.22) but it is not installable
  python-gtop: Depends: libgtop2-7 (>= 2.20.0) but it is not installable
               Depends: python-gtk2 but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
adobe-flashplugin
apturl
compiz-fusion-plugins-extra
compiz-kde
compizconfig-backend-kconfig
compizconfig-settings-manager
dkms
ekiga
festival
festlex-cmu
festlex-poslex
festvox-kallpc16k
firefox-3.0
firefox-3.0-gnome-support
firefox-3.5
fusion-icon
gcc-4.3
gcompris
gimp
gir1.0-clutter-1.0
gir1.0-clutter-gtk-0.10
glchess
glines
gnect
gnibbles
gnobots2
gnome-games
gnome-pilot
gnome-pilot-conduits
gnome-user-guide-en
gnotravex
gnotski
gstreamer0.10-ffmpeg
gstreamer0.10-gnomevfs
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly
gtali
human-theme
iagno
kdelibs4c2a
kinfocenter
language-support-translations-en
libavcodec-extra-52
libavcodec-unstripped-52
libavformat52
libdc1394-22
libemeraldengine0
libesd-alsa0
libestools1.2
libgegl-0.0-0
libgmime2.2a-cil
libgnome-speech7
libgnomeprint2.2-0
libgnomeprintui2.2-0
libgnomevfs2-bin
libgtkhtml2-0
libgtksourceview1.0-0
libiso9660-7
libk3b6-extracodecs
libmono-data2.0-cil
libmono-getoptions2.0-cil
libmono-i18n2.0-cil
libopal3.6.6
libschroedinger-1.0-0
libseed0
libswfdec-0.8-0
libvcdinfo0
libxine1-ffmpeg
lightsoff
mirage
moovida
moovida-plugins-bad
moovida-plugins-good
moovida-plugins-ugly
nvidia-173
nvidia-glx-173
nvidia-settings
pcmanfm-nohal
pidgin
pidgin-libnotify
pidgin-otr
pysdm
python-axiom
python-bugbuddy
python-coherence
python-compizconfig
python-epsilon
python-evince
python-evolution
python-gnome2-desktop
python-gnomedesktop
python-gnomeprint
python-gtop
python-mediaprofiles
python-metacity
python-moovida
python-nevow
python-pgm
python-rsvg
python-sexy
python-totem-plparser
python-twisted-conch
python-twisted-web2
seahorse-plugins
seed
soundconverter
startupmanager
swell-foop
swfdec-mozilla
tangerine-icon-theme
thunderbird
thunderbird-locale-en-gb
totem-gstreamer
tuxpaint
usb-creator
vlc
vlc-nox
vlc-plugin-pulse
wine
wine1.2

Install the following packages:
libsdl1.2debian-alsa [1.2.14-4ubuntu1 (lucid)]

Leave the following dependencies unresolved:
kipi-plugins recommends imagemagick (>= 5.4.8) | graphicsmagick-imagemagick-compat (>= 1.1.7)
libglib2.0-0 recommends libglib2.0-data
libgnomeprintui2.2-common recommends gnome-icon-theme
bluetooth recommends bluez-gstreamer
gcompris-data recommends gcompris
gcompris-sound-en recommends gcompris
python-twill recommends doc-base
tuxpaint-data recommends tuxpaint
tuxpaint-stamps-default recommends tuxpaint
flashplugin-installer recommends libasound2-plugins (>= 1.0.16)
ttf-mscorefonts-installer recommends ttf-liberation
wine1.2-gecko recommends wine1.2
gimp-data recommends gimp
libgimp2.0 recommends gimp
Score is -16777

Accept this solution? [Y/n/q/?] q


From what I can make out - it wants to remove pretty much ALL the applications in order to resolve the dependency issues. That doesn't sound that terribly useful to me. Or am I misunderstanding what it is suggesting?

---

### Post by Zorael on 2010-05-18
```
The following actions will resolve these dependencies:

Remove the following packages:
adobe-flashplugin
apturl
compiz-fusion-plugins-extra
compiz-kde
compizconfig-backend-kconfig
compizconfig-settings-manager
dkms
ekiga
festival
festlex-cmu
festlex-poslex
festvox-kallpc16k
firefox-3.0
firefox-3.0-gnome-support
firefox-3.5
fusion-icon
gcc-4.3
gcompris
gimp
gir1.0-clutter-1.0
gir1.0-clutter-gtk-0.10
glchess
glines
gnect
gnibbles
gnobots2
gnome-games
gnome-pilot
gnome-pilot-conduits
gnome-user-guide-en
gnotravex
gnotski
gstreamer0.10-ffmpeg
gstreamer0.10-gnomevfs
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly
gtali
human-theme
iagno
kdelibs4c2a
kinfocenter
language-support-translations-en
libavcodec-extra-52
libavcodec-unstripped-52
libavformat52
libdc1394-22
libemeraldengine0
libesd-alsa0
libestools1.2
libgegl-0.0-0
libgmime2.2a-cil
libgnome-speech7
libgnomeprint2.2-0
libgnomeprintui2.2-0
libgnomevfs2-bin
libgtkhtml2-0
libgtksourceview1.0-0
libiso9660-7
libk3b6-extracodecs
libmono-data2.0-cil
libmono-getoptions2.0-cil
libmono-i18n2.0-cil
libopal3.6.6
libschroedinger-1.0-0
libseed0
libswfdec-0.8-0
libvcdinfo0
libxine1-ffmpeg
lightsoff
mirage
moovida
moovida-plugins-bad
moovida-plugins-good
moovida-plugins-ugly
nvidia-173
nvidia-glx-173
nvidia-settings
pcmanfm-nohal
pidgin
pidgin-libnotify
pidgin-otr
pysdm
python-axiom
python-bugbuddy
python-coherence
python-compizconfig
python-epsilon
python-evince
python-evolution
python-gnome2-desktop
python-gnomedesktop
python-gnomeprint
python-gtop
python-mediaprofiles
python-metacity
python-moovida
python-nevow
python-pgm
python-rsvg
python-sexy
python-totem-plparser
python-twisted-conch
python-twisted-web2
seahorse-plugins
seed
soundconverter
startupmanager
swell-foop
swfdec-mozilla
tangerine-icon-theme
thunderbird
thunderbird-locale-en-gb
totem-gstreamer
tuxpaint
usb-creator
vlc
vlc-nox
vlc-plugin-pulse
wine
wine1.2

Install the following packages:
libsdl1.2debian-alsa [1.2.14-4ubuntu1 (lucid)]

Leave the following dependencies unresolved:
kipi-plugins recommends imagemagick (>= 5.4.8) | graphicsmagick-imagemagick-compat (>= 1.1.7)
libglib2.0-0 recommends libglib2.0-data
libgnomeprintui2.2-common recommends gnome-icon-theme
bluetooth recommends bluez-gstreamer
gcompris-data recommends gcompris
gcompris-sound-en recommends gcompris
python-twill recommends doc-base
tuxpaint-data recommends tuxpaint
tuxpaint-stamps-default recommends tuxpaint
flashplugin-installer recommends libasound2-plugins (>= 1.0.16)
ttf-mscorefonts-installer recommends ttf-liberation
wine1.2-gecko recommends wine1.2
gimp-data recommends gimp
libgimp2.0 recommends gimp
```
That looks *fairly* good, though it's still leaving some useless packages (like gimp libraries even though Gimp itself was removed). If you're just going to reinstall Gimp afterwards, it doesn't matter much. In particular you will want to get your Nvidia drivers back in immediately (**nvidia-current**?).

And again, this command removes non-KDE and non-Kubuntu stuff. Obviously stuff like Firefox, Gimp, Pidgin and Synaptic will be dragged along with it, since they're not KDE software.

I'd advise to pick that solution and then reinstall whatever you'd like to keep. Your own user-specific settings will still be in your user directory, so they should persist.

This one *might* produce less errors, but it may as well not. If it spouts even more, just go with the first one.
```
sudo aptitude purge adium-theme-ubuntu aisleriot alacarte app-install-data-partner apport-gtk aptdaemon at-spi binfmt-support binutils bluez-gstreamer branding-ubuntu brasero brasero-common brltty-x11 capplets-data checkbox checkbox-gtk cli-common compiz compiz-core compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf computer-janitor computer-janitor-gtk couchdb-bin dcraw desktop-file-utils desktopcouch dmz-cursor-theme doc-base docbook-xml empathy empathy-common eog erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl esound-clients esound-common espeak espeak-data evince evolution evolution-common evolution-couchdb evolution-data-server evolution-data-server-common evolution-exchange evolution-indicator evolution-plugins evolution-webcal example-content f-spot file-roller firefox firefox-branding firefox-gnome-support gamin gbrainy gcalctool gcc gcc-4.4 gconf-defaults-service gconf-editor gdebi gdm gdm-guest-session gedit gedit-common gksu gnome-about gnome-accessibility-themes gnome-applets gnome-applets-data gnome-bluetooth gnome-codec-install gnome-control-center gnome-desktop-data gnome-disk-utility gnome-doc-utils gnome-games-common gnome-icon-theme gnome-mag gnome-mahjongg gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-power-manager gnome-screensaver gnome-session gnome-session-bin gnome-session-canberra gnome-settings-daemon gnome-sudoku gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu gnome-user-guide gnome-user-share gnome-utils gnomine gstreamer0.10-alsa gstreamer0.10-gnonlin gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse gwibber gwibber-service humanity-icon-theme ibus ibus-gtk ibus-m17n ibus-table indicator-applet indicator-applet-session indicator-application indicator-me indicator-messages indicator-session indicator-sound jockey-gtk language-selector launchpad-integration libanthy0 libappindicator0 libart-2.0-2 libart2.0-cil libatspi1.0-0 libaudiofile0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrasero-media0 libc-dev-bin libc6-dev libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio10 libclutter-1.0-0 libclutter-gtk-0.10-0 libcompizconfig0 libcouchdb-glib-1.0-2 libcroco3 libcryptui0 libcurl3 libdbusmenu-gtk1 libdecoration0 libdesktopcouch-glib-1.0-2 libdevkit-power-gobject1 libdotconf1.0 libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13 libesd0 libespeak1 libevdocument2 libevent-1.4-2 libevview2 libexchange-storage1.2-3 libexempi3 libflickrnet2.2-cil libfreezethaw-perl libgail-common libgail-gnome-module libgail18 libgamin0 libgconf2.0-cil libgd2-xpm libgdata-common libgdata-google1.2-1 libgdata1.2-1 libgdata6 libgdict-1.0-6 libgdiplus libgdu-gtk0 libgdu0 libgksu2-0 libglade2.0-cil libglib-perl libglib2.0-cil libglibmm-2.4-1c2a libglitz-glx1 libglitz1 libgmime-2.4-2 libgmime2.4-cil libgnome-bluetooth7 libgnome-desktop-2-17 libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomekbd-common libgnomekbd4 libgnomepanel2.24-cil libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgoocanvas-common libgoocanvas3 libgraphviz4 libgsf-1-114 libgsf-1-common libgssdp-1.0-2 libgstfarsight0.10-0 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgupnp-1.0-3 libgupnp-igd-1.0-2 libgvfscommon0 libgweather-common libgweather1 libibus1 libido-0.1-0 libiec61883-0 libindicate-gtk2 libindicator0 libjson-glib-1.0-0 libkpathsea5 liblaunchpad-integration1 liblaunchpad-integration1.0-cil liblircclient0 liblouis-data liblouis0 liblpint-bonobo0 libm17n-0 libmagickcore2-extra libmetacity-private0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-i18n-west2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-runtime2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnice0 libnotify1 libnunit2.4-cil liboil0.3 liboobs-1-4 libotf0 libpanel-applet2-0 libpango-perl libpangomm-1.4-1 libpisock9 libpisync1 libpolkit-gtk-1-0 libpoppler-glib4 libportaudio2 libprotobuf5 libprotoc5 libproxy0 libpst4 libpulse-browse0 libpurple-bin libpurple0 librarian0 libraw1394-11 librsvg2-2 librsvg2-common libsctp1 libsdl1.2debian-pulseaudio libsexy2 libshout3 libsilc-1.1-2 libsilcclient-1.1-3 libsoup-gnome2.4-1 libsoup2.4-1 libspeechd2 libspeexdsp1 libsqlite0 libstartup-notification0 libtdb1 libtelepathy-farsight0 libtelepathy-glib0 libtie-ixhash-perl libtotem-plparser17 libubuntuone-1.0-1 libunique-1.0-0 libupower-glib1 libuuid-perl libvisual-0.4-0 libvisual-0.4-plugins libvte-common libvte9 libwebkit-1.0-2 libwebkit-1.0-common libwmf0.2-7 libwmf0.2-7-gtk libwnck-common libwnck22 libxcb-atom1 libxcb-aux0 libxcb-event1 libxml-twig-perl libxml-xpath-perl libxres1 libzephyr4 light-themes linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic linux-headers-generic linux-libc-dev lksctp-tools m17n-contrib m17n-db manpages-dev media-player-info metacity metacity-common mobile-broadband-provider-info mono-2.0-gac mono-gac mono-runtime mousetweaks nautilus nautilus-data nautilus-sendto nautilus-sendto-empathy nautilus-share network-manager-gnome notification-daemon notify-osd notify-osd-icons obexd-client onboard openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-style-human pitivi pkg-config plymouth-theme-ubuntu-logo policykit-1-gnome protobuf-compiler pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils python-appindicator python-aptdaemon python-aptdaemon-gtk python-avahi python-brlapi python-cairo python-configglue python-couchdb python-crypto python-desktopcouch python-desktopcouch-records python-egenix-mxdatetime python-egenix-mxtools python-farsight python-fstab python-gconf python-glade2 python-gmenu python-gnome2 python-gnomeapplet python-gnomecanvas python-gnomekeyring python-gst0.10 python-gtk2 python-gtksourceview2 python-gtkspell python-ibus python-indicate python-launchpad-integration python-libxml2 python-louis python-mako python-notify python-openssl python-pam python-papyon python-protobuf python-pyatspi python-pycurl python-pygoocanvas python-pyinotify python-pyorbit python-rdflib python-serial python-speechd python-telepathy python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntuone python-ubuntuone-client python-ubuntuone-storageprotocol python-virtkey python-vte python-webkit python-wnck quadrapassel rarian-compat rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins rhythmbox-ubuntuone-music-store rtkit screen-resolution-extra screensaver-default-images scrollkeeper seahorse sgml-data simple-scan software-center software-properties-gtk speech-dispatcher ssh-askpass-gnome synaptic system-config-printer-gnome system-tools-backends telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-mission-control-5 telepathy-salut tomboy totem totem-common totem-mozilla totem-plugins transmission-common transmission-gtk tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono ubuntu-sounds ubuntu-system-service ubuntu-wallpapers ubuntuone-client ubuntuone-client-gnome update-manager update-notifier upower usb-creator-gtk vinagre vino xdg-user-dirs-gtk xscreensaver-data xscreensaver-gl xsltproc xulrunner-1.9.2 yelp ~ngimp ~ngcompris ~ntuxpaint ~nwine1.2 -P && sudo aptitude install kubuntu-desktop nvidia-current
```

---

### Post by a.sarkar on 2010-06-04
> **Zorael said:**
> Try using **aptitude** instead of apt-get. It is much better at resolving dependencies.
```
$ sudo aptitude purge adium-theme-ubuntu aisleriot alacarte app-install-data-partner apport-gtk aptdaemon at-spi binfmt-support binutils bluez-gstreamer branding-ubuntu brasero brasero-common brltty-x11 capplets-data checkbox checkbox-gtk cli-common compiz compiz-core compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf computer-janitor computer-janitor-gtk couchdb-bin dcraw desktop-file-utils desktopcouch dmz-cursor-theme doc-base docbook-xml empathy empathy-common eog erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl esound-clients esound-common espeak espeak-data evince evolution evolution-common evolution-couchdb evolution-data-server evolution-data-server-common evolution-exchange evolution-indicator evolution-plugins evolution-webcal example-content f-spot file-roller firefox firefox-branding firefox-gnome-support gamin gbrainy gcalctool gcc gcc-4.4 gconf-defaults-service gconf-editor gdebi gdm gdm-guest-session gedit gedit-common gksu gnome-about gnome-accessibility-themes gnome-applets gnome-applets-data gnome-bluetooth gnome-codec-install gnome-control-center gnome-desktop-data gnome-disk-utility gnome-doc-utils gnome-games-common gnome-icon-theme gnome-mag gnome-mahjongg gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-power-manager gnome-screensaver gnome-session gnome-session-bin gnome-session-canberra gnome-settings-daemon gnome-sudoku gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu gnome-user-guide gnome-user-share gnome-utils gnomine gstreamer0.10-alsa gstreamer0.10-gnonlin gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse gwibber gwibber-service humanity-icon-theme ibus ibus-gtk ibus-m17n ibus-table imagemagick indicator-applet indicator-applet-session indicator-application indicator-me indicator-messages indicator-session indicator-sound jockey-gtk language-selector launchpad-integration libanthy0 libappindicator0 libart-2.0-2 libart2.0-cil libasound2-plugins libatspi1.0-0 libaudiofile0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrasero-media0 libc-dev-bin libc6-dev libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio10 libclutter-1.0-0 libclutter-gtk-0.10-0 libcompizconfig0 libcouchdb-glib-1.0-2 libcroco3 libcryptui0 libcurl3 libdbusmenu-gtk1 libdecoration0 libdesktopcouch-glib-1.0-2 libdevkit-power-gobject1 libdotconf1.0 libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13 libesd0 libespeak1 libevdocument2 libevent-1.4-2 libevview2 libexchange-storage1.2-3 libexempi3 libflickrnet2.2-cil libfreezethaw-perl libgail-common libgail-gnome-module libgail18 libgamin0 libgconf2.0-cil libgd2-xpm libgdata-common libgdata-google1.2-1 libgdata1.2-1 libgdata6 libgdict-1.0-6 libgdiplus libgdu-gtk0 libgdu0 libgksu2-0 libglade2.0-cil libglib-perl libglib2.0-cil libglib2.0-data libglibmm-2.4-1c2a libglitz-glx1 libglitz1 libgmime-2.4-2 libgmime2.4-cil libgnome-bluetooth7 libgnome-desktop-2-17 libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomekbd-common libgnomekbd4 libgnomepanel2.24-cil libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgoocanvas-common libgoocanvas3 libgraphviz4 libgsf-1-114 libgsf-1-common libgssdp-1.0-2 libgstfarsight0.10-0 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgupnp-1.0-3 libgupnp-igd-1.0-2 libgvfscommon0 libgweather-common libgweather1 libibus1 libido-0.1-0 libiec61883-0 libindicate-gtk2 libindicator0 libjson-glib-1.0-0 libkpathsea5 liblaunchpad-integration1 liblaunchpad-integration1.0-cil liblircclient0 liblouis-data liblouis0 liblpint-bonobo0 libm17n-0 libmagickcore2-extra libmetacity-private0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-i18n-west2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-runtime2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnice0 libnotify1 libnunit2.4-cil liboil0.3 liboobs-1-4 libotf0 libpanel-applet2-0 libpango-perl libpangomm-1.4-1 libpisock9 libpisync1 libpolkit-gtk-1-0 libpoppler-glib4 libportaudio2 libprotobuf5 libprotoc5 libproxy0 libpst4 libpulse-browse0 libpurple-bin libpurple0 librarian0 libraw1394-11 librsvg2-2 librsvg2-common libsctp1 libsdl1.2debian-pulseaudio libsexy2 libshout3 libsilc-1.1-2 libsilcclient-1.1-3 libsoup-gnome2.4-1 libsoup2.4-1 libspeechd2 libspeexdsp1 libsqlite0 libstartup-notification0 libtdb1 libtelepathy-farsight0 libtelepathy-glib0 libtie-ixhash-perl libtotem-plparser17 libubuntuone-1.0-1 libunique-1.0-0 libupower-glib1 libuuid-perl libvisual-0.4-0 libvisual-0.4-plugins libvte-common libvte9 libwebkit-1.0-2 libwebkit-1.0-common libwmf0.2-7 libwmf0.2-7-gtk libwnck-common libwnck22 libxcb-atom1 libxcb-aux0 libxcb-event1 libxml-twig-perl libxml-xpath-perl libxres1 libzephyr4 light-themes linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic linux-headers-generic linux-libc-dev lksctp-tools m17n-contrib m17n-db manpages-dev media-player-info metacity metacity-common mobile-broadband-provider-info mono-2.0-gac mono-gac mono-runtime mousetweaks nautilus nautilus-data nautilus-sendto nautilus-sendto-empathy nautilus-share network-manager-gnome notification-daemon notify-osd notify-osd-icons obexd-client onboard openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-style-human pitivi pkg-config plymouth-theme-ubuntu-logo policykit-1-gnome protobuf-compiler pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils python-appindicator python-aptdaemon python-aptdaemon-gtk python-avahi python-brlapi python-cairo python-configglue python-couchdb python-crypto python-desktopcouch python-desktopcouch-records python-egenix-mxdatetime python-egenix-mxtools python-farsight python-fstab python-gconf python-glade2 python-gmenu python-gnome2 python-gnomeapplet python-gnomecanvas python-gnomekeyring python-gst0.10 python-gtk2 python-gtksourceview2 python-gtkspell python-ibus python-indicate python-launchpad-integration python-libxml2 python-louis python-mako python-notify python-openssl python-pam python-papyon python-protobuf python-pyatspi python-pycurl python-pygoocanvas python-pyinotify python-pyorbit python-rdflib python-serial python-speechd python-telepathy python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntuone python-ubuntuone-client python-ubuntuone-storageprotocol python-virtkey python-vte python-webkit python-wnck quadrapassel rarian-compat rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins rhythmbox-ubuntuone-music-store rtkit screen-resolution-extra screensaver-default-images scrollkeeper seahorse sgml-data simple-scan software-center software-properties-gtk speech-dispatcher ssh-askpass-gnome synaptic system-config-printer-gnome system-tools-backends telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-mission-control-5 telepathy-salut tomboy totem totem-common totem-mozilla totem-plugins transmission-common transmission-gtk tsclient ttf-liberation ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono ubuntu-sounds ubuntu-system-service ubuntu-wallpapers ubuntuone-client ubuntuone-client-gnome update-manager update-notifier upower usb-creator-gtk vinagre vino whois xdg-user-dirs-gtk xscreensaver-data xscreensaver-gl xsltproc xulrunner-1.9.2 yelp zenity -P && sudo aptitude install kubuntu-desktop
```

Using Zorael's first aptitude command **worked**. 
[COLOR=Red]Warning:[/COLOR] However it pretty much un-installed all the packages that I had installed over the default setup. The packages it un-installed in my system were
```

acetoneiso
alien
apturl
audacious
audacious-plugins
build-essential
catfish
checkinstall
curl
dayplanner
debhelper
devede
djvulibre-bin
dpkg-dev
dvd-slideshow
dvipng
ekee
f2c
feynmf
ffmpeg
foiltex
fort77
g++
g++-4.4
gettext
gfortran
gfortran-4.4
gimp
gnome-network-admin
gnome-user-guide-bn
gnome-user-guide-en
gnumeric
gparted
gstreamer0.10-ffmpeg
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
intltool-debian
latex-beamer
latex-sanskrit
latex-xcolor
libatk1.0-dev
libavcodec-extra-52
libavdevice52
libavfilter0
libavformat-extra-52
libcairo2-dev
libdc1394-22
libdirectfb-dev
libexpat1-dev
libf2c2-dev
libfontconfig1-dev
libfreetype6-dev
libgegl-0.0-0
libglib2.0-dev
libgoffice-0.8-8
libgraphicsmagick++3
libgraphicsmagick3
libgtk2.0-dev
libiso9660-7
libjpeg62-dev
libmjpegtools-1.9
libpango1.0-dev
libpng12-dev
libquicktime1
libschroedinger-1.0-0
libsox-fmt-all
libsox-fmt-ffmpeg
libstdc++6-4.4-dev
libvcdinfo0
libxft-dev
libxine1-ffmpeg
mencoder
mjpegtools
mplayer
mplayer-fonts
mplayer-gui
mplayer-nogui
mplayerthumbs
nautilus-open-terminal
nautilus-wallpaper
openoffice.org-base-core
openoffice.org-calc
openoffice.org-common
openoffice.org-core
openoffice.org-draw
openoffice.org-emailmerge
openoffice.org-help-en-gb
openoffice.org-impress
openoffice.org-l10n-bn
openoffice.org-l10n-en-gb
openoffice.org-l10n-en-za
openoffice.org-math
openoffice.org-writer
pdf2djvu
pgf
po-debconf
prosper
python-uno
qdvdauthor
qdvdauthor-common
startupmanager
sysinfo
texlive-base
texlive-bibtex-extra
texlive-binaries
texlive-extra-utils
texlive-font-utils
texlive-fonts-extra
texlive-fonts-recommended
texlive-generic-recommended
texlive-lang-indic
texlive-latex-base
texlive-latex-extra
texlive-latex-recommended
texlive-luatex
texlive-math-extra
texlive-metapost
texlive-pictures
texlive-pstricks
texlive-publishers
texlive-xetex
tipa
vcdimager
videotrans
vim-gnome
vlc
vlc-nox
vlc-plugin-pulse
wine
wine1.2
zlib1g-dev

```Strange that it should un-install non-gnome packages like texlive :confused:. However no harm done, since I already had the list of packages that I had installed.
**Important: ** So if you are trying out this method, then make sure you know the list of packages you had installed over the default setup. 

Fortunately, the packages that I had installed were still in "/var/cache/apt/archives" folder. (This is the folder where ubuntu downloads the packages). So when I ran through my list of packages, very little were downloaded. 

I had to make some changes to the list though - like change vim-gnome package to vim-gtk (vim-gnome has a lot of gnome related stuff). 
[B]
Info: [/B]If you are also planning to use scim + openoffice (for non-english input), then run the commands
```

sudo apt-get remove openoffice.org-kde
sudo apt-get install openoffice.org openoffice.org-gnome
```Yes. uninstall the -kde package and install the -gnome package. The -gnome package will only install a few gnome packages. The -kde package has some problem with scim.

Further, if you have disabled installation of recommended packages then its better to install the following kde packages as well
```
sudo apt-get install gwenview k3b kfind ktorrent  plasma-widgets-addons plasma-widget-logout plasma-widget-memusage network-manager-kde adept
```
These packages are part of the recommended packages of kubuntu-desktop.
Now enjoying kde4. Very COOL :guitar:

---

