---
title: "Update Manager Fault"
date: 2009-03-20
forum: Desktop Environments
---

### Post by gewitty on 2009-03-20
I was reinstalling something in Synaptic yesterday and in the middle of the process suffered a power cut. After the power came back on, I restarted my PC and everything seemed to be working OK. However, I now get an update alert which tells me that there are 627 updates available (436Mb)!

It seems that somewhere there must be a file that keeps track of what updates have been applied and this seems to have been deleted or corrupted by the power failure.

Is there any way I can correct this problem, so that I get back to only being alerted to genuine updates?

---

### Post by taurus on 2009-03-20
Close down update manager.  Then, open a terminal and post the outputs of these two commands.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by gewitty on 2009-03-20
This is the output from the two commands:

sudo apt-get update

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB           
Get: 1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_GB                     
Get: 2 [http://ftp.de.debian.org](http://ftp.de.debian.org) sid Release.gpg [197B]                         
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) sid/main Translation-en_GB                        
Get: 3 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [197B]                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_GB                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg                             
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB [19.6kB]      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_GB             
Get: 5 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [11.7kB]                    
Get: 6 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [31.1kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get: 7 [http://ftp.de.debian.org](http://ftp.de.debian.org) sid Release [77.8kB]                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) sid Release                                       
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy Release.gpg                                      
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy/main Translation-en_GB                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://ftp.de.debian.org](http://ftp.de.debian.org) sid/main Packages                                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources               
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy Release                                          
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB [1956B] 
Get: 9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB [4368B]   
Get: 10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB [36.1kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy/main Packages                      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Sources
Hit [http://apt.boxee.tv](http://apt.boxee.tv) hardy/main Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Sources
Fetched 74.4kB in 1s (64.0kB/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0503DBBBDFAF548E
W: GPG error: [http://ftp.de.debian.org](http://ftp.de.debian.org) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

sudo apt-get upgrade

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB           
Get: 1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_GB                     
Get: 2 [http://ftp.de.debian.org](http://ftp.de.debian.org) sid Release.gpg [197B]                         
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) sid/main Translation-en_GB                        
Get: 3 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [197B]                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_GB                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg                             
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB [19.6kB]      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_GB             
Get: 5 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [11.7kB]                    
Get: 6 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [31.1kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get: 7 [http://ftp.de.debian.org](http://ftp.de.debian.org) sid Release [77.8kB]                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) sid Release                                       
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy Release.gpg                                      
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy/main Translation-en_GB                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://ftp.de.debian.org](http://ftp.de.debian.org) sid/main Packages                                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources               
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy Release                                          
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB [1956B] 
Get: 9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB [4368B]   
Get: 10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB [36.1kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy/main Packages                      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Sources
Hit [http://apt.boxee.tv](http://apt.boxee.tv) hardy/main Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Sources
Fetched 74.4kB in 1s (64.0kB/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0503DBBBDFAF548E
W: GPG error: [http://ftp.de.debian.org](http://ftp.de.debian.org) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
dave@dave-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  acpi-support apt aptitude at audacity avahi-daemon belocs-locales-bin
  bind9-host bluez-cups bogofilter-bdb brltty clamav clamav-freshclam
  command-not-found contact-lookup-applet cpp cpp-4.2 cups-pdf cupsddk
  cupsddk-drivers cupsys cupsys-bsd cupsys-client cupsys-common deskbar-applet
  dnsutils doc-base dvdauthor ekiga eog epiphany-browser-data epiphany-gecko
  espeak espeak-data evince evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-exchange evolution-plugins
  evolution-webcal f-spot fast-user-switch-applet ffmpeg filezilla
  filezilla-common gcalctool gcc gcc-4.2 gcc-4.2-base gconf-editor gedit
  gedit-common ghostscript ghostscript-x gimp gimp-data gksu
  gnome-accessibility-themes gnome-app-install gnome-applets gnome-cards-data
  gnome-control-center gnome-games gnome-games-data gnome-keyring gnome-mag
  gnome-media gnome-media-common gnome-nettool gnome-power-manager
  gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data
  gnome-themes gnome-utils gparted grub gstreamer0.10-ffmpeg
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-good
  gstreamer0.10-plugins-ugly gstreamer0.10-pulseaudio gtk2-engines
  gtk2-engines-murrine gtk2-engines-pixbuf gucharmap gvfs gvfs-backends
  gvfs-fuse hal hal-cups-utils hotkey-setup hpijs hplip hplip-data hugin-data
  hugin-tools initscripts inkscape iproute kdebase-bin kdebase-bin-kde3
  kdebase-kio-plugins kdebase-runtime kdebase-runtime-bin-kde4
  kdebase-runtime-data kdebase-runtime-data-common kdelibs4c2a kdelibs5
  kdepimlibs5 kdesktop khelpcenter kino lftp libaa1 libalut0 libart2.0-cil
  libavc1394-0 libbit-vector-perl libbonoboui2-0 libbonoboui2-common
  libbrlapi0.5 libcairo-perl libcupsimage2 libcupsys2 libcurl3 libcurl3-gnutls
  libcurl4-openssl-dev libdate-calc-perl libdvdnav4 libebook1.2-9 libecal1.2-7
  libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8
  libegroupwise1.2-13 libenchant1c2a libespeak1 libevent-perl
  libexchange-storage1.2-3 libflickrnet2.1.5-cil libfreebob0 libgail-common
  libgail18 libgcc1 libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1 libggz2
  libggzcore9 libggzmod4 libgimp2.0 libgksu2-0 libglade2.0-cil libglib-perl
  libglib2.0-cil libgnome-media0 libgnome-vfs2.0-cil libgnome-window-settings1
  libgnome2-canvas-perl libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil
  libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0
  libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra
  libgomp1 libgpod-common libgs8 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-0
  libgtk2.0-bin libgtk2.0-cil libgtkhtml3.14-19 libgtkmm-2.4-1c2a
  libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgweather1
  libhtml-parser-perl libiec61883-0 libio-pty-perl libjack0 libkadm55
  libkexiv2-3 libkrb5-dev libkrb53 libldap-2.4-2 libldap2-dev
  liblocale-gettext-perl libmagick10 libmono-addins-gui0.2-cil
  libmono-addins0.2-cil libmono-corlib1.0-cil libmono-corlib2.0-cil
  libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil
  libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil
  libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil
  libmono1.0-cil libmono2.0-cil libndesk-dbus1.0-cil libnet-dbus-perl
  libnm-glib0 libnotify1 libopal-2.2 libpam-modules libphonon4
  libpolkit-gnome0 libpq5 libpulse-browse0 libpulse0 libqt4-core libqt4-gui
  libqt4-qt3support libqt4-sql libquicktime1 librdf0 librsvg2-2
  librsvg2-common libsdl1.2debian libsdl1.2debian-alsa libsmbclient libsnmp15
  libsoprano4 libsoup2.4-1 libstdc++6 libstreamanalyzer0 libstreams0
  libstrigiqtdbusclient0 libterm-readkey-perl libtext-charwidth-perl
  libtext-iconv-perl libtotem-plparser10 libtracker-gtk0 libtunepimp5 libvte9
  libwnck22 libxine1 libxine1-bin libxine1-console libxine1-ffmpeg
  libxine1-misc-plugins libxine1-plugins libxine1-x libxml-parser-perl locales
  lsdvd metacity metacity-common mono-common mono-gac mono-jit mono-runtime
  mousetweaks network-manager network-manager-gnome notification-daemon
  ntfs-3g ntpdate ogmtools openoffice.org-hyphenation-en-us parted pciutils
  perl perl-base perl-modules pidgin-otr policykit-gnome poppler-utils
  pppoeconf pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf
  pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-utils python
  python-gconf python-glade2 python-gnome2 python-gnome2-desktop
  python-gobject python-gtk2 python-gtksourceview2 python-minimal python-vte
  python2.4 python2.4-minimal python2.5 python2.5-minimal rhythmbox rss-glx
  samba-common seahorse shared-mime-info smbclient sound-juicer
  system-tools-backends tomboy toshset totem totem-gstreamer totem-mozilla
  totem-plugins tracker tracker-search-tool transmission-common
  transmission-gtk usplash vamps vbetool vinagre vino w3m winbind wine wodim
  wpasupplicant xdg-user-dirs-gtk xserver-xorg-video-all
  xserver-xorg-video-ati xserver-xorg-video-openchrome yelp zenity
The following packages will be upgraded:
  acl acpi acpid adduser alsa-base alsa-utils anacron apmd app-install-data
  apt-utils aspell avahi-autoipd base-files base-passwd bash bash-completion
  binfmt-support binutils bluez-audio bluez-utils bogofilter bogofilter-common
  bsdutils bzip2 ca-certificates cabextract capplets-data cdparanoia cdrdao
  clamav-base cli-common comerr-dev compiz-fusion-plugins-extra
  compiz-fusion-plugins-main compizconfig-backend-gconf console-setup
  console-terminus console-tools consolekit coreutils cpio cron cryptsetup
  dash dbus dbus-x11 dcraw debconf debconf-i18n debianutils dhcdbd
  dhcp3-client dhcp3-common dictionaries-common dmsetup docbook-xml dosfstools
  dpkg dvd+rw-tools e2fslibs e2fsprogs ed eject enigmail epiphany-browser
  esound-common ethtool fdutils file file-roller findutils finger firestarter
  fontconfig fontconfig-config foo2zjs foomatic-db foomatic-db-engine
  foomatic-db-hpijs foomatic-filters fortune-mod fortunes-min fping freeglut3
  ftp fuse-utils gconf2 gconf2-common gdb gdebi gdebi-core gdm genisoimage
  gettext-base gimp-help-common gimp-help-en gnome-applets-data
  gnome-doc-utils gnome-icon-theme gnome-menus gnome-netstatus-applet
  gnome-pilot gnome-pilot-conduits gnome-screensaver gnome-session
  gnome-settings-daemon gnome-user-guide gnupg gocr gpgv grep groff-base
  gsfonts gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-tools gstreamer0.10-x
  guile-1.6-libs gzip hal-info hdparm hostname ifupdown imagemagick info
  initramfs-tools iptables iso-codes java-common kde-icons-oxygen kdelibs-data
  kdelibs5-data kdepimlibs-data klibc-utils klogd laptop-detect
  laptop-mode-tools libacl1 libao2 libapm1 libarchive1 libart-2.0-2 libasound2
  libaspell15 libatk1.0-0 libatm1 libatspi1.0-0 libattr1 libaudio2
  libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-compat-libdnssd1 libavahi-glib1 libavahi-gobject0 libavahi-qt3-1
  libavahi-ui0 libblkid1 libbluetooth2 libbonobo2-0 libbonobo2-common
  libboost-thread1.34.1 libbz2-1.0 libc6 libc6-dev libc6-i686 libcaca0
  libcairomm-1.0-1 libcarp-clan-perl libcdaudio1 libcdio-cdda0
  libcdio-paranoia0 libcdio7 libcdparanoia0 libck-connector0 libclucene0ldbl
  libcomerr2 libcompizconfig0 libconfig-tiny-perl libconsole libcroco3
  libcucul0 libcwidget3 libdaemon0 libdatrie0 libdb4.6 libdbus-1-3
  libdbus-glib-1-2 libdeskbar-tracker libdevmapper1.02.1 libdmx1 libdrm2
  libdv4 libedit2 libelfg0 libenca0 libesd-alsa0 libevent-rpc-perl libexempi3
  libexpat1 libfaad-dev libfaad0 libfftw3-3 libfile-find-rule-perl libflac++6
  libflac8 libfontconfig1 libfontenc1 libfreetype6 libfs6 libfuse2 libgadu3
  libgail-gnome-module libgc1c2 libgconf2-4 libgcrypt11 libgd2-noxpm
  libgl1-mesa-dri libgl1-mesa-glx libgnome2-0 libgnome2-common
  libgnomevfs2-bin libgpgme11 libgphoto2-2 libgphoto2-port0 libgps17
  libgraphviz4 libgsf-1-114 libgsf-1-common libgsl0ldbl
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk2.0-common
  libgtkhtml2-0 libgtkhtml3.16-cil libgtksourceview-common
  libgtksourceview1.0-0 libgtop2-7 libgtop2-common libguile-ltdl-1
  libgutenprint2 libgvfscommon0 libgweather-common libhal-storage1 libhal1
  libhesiod0 libhtml-tagset-perl libice6 libidl0 libidn11 libidn11-dev
  libieee1284-3 libimage-exiftool-perl libimlib2 libintl-perl libipc-run-perl
  libiptcdata0 libiw29 libkeyutils1 libkipi0 libklibc libkonq4 libkpathsea4
  liblcms1 liblircclient0 libltdl3 liblzo2-2 libmad0 libmagic1 libmagick++10
  libmcrypt4 libmms0 libmodplug0c2 libmono-cairo1.0-cil libmono-cairo2.0-cil
  libmono-data-tds1.0-cil libmono-security1.0-cil libmono-sharpzip0.84-cil
  libmono-system-data1.0-cil libmono0 libmpcdec3 libmpeg2-4 libmusicbrainz4c2a
  libmysqlclient15off libncurses5 libncursesw5 libndesk-dbus-glib1.0-cil
  libneon27 libnetpbm10 libnewt0.52 libnjb5 libnl1 libnss3-1d
  libnumber-compare-perl libofa0 libogg0 liboil0.3 liboobs-1-4 libopenobex1
  liborbit2 libotr2 libpam-gnome-keyring libpam-runtime libpam0g libpano12-0
  libpano12-bin libpaper-utils libpaper1 libpcap0.8 libpisock9 libpisync1
  libplot2c2 libpng12-0 libpolkit-dbus2 libpolkit-grant2 libpolkit2
  libportaudio0 libpt-1.10.10 libpt-1.10.10-plugins-alsa
  libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpth20 libpvm3
  libqthreads-12 libraptor1 librarian0 libreadline5 librecode0 librpc-xml-perl
  libruby1.8 libsamplerate0 libsane libsane-extras libsasl2-2 libsasl2-modules
  libscrollkeeper0 libsdl-gfx1.2-4 libsdl-mixer1.2 libsdl-sound1.2 libsensors3
  libsepol1 libsexy2 libsgutils1 libshout3 libsidplay1 libsigc++-2.0-0c2a
  libslang2 libslp1 libsm6 libsmpeg0 libsndfile1 libsnmp-base libsoundtouch1c2
  libspeex1 libsqlite3-0 libss2 libssl-dev libssl0.9.8 libsysfs2 libtag1c2a
  libtasn1-3 libtext-wrapi18n-perl libthai-data libthai0 libtheora0 libtiff4
  libtrackerclient0 libtre4 libtwolame0 libuniconf4.4 liburi-perl libusb-0.1-4
  libusplash0 libuuid1 libvisual-0.4-0 libvorbis0a libvorbisenc2
  libvorbisfile3 libvte-common libwavpack1 libwnck-common libwpd8c2a
  libwpg-0.1-1 libwps-0.1-1 libwrap0 libwvstreams4.4-base
  libwvstreams4.4-extras libwww-perl libwxbase2.6-0 libwxbase2.8-0
  libwxgtk2.6-0 libwxgtk2.8-0 libx11-data libx11-xcb1 libx86-1 libxau6 libxaw7
  libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcomposite1 libxdamage1 libxdmcp6
  libxevie1 libxext6 libxfont1 libxft2 libxi6 libxinerama1 libxkbfile1
  libxklavier12 libxml-twig-perl libxml2 libxml2-utils libxmlrpc-c3 libxp6
  libxplc0.3.13 libxrandr2 libxrender1 libxslt1.1 libxss1 libxtrap6 libxv1
  libxxf86misc1 libxxf86vm1 libzephyr3 linux-libc-dev linux-sound-base login
  logrotate lsb-base lsb-release lshw lsof ltrace lzma make makedev man-db
  manpages mawk meld memtest86+ mesa-utils mime-support min12xxw mktemp
  mlocate module-init-tools mount mscompress mtr-tiny myspell-en-gb
  myspell-en-us myspell-en-za mysql-common nano nautilus-sendto ncurses-base
  ncurses-bin net-tools netbase netcat netcat-traditional obex-data-server
  openprinting-ppds openssh-client openssl openssl-blacklist passwd patch
  pm-utils pnm2ppa policykit popularity-contest powermgmt-base powernowd ppp
  pppconfig procps python-apt python-brlapi python-cairo python-central
  python-dbus python-gdata python-gdbm python-gmenu python-gst0.10
  python-gtkhtml2 python-imaging python-libxml2 python-notify python-numeric
  python-support python-wxgtk2.8 rdesktop readahead readline-common
  reiserfsprogs rsync ruby ruby1.8 sane-utils scanbuttond scim-bridge-agent
  scim-bridge-client-gtk screen scrollkeeper sed sqlite3 ssh-askpass-gnome
  ssl-cert strace sudo synaptic sysklogd sysv-rc tar tasksel tasksel-data
  tcl8.4 tcpd tcpdump telnet testdisk time tk8.4 totem-common ttf-arabeyes
  ttf-arphic-uming ttf-dejavu-core ttf-freefont ttf-kochi-gothic
  ttf-kochi-mincho ttf-malayalam-fonts ttf-opensymbol ttf-thai-tlwg
  ttf-unfonts-core ttmkfdir tzdata ucf unattended-upgrades unzip update-inetd
  usbutils util-linux util-linux-locales uuid-runtime vim-common vim-tiny
  wamerican wbritish wget whiptail whois wifi-radar wipe wireless-tools wvdial
  x-ttcidfont-conf x11-apps x11-common x11-utils x11-xfs-utils x11-xkb-utils
  x11-xserver-utils xauth xbase-clients xdg-utils xfonts-utils xinit xkb-data
  xml-core xorg xsane xsane-common xscreensaver-data xscreensaver-gl
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-video-amd xserver-xorg-video-apm xserver-xorg-video-ark
  xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-dummy
  xserver-xorg-video-fbdev xserver-xorg-video-geode xserver-xorg-video-glint
  xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-i810
  xserver-xorg-video-intel xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nsc xserver-xorg-video-nv xserver-xorg-video-rendition
  xserver-xorg-video-s3 xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-vesa xserver-xorg-video-via
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xsltproc xterm xutils
  xutils-dev zlib1g zlib1g-dev
626 upgraded, 0 newly installed, 0 to remove and 341 not upgraded.
Need to get 456MB of archives.
After this operation, 84.2MB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by taurus on 2009-03-20
You are asking for trouble here.  You have jaunty in /etc/apt/sources.list which means adept will try to upgrade every package to jaunty so prepare for a breakage.


```
cat /etc/apt/sources.list
```

---

### Post by gewitty on 2009-03-20
Since I'm still running Hardy and have never had this problem before, I don't understand how the Jaunty sources list got in there.

I'll delete it from the list and see if that fixes the problem.

---

### Post by gewitty on 2009-03-20
That cleared it. I'm no longer getting any update messages. Hopefully, I'll just get the normal Hardy updates from now on.

Still mystified as to how that happened though.

---

### Post by taurus on 2009-03-20
Sorry to tell you but it didn't get it there all by itself.  You must have added it in there, ppa.launchpad.net (& sid), yourself.

---

### Post by gewitty on 2009-03-20
Normally, I'd agree with you and bow to superior knowledge. But in this case the problem only occurred after the interrupted Synaptic session. Bizzare I know, but I can say hand-on-heart that I didn't add Jaunty to the repositories list.

---

