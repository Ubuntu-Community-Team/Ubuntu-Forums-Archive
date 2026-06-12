---
title: "Installing KDE on gutsy 7.10(GNOME) from CD"
date: 2008-03-20
forum: Desktop Environments
---

### Post by JasonCYH on 2008-03-20
i'm running Gutsy with GNOME.I want to run the KDE enviroment on my PC.
Now we know we can use the synaptics pkg manger to get the kubuntu-desktop,[B]but is it possible to install KDE from a Kubuntu 7.10 CD?
[/B]
Internet costs in my area are costly,I've got no broadband,only dial-up.

Any ideas?

---

### Post by ajgreeny on 2008-03-20
You will need the Alternate install CD, not the Live/install CD to do this, I think.  It would have to be the Kubuntu live CD, however, not the Ubuntu live CD.

---

### Post by trippinnik on 2008-03-20
you can do it with the live cd as well.  Ubuntu usually recognizes Cds with deb packages on them, but if not you can add the cd as a repository.  Open Synaptic, go to sources and add cdrom.

---

### Post by JasonCYH on 2008-03-20
Hmm,I opened synaptic and did as you said,but I can't find kubuntu-desktop when clicked on the list...oh,well...maybe I'gotta download it,or am I not looking for it well?Do you think that I've missed out on certain areas?

---

### Post by trippinnik on 2008-03-22
Ok, I just looked at it myself again.  Open Synaptic - in the Installation Media Tab - Click "Add CD-rom"  the CD needs to be loaded in the drive.

---

### Post by aysiu on 2008-03-22
> **trippinnik said:**
> you can do it with the live cd as well.  Ubuntu usually recognizes Cds with deb packages on them, but if not you can add the cd as a repository.  No, you can't. There are very few .deb packages on the Desktop CD, not all of the ones you need to install *kubuntu-desktop*. You need the Alternate CD if you're going to *add* Kubuntu to Ubuntu. The Desktop CD can be used only to install Kubuntu a fresh (on top of or next to Ubuntu).

I've attached pictures of what packages the Desktop CD contains and have displayed below what packages *kubuntu-desktop* needs: ```
    *

      acpi [not powerpc]
          displays information on ACPI devices 

    *

      dep: acpi-support [not powerpc]
          a collection of useful events for acpi 

    *

      dep: acpid [not powerpc]
          Utilities for using ACPI power management 

    *

      dep: anacron
          cron-like program that doesn't go by time 

    *

      dep: apmd [i386]
          Utilities for Advanced Power Management (APM)
          also a virtual package provided by powersaved 

    *

      dep: ark
          graphical archiving tool for KDE 

    *

      dep: arts
          sound system from the official KDE release 

    *

      dep: avahi-daemon
          Avahi mDNS/DNS-SD daemon 

    *

      dep: bc
          The GNU bc arbitrary precision calculator language 

    *

      dep: cupsys
          Common UNIX Printing System(tm) - server 

    *

      dep: cupsys-bsd
          Common UNIX Printing System(tm) - BSD commands 

    *

      dep: cupsys-client
          Common UNIX Printing System(tm) - client programs (SysV) 

    *

      dep: dbus
          simple interprocess messaging system 

    *

      dep: dc
          The GNU dc arbitrary precision reverse-polish calculator 

    *

      dep: foomatic-db
          OpenPrinting printer support - database 

    *

      dep: foomatic-db-engine
          OpenPrinting printer support - programs 

    *

      dep: foomatic-db-hpijs
          OpenPrinting printer support - database for HPIJS driver 

    *

      dep: foomatic-filters
          OpenPrinting printer support - filters 

    *

      dep: genisoimage
          Creates ISO-9660 CD-ROM filesystem images 

    *

      dep: ghostscript-x
          The GPL Ghostscript PostScript/PDF interpreter - X Display support 

    *

      dep: hal
          Hardware Abstraction Layer 

    *

      dep: hotkey-setup [not powerpc]
          auto-configures laptop hotkeys 

    *

      dep: hwdb-client-kde
          KDE client program for the Ubuntu Hardware Database 

    *

      dep: kcontrol
          control center for KDE 

    *

      dep: kcron
          the KDE crontab editor 

    *

      dep: kde-guidance
          collection of KDE system administration tools for GNU/Linux 

    *

      dep: kde-style-polyester
          Polyester widget style and kwin decoration for KDE3 

    *

      dep: kde-systemsettings
          easy to use control centre for KDE 

    *

      dep: kdeadmin-kfile-plugins
          KDE file metainfo plugins for deb and rpm files 

    *

      dep: kdebase-kio-plugins
          core I/O slaves for KDE 

    *

      dep: kdegraphics-kfile-plugins
          KDE metainfo plugins for graphic files 

    *

      dep: kdemultimedia-kfile-plugins
          au/avi/m3u/mp3/ogg/wav plugins for kfile 

    *

      dep: kdemultimedia-kio-plugins
          enables the browsing of audio CDs under Konqueror 

    *

      dep: kdenetwork-filesharing
          network filesharing configuration module for KDE 

    *

      dep: kdenetwork-kfile-plugins
          torrent metainfo plugin for KDE 

    *

      dep: kdepasswd
          password changer for KDE 

    *

      dep: kdeprint
          print system for KDE 

    *

      dep: kdesktop
          miscellaneous binaries and files for the KDE desktop 

    *

      dep: kdm
          X display manager for KDE 

    *

      dep: kdnssd
          Zeroconf support for KDE 

    *

      dep: kghostview
          PostScript viewer for KDE 

    *

      dep: khelpcenter
          help center for KDE 

    *

      dep: kicker
          desktop panel for KDE 

    *

      dep: kio-apt
          an apt-cache ioslave for KDE 

    *

      dep: kio-locate
          kio-slave for the locate command 

    *

      dep: kmenuedit
          menu editor for KDE 

    *

      dep: kmix
          sound mixer applet for KDE 

    *

      dep: knetworkconf
          KDE network configuration tool 

    *

      dep: konq-plugins
          plugins for Konqueror, the KDE file/web/doc browser 

    *

      dep: konsole
          X terminal emulator for KDE 

    *

      dep: kpdf
          PDF viewer for KDE 

    *

      dep: ksmserver
          session manager for KDE 

    *

      dep: ksnapshot
          screenshot utility for KDE 

    *

      dep: ksplash
          the KDE splash screen 

    *

      dep: ksplash-engine-moodin
          fading splash screen engine for KDE 

    *

      dep: ksvg
          SVG viewer for KDE 

    *

      dep: ksystemlog
          system log viewer tool for KDE 

    *

      dep: kubuntu-artwork-usplash
          kubuntu artwork for usplash 

    *

      dep: kwin
          the KDE window manager 

    *

      dep: language-selector-qt
          Language selector for kubuntu linux 

    *

      dep: lftp
          Sophisticated command-line FTP/HTTP client programs 

    *

      dep: libarts1-akode
          akode plugin for aRts 

    *

      dep: libgl1-mesa-glx
          A free implementation of the OpenGL API -- GLX runtime 

    *

      dep: libglut3
          the OpenGL Utility Toolkit
          also a virtual package provided by freeglut3 

    *

      dep: libpam-foreground
          create lockfiles describing which users own which console 

    *

      dep: libqt-perl
          Perl bindings for the Qt library 

    *

      dep: libsasl2-modules
          Pluggable Authentication Modules for SASL 

    *

      dep: libxp6
          X Printing Extension (Xprint) client library 

    *

      dep: openprinting-ppds
          OpenPrinting printer support - PostScript PPD files 

    *

      dep: pbbuttonsd [powerpc]
          PBButtons daemon to handle special hotkeys of Apple computers 

    *

      dep: pnm2ppa
          PPM to PPA converter 

    *

      dep: powermanagement-interface
          platform neutral powermanagement interface 

    *

      dep: qca-tls
          TLS plugin for the Qt Cryptographic Architecture (QCA) 

    *

      dep: readahead
          read files into the page cache 

    *

      dep: screen
          a terminal multiplexor with VT100/ANSI terminal emulation 

    *

      dep: slocate
          Secure replacement of findutil's locate 

    *

      dep: smbclient
          a LanManager-like simple client for Unix 

    *

      dep: software-properties-kde
          manage the repositories that you install software from 

    *

      dep: ttf-bitstream-vera
          The Bitstream Vera family of free TrueType fonts 

    *

      dep: ttf-dejavu-core
          Vera font family derivate with additional characters 

    *

      dep: ttf-freefont
          Freefont Serif, Sans and Mono Truetype fonts 

    *

      dep: unzip
          De-archiver for .zip files 

    *

      dep: usplash
          Userspace bootsplash utility 

    *

      dep: vorbis-tools
          several Ogg Vorbis tools 

    *

      dep: x-ttcidfont-conf
          Configure TrueType and CID fonts for X 

    *

      dep: xkb-data
          X Keyboard Extension (XKB) configuration data 

    *

      dep: xorg
          X.Org X Window System 

    *

      dep: zip
          Archiver for .zip files 

    *

      rec: adept
          package management suite for KDE 

    *

      rec: akregator
          RSS feed aggregator for KDE 

    *

      rec: amarok
          versatile and easy to use audio player for KDE 

    *

      rec: apport-qt
          Qt4 frontend for the apport crash report system 

    *

      rec: avahi-autoipd
          Avahi IPv4LL network address configuration daemon 

    *

      rec: bluez-cups
          Bluetooth printer driver for CUPS 

    *

      rec: bluez-utils
          Bluetooth tools and daemons 

    *

      rec: bogofilter
          a fast Bayesian spam filter (dummy package) 

    *

      rec: brltty
          Access software for a blind person using a soft braille terminal 

    *

      rec: cdparanoia
          audio extraction tool for sampling CDs 

    *

      rec: cdrdao
          records CDs in Disk-At-Once (DAO) mode 

    *

      rec: cups-pdf
          PDF printer for CUPS 

    *

      rec: digikam [not powerpc]
          digital photo management application for KDE 

    *

      rec: discover1
          hardware identification system 

    *

      rec: dolphin
          File manager for KDE focusing on usability 

    *

      rec: dvd+rw-tools
          DVD+-RW/R tools 

    *

      rec: foo2zjs
          Support for printing to ZjStream-based printers 

    *

      rec: foomatic-db-gutenprint
          OpenPrinting printer support - database for Gutenprint printer drivers 

    *

      rec: fortune-mod
          provides fortune cookies on demand 

    *

      rec: gcc
          The GNU C compiler 

    *

      rec: gdebi-kde
          Simple tool to install deb files 

    *

      rec: gtk-qt-engine
          theme engine using Qt for GTK+ 2.x 

    *

      rec: gwenview
          image viewer for KDE 

    *

      rec: hplip
          HP Linux Printing and Imaging System (HPLIP) 

    *

      rec: hplip-gui
          HP Linux Printing and Imaging - GUI utilities 

    *

      rec: k3b
          A sophisticated KDE CD burning application 

    *

      rec: kaddressbook
          KDE NG addressbook application 

    *

      rec: kaffeine-xine
          Xine engine for kaffeine media player 

    *

      rec: kamera
          digital camera io_slave for Konqueror 

    *

      rec: karm
          KDE time tracker tool 

    *

      rec: katapult
          item launcher for KDE 

    *

      rec: kate
          advanced text editor for KDE 

    *

      rec: kbstate
          a keyboard status applet for KDE 

    *

      rec: kde-guidance-powermanager
          HAL based power manager applet 

    *

      rec: kde-icons-mono
          a monochromatic icons theme for KDE 

    *

      rec: kdebluetooth
          KDE Bluetooth Framework 

    *

      rec: kdepim-kio-plugins
          KDE pim I/O Slaves 

    *

      rec: kdepim-wizards
          KDE server configuration wizards 

    *

      rec: kdesudo
          sudo frontend for KDE 

    *

      rec: keep
          backup system for KDE 

    *

      rec: kfind
          file-find utility for KDE 

    *

      rec: kio-umountwrapper
          progress dialog for safely removing devices in KDE. 

    *

      rec: kipi-plugins [not powerpc]
          image manipulation/handling plugins for KIPI aware programs 

    *

      rec: klipper
          clipboard utility for KDE 

    *

      rec: kmag
          a screen magnifier for KDE 

    *

      rec: kmail
          KDE Email client 

    *

      rec: kmailcvt
          KDE KMail mail folder converter 

    *

      rec: kmilo
          laptop special keys support for KDE 

    *

      rec: kmousetool
          KDE mouse manipulation tool for the disabled 

    *

      rec: kmplayer-konq-plugins
          KMPlayer plugin for KHTML/Konqueror 

    *

      rec: knotes
          KDE sticky notes 

    *

      rec: konqueror
          KDE's advanced file manager, web browser and document viewer 

    *

      rec: konqueror-nsplugins
          Netscape plugin support for Konqueror 

    *

      rec: kontact
          KDE pim application 

    *

      rec: konversation
          user friendly Internet Relay Chat (IRC) client for KDE 

    *

      rec: kooka
          scanner program for KDE 

    *

      rec: kopete
          instant messenger for KDE 

    *

      rec: korganizer
          KDE personal organizer 

    *

      rec: kpf
          public fileserver for KDE 

    *

      rec: kppp
          modem dialer and ppp frontend for KDE 

    *

      rec: krdc
          Remote Desktop Connection for KDE 

    *

      rec: krfb
          Desktop Sharing for KDE 

    *

      rec: kscreensaver
          additional screen savers released with KDE 

    *

      rec: ksysguard
          system guard for KDE 

    *

      rec: ktorrent
          BitTorrent client for KDE 

    *

      rec: kubuntu-default-settings
          Default settings and artwork for the Kubuntu desktop 

    *

      rec: kubuntu-docs
          kubuntu documentation 

    *

      rec: kubuntu-konqueror-shortcuts
          Konqueror shortcuts for the Kubuntu wiki, Ubuntu Docs and Launchpad 

    *

      rec: kvkbd
          Virtual keyboard for KDE 

    *

      rec: kwalletmanager
          wallet manager for KDE 

    *

      rec: landscape-client
          Placeholder for the Landscape client 

    *

      rec: laptop-detect
          attempt to detect a laptop 

    *

      rec: libgl1-mesa-dri
          A free implementation of the OpenGL API -- DRI modules 

    *

      rec: libnss-mdns
          NSS module for Multicast DNS name resolution 

    *

      rec: linux-headers-generic [not powerpc]
          Generic Linux kernel headers 

    *

      rec: linux-headers-powerpc [powerpc]
          Linux kernel headers on PowerPC 

    *

      rec: linux-headers-powerpc64-smp [powerpc]
          Linux kernel headers on PowerPC64 SMP 

    *

      rec: make
          The GNU version of the "make" utility. 

    *

      rec: min12xxw
          Printer driver for KonicaMinolta PagePro 1[234]xxW 

    *

      rec: network-manager-kde
          KDE systray applet for controlling NetworkManager 

    *

      rec: networkstatus
          KDE network status monitor 

    *

      rec: openoffice.org-calc
          OpenOffice.org office suite - spreadsheet 

    *

      rec: openoffice.org-draw
          OpenOffice.org office suite - drawing 

    *

      rec: openoffice.org-impress
          OpenOffice.org office suite - presentation 

    *

      rec: openoffice.org-java-common
          OpenOffice.org office suite Java support arch. independent files 

    *

      rec: openoffice.org-kde
          KDE Integration for OpenOffice.org (Widgets, Dialogs, Addressbook) 

    *

      rec: openoffice.org-math
          OpenOffice.org office suite - equation editor 

    *

      rec: openoffice.org-writer
          OpenOffice.org office suite - word processor 

    *

      rec: pinentry-qt
          Qt-based PIN or pass-phrase entry dialog for GnuPG 

    *

      rec: powernowd
          control cpu speed and voltage using 2.6 kernel interface
          also a virtual package provided by powersaved 

    *

      rec: pxljr
          Driver for HP's Color LaserJet 35xx/36xx color laser printers 

    *

      rec: rdesktop
          RDP client for Windows NT/2000 Terminal Server 

    *

      rec: restricted-manager-kde
          manage non-free hardware drivers - KDE frontend 

    *

      rec: scim-qtimm
          SCIM context plugin for qt-immodule 

    *

      rec: skim
          smart common input method platform for KDE 

    *

      rec: speedcrunch
          High precision calculator 

    *

      rec: splix
          Driver for Samsung's SPL2 (bw) and SPLc (color) laser printers 

    *

      rec: strigi-applet
          KDE applet for Strigi Desktop Search 

    *

      rec: strigi-daemon
          fast indexing and searching tool for your personal data (daemon) 

    *

      rec: ttf-arabeyes
          Arabeyes GPL TrueType Arabic fonts 

    *

      rec: ttf-arphic-ukai
          "AR PL ZenKai Uni" Chinese Unicode TrueType font Kaiti style 

    *

      rec: ttf-arphic-uming
          "AR PL ShanHeiSun Uni" Chinese Unicode TrueType font Mingti style 

    *

      rec: ttf-gentium
          Gentium TrueType font 

    *

      rec: ttf-indic-fonts-core
          Core collection of free Indian language fonts 

    *

      rec: ttf-kochi-gothic
          Kochi Subst Gothic Japanese TrueType font without naga10
          also a virtual package provided by ttf-kochi-gothic-naga10 

    *

      rec: ttf-kochi-mincho
          Kochi Subst Mincho Japanese TrueType font without naga10
          also a virtual package provided by ttf-kochi-mincho-naga10 

    *

      rec: ttf-lao
          TrueType font for Lao language 

    *

      rec: ttf-malayalam-fonts
          Free TrueType fonts for the Malayalam language 

    *

      rec: ttf-mgopen
          Magenta Open Truetype fonts 

    *

      rec: ttf-thai-tlwg
          Thai fonts in TrueType format 

    *

      rec: ttf-unfonts-core
          Un series Korean TrueType fonts 

    *

      rec: wodim
          command line CD/DVD writing tool 

    *

      rec: wvdial
          PPP dialer with built-in intelligence 

    *

      rec: xcursor-themes
          Base X cursor themes 

    *

      rec: xdg-utils
          Desktop integration utilities from freedesktop.org 

    *

      rec: xresprobe
          X Resolution Probe 
``` As you can see, the two do not compare at all.

---

