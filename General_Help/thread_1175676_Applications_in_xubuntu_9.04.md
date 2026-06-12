---
title: "Applications in xubuntu 9.04"
date: 2009-06-01
forum: General Help
---

### Post by borgward on 2009-06-01
I need a complete list of all applications included in xubuntu 9.04. I am currently running Knoppix 5.1.1 HDD install on Dell Latitude CPi. 400MHz PII 256 MB RAM. It runs better than any other distro that I have run on it. I looked at [http://www.xubuntu.org/tour](http://www.xubuntu.org/tour) which did not give me much info.

---

### Post by zonination on 2009-06-01
> **borgward said:**
> I need a complete list of all applications included in xubuntu 9.04. I am currently running Knoppix 5.1.1 HDD install on Dell Latitude CPi. 400MHz PII 256 MB RAM. It runs better than any other distro that I have run on it. I looked at [http://www.xubuntu.org/tour](http://www.xubuntu.org/tour) which did not give me much info.

If you're currently using a fresh install of Xubuntu, you can do this:
```
dpkg -l
```

To put the list into a file (since it might flood the terminal):
```
dpkg -l > packages.txt
```

For the sake of helping you out, however, I virtualized a fresh install of Xubuntu and provided the list here:

```
                                                                     
                                                                     
                                                                     
                                             
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                       Version                            Description
+++-==========================================-==================================-================================================================
ii  a2ps                                       1:4.14-1                           GNU a2ps - 'Anything to PostScript' converter and pretty-printer
ii  abiword                                    2.6.6-0ubuntu1                     efficient, featureful word processor with collaboration
ii  abiword-common                             2.6.6-0ubuntu1                     efficient, featureful word processor with collaboration -- commo
ii  abiword-help                               2.6.6-0ubuntu1                     online help for AbiWord
ii  abiword-plugin-grammar                     2.6.6-0ubuntu1                     grammar checking plugin for AbiWord
ii  abiword-plugin-mathview                    2.6.6-0ubuntu1                     equation editor plugin for AbiWord
ii  abiword-plugins                            2.6.6-0ubuntu1                     transitional plugins package for AbiWord
ii  acl                                        2.2.47-2                           Access control list utilities
ii  acpi-support                               0.121                              scripts for handling many ACPI events
ii  acpid                                      1.0.6-9ubuntu4                     Utilities for using ACPI power management
ii  adduser                                    3.110ubuntu5                       add and remove users and groups
ii  alsa-base                                  1.0.18.dfsg-1ubuntu8               ALSA driver configuration files
ii  alsa-utils                                 1.0.18-1ubuntu11                   ALSA utilities
ii  anacron                                    2.3-13.1ubuntu6                    cron-like program that doesn't go by time
ii  apmd                                       3.2.2-12ubuntu3                    Utilities for Advanced Power Management (APM)
ii  app-install-data                           0.7.6                              Ubuntu applications (data files)
ii  app-install-data-commercial                11.9.04                            Transitional package
ii  apparmor                                   2.3+1289-0ubuntu14                 User-space parser utility for AppArmor
ii  apparmor-utils                             2.3+1289-0ubuntu14                 Utilities for controlling AppArmor
ii  apport                                     1.0-0ubuntu5                       automatically generate crash reports for debugging
ii  apport-gtk                                 1.0-0ubuntu5                       GTK+ frontend for the apport crash report system
ii  apt                                        0.7.20.2ubuntu6                    Advanced front-end for dpkg
ii  apt-transport-https                        0.7.20.2ubuntu6                    APT https transport
ii  apt-utils                                  0.7.20.2ubuntu6                    APT utility programs
ii  apt-xapian-index                           0.16                               maintenance tools for a Xapian index of Debian packages
ii  aptitude                                   0.4.11.11-1ubuntu1                 terminal-based package manager
ii  apturl                                     0.3.3ubuntu1                       install packages using the apt protocol
ii  aspell                                     0.60.6-1                           GNU Aspell spell-checker
ii  aspell-en                                  6.0-0-5.1                          English dictionary for GNU Aspell
ii  at                                         3.1.10.2ubuntu2                    Delayed job execution and batch processing
ii  aumix                                      2.8-22                             Simple text-based mixer control program
ii  avahi-autoipd                              0.6.23-4ubuntu4                    Avahi IPv4LL network address configuration daemon
ii  avahi-daemon                               0.6.23-4ubuntu4                    Avahi mDNS/DNS-SD daemon
ii  avahi-utils                                0.6.23-4ubuntu4                    Avahi browsing, publishing and discovery utilities
ii  base-files                                 5ubuntu4                           Debian base system miscellaneous files
ii  base-passwd                                3.5.21                             Debian base system master password and group files
ii  bash                                       3.2-5ubuntu1                       The GNU Bourne Again SHell
ii  bash-completion                            20080705ubuntu3                    programmable completion for the bash shell
ii  bc                                         1.06.94-3ubuntu1                   The GNU bc arbitrary precision calculator language
ii  bind9-host                                 1:9.5.1.dfsg.P2-1                  Version of 'host' bundled with BIND 9.X
ii  binutils                                   2.19.1-0ubuntu3                    The GNU assembler, linker and binary utilities
ii  binutils-static                            2.19.1-0ubuntu3                    statically linked binutils tools
ii  bluetooth                                  4.32-0ubuntu4                      Bluetooth support
ii  bluez                                      4.32-0ubuntu4                      Bluetooth tools and daemons
ii  bluez-alsa                                 4.32-0ubuntu4                      Bluetooth audio support
ii  bluez-cups                                 4.32-0ubuntu4                      Bluetooth printer driver for CUPS
ii  bluez-gnome                                1.8-0ubuntu5                       Bluetooth utilities for GNOME
ii  bluez-gstreamer                            4.32-0ubuntu4                      Bluetooth gstreamer support
ii  bluez-utils                                4.32-0ubuntu4                      Transitional package
ii  bogofilter                                 1.1.7-1ubuntu1                     a fast Bayesian spam filter (dummy package)
ii  bogofilter-bdb                             1.1.7-1ubuntu1                     a fast Bayesian spam filter (Berkeley DB)
ii  bogofilter-common                          1.1.7-1ubuntu1                     a fast Bayesian spam filter (common files)
ii  brasero                                    2.26.0-0ubuntu3                    CD/DVD burning application for GNOME
ii  bsdmainutils                               6.1.10ubuntu3                      collection of more utilities from FreeBSD
ii  bsdutils                                   1:2.14.2-1ubuntu4                  Basic utilities from 4.4BSD-Lite
ii  busybox-initramfs                          1:1.10.2-2ubuntu7                  Standalone shell setup for initramfs
ii  bzip2                                      1.0.5-1ubuntu1                     high-quality block-sorting file compressor - utilities
ii  ca-certificates                            20080809                           Common CA certificates
ii  catfish                                    0.3.2-1                            file search tool that support several different engines
ii  cdparanoia                                 3.10.2+debian-5                    audio extraction tool for sampling CDs
ii  command-not-found                          0.2.34ubuntu3                      Suggest installation of packages in interactive bash sessions
ii  command-not-found-data                     0.2.34ubuntu3                      Set of data files for command-not-found.
ii  console-setup                              1.28ubuntu8                        Set up the font and the keyboard on the console
ii  console-terminus                           4.26-2.1                           Fixed-width fonts for fast reading on the Linux console
ii  consolekit                                 0.3.0-2ubuntu3                     framework for defining and tracking users, sessions and seats
ii  coreutils                                  6.10-6ubuntu1                      The GNU core utilities
ii  cpio                                       2.9-15ubuntu1                      GNU cpio -- a program to manage archives of files
ii  cpp                                        4:4.3.3-1ubuntu1                   The GNU C preprocessor (cpp)
ii  cpp-4.3                                    4.3.3-5ubuntu4                     The GNU C preprocessor
ii  cron                                       3.0pl1-105ubuntu1                  management of regular background processing
ii  cups                                       1.3.9-17ubuntu1                    Common UNIX Printing System(tm) - server
ii  cups-bsd                                   1.3.9-17ubuntu1                    Common UNIX Printing System(tm) - BSD commands
ii  cups-client                                1.3.9-17ubuntu1                    Common UNIX Printing System(tm) - client programs (SysV)
ii  cups-common                                1.3.9-17ubuntu1                    Common UNIX Printing System(tm) - common files
ii  cups-driver-gutenprint                     5.2.3-0ubuntu5                     printer drivers for CUPS
ii  cupsddk                                    1.2.3-5ubuntu1                     CUPS Driver Development Kit
ii  cupsddk-drivers                            1.2.3-5ubuntu1                     CUPS Driver Development Kit - Driver files
ii  cupsys-driver-gutenprint                   5.2.3-0ubuntu5                     Transitional package
ii  dash                                       0.5.4-12ubuntu2                    POSIX-compliant shell
ii  dbus                                       1.2.12-0ubuntu2                    simple interprocess messaging system
ii  dbus-x11                                   1.2.12-0ubuntu2                    simple interprocess messaging system (X11 deps)
ii  dc                                         1.06.94-3ubuntu1                   The GNU dc arbitrary precision reverse-polish calculator
ii  debconf                                    1.5.26ubuntu3                      Debian configuration management system
ii  debconf-i18n                               1.5.26ubuntu3                      full internationalization support for debconf
ii  debianutils                                2.30ubuntu3                        Miscellaneous utilities specific to Debian
ii  defoma                                     0.11.10-0.2ubuntu1                 Debian Font Manager -- automatic font configuration framework
ii  desktop-file-utils                         0.15-1ubuntu7                      Utilities for .desktop files
ii  dhcp3-client                               3.1.1-5ubuntu8                     DHCP client
ii  dhcp3-common                               3.1.1-5ubuntu8                     common files used by all the dhcp3* packages
ii  dictionaries-common                        1.0.0ubuntu1                       Common utilities for spelling dictionary tools
ii  diff                                       2.8.1-12ubuntu1                    File comparison utilities
ii  dmidecode                                  2.9-1ubuntu1                       Dump Desktop Management Interface data
ii  dmsetup                                    2:1.02.27-4ubuntu5                 The Linux Kernel Device Mapper userspace library
ii  dmz-cursor-theme                           0.4.1                              Style neutral, scalable cursor theme
ii  dnsmasq-base                               2.47-3                             A small caching DNS proxy and DHCP/TFTP server
ii  dnsutils                                   1:9.5.1.dfsg.P2-1                  Clients provided with BIND
ii  doc-base                                   0.8.20                             utilities to manage online documentation
ii  docbook-xml                                4.5-6                              standard XML documentation system, for software and systems
ii  dosfstools                                 3.0.1-1                            utilities for making and checking MS-DOS FAT filesystems
ii  dpkg                                       1.14.24ubuntu1                     Debian package management system
ii  dvd+rw-tools                               7.1-4                              DVD+-RW/R tools
ii  e2fslibs                                   1.41.4-1ubuntu1                    ext2 filesystem libraries
ii  e2fsprogs                                  1.41.4-1ubuntu1                    ext2/ext3/ext4 file system utilities
ii  ed                                         0.7-3ubuntu1                       The classic unix line editor
ii  eject                                      2.1.5+deb1+cvs20081104-5           ejects CDs and operates CD-Changers under Linux
ii  esound-clients                             0.2.40-0ubuntu3                    Enlightened Sound Daemon - clients
ii  esound-common                              0.2.40-0ubuntu3                    Enlightened Sound Daemon - Common files
ii  ethtool                                    6+20080913-1                       display or change Ethernet device settings
ii  evince                                     2.26.0-0ubuntu1                    Document (postscript, pdf) viewer
ii  exo-utils                                  0.3.100-1ubuntu1                   Utility files for libexo
ii  fglrx-modaliases                           2:8.600-0ubuntu2                   Identifiers supported by the ATI graphics driver
ii  file                                       4.26-2ubuntu3                      Determines file type using "magic" numbers
ii  file-roller                                2.26.1-0ubuntu1                    an archive manager for GNOME
ii  findutils                                  4.4.0-2ubuntu4                     utilities for finding files--find, xargs
ii  finger                                     0.17-12                            user information lookup program
ii  firefox                                    3.0.8+nobinonly-0ubuntu3           meta package for the popular mozilla web browser
ii  firefox-3.0                                3.0.8+nobinonly-0ubuntu3           safe and easy web browser from Mozilla
ii  firefox-3.0-branding                       3.0.8+nobinonly-0ubuntu3           Package that ships the firefox branding
ii  firefox-3.0-gnome-support                  3.0.8+nobinonly-0ubuntu3           Support for Gnome in Mozilla Firefox
ii  fontconfig                                 2.6.0-1ubuntu12                    generic font configuration library - support binaries
ii  fontconfig-config                          2.6.0-1ubuntu12                    generic font configuration library - configuration
ii  foo2zjs                                    20090217-0ubuntu4                  Support for printing to ZjStream-based printers
ii  foomatic-db                                20090218-0ubuntu3                  OpenPrinting printer support - database
ii  foomatic-db-engine                         4.0.0-0ubuntu6                     OpenPrinting printer support - programs
ii  foomatic-db-hpijs                          20090218-0ubuntu3                  OpenPrinting printer support - database for HPIJS driver
ii  foomatic-filters                           4.0.0-0ubuntu9                     OpenPrinting printer support - filters
ii  fortune-mod                                1:1.99.1-3.1ubuntu3                provides fortune cookies on demand
ii  fortunes-min                               1:1.99.1-3.1ubuntu3                Data files containing fortune cookies
ii  friendly-recovery                          0.2.8.1                            Make recovery more user-friendly
ii  ftp                                        0.17-18                            The FTP client
ii  fuse-utils                                 2.7.4-1.1ubuntu4                   Filesystem in USErspace (utilities)
ii  gamin                                      0.1.9-2ubuntu4                     File and directory monitoring system
ii  gcalctool                                  5.26.0-0ubuntu1                    A GTK2 desktop calculator
ii  gcc                                        4:4.3.3-1ubuntu1                   The GNU C compiler
ii  gcc-4.3                                    4.3.3-5ubuntu4                     The GNU C compiler
ii  gcc-4.3-base                               4.3.3-5ubuntu4                     The GNU Compiler Collection (base package)
ii  gconf2                                     2.26.0-0ubuntu1                    GNOME configuration database system (support tools)
ii  gconf2-common                              2.26.0-0ubuntu1                    GNOME configuration database system (common files)
ii  gdb                                        6.8-3ubuntu2                       The GNU Debugger
ii  gdebi                                      0.4.9                              Simple tool to install deb files
ii  gdebi-core                                 0.4.9                              Simple tool to install deb files
ii  gdm                                        2.20.10-0ubuntu2                   GNOME Display Manager
ii  genisoimage                                9:1.1.9-1ubuntu1                   Creates ISO-9660 CD-ROM filesystem images
ii  gettext-base                               0.17-6ubuntu2                      GNU Internationalization utilities for the base system
ii  ggzcore-bin                                0.0.14.1-1ubuntu1                  GGZ Gaming Zone: various command-line helper programs
ii  ghostscript                                8.64.dfsg.1-0ubuntu8               The GPL Ghostscript PostScript/PDF interpreter
ii  ghostscript-x                              8.64.dfsg.1-0ubuntu8               The GPL Ghostscript PostScript/PDF interpreter - X Display suppo
ii  gigolo                                     0.3.0-0ubuntu1                     frontend to manage connections to remote filesystems using GIO/G
ii  gimp                                       2.6.6-0ubuntu1                     The GNU Image Manipulation Program
ii  gimp-data                                  2.6.6-0ubuntu1                     Data files for GIMP
ii  gksu                                       2.0.2-1ubuntu2                     graphical frontend to su
ii  gnome-accessibility-themes                 2.26.0-0ubuntu1                    accessibility themes for the GNOME 2 desktop
ii  gnome-app-install                          0.5.24-0ubuntu1                    GNOME Application Installer
ii  gnome-cards-data                           1:2.26.1-0ubuntu2                  data files for the GNOME card games
ii  gnome-desktop-data                         1:2.26.1-0ubuntu1                  Common files for GNOME 2 desktop apps
ii  gnome-doc-utils                            0.16.0-0ubuntu1                    a collection of documentation utilities for the GNOME project
ii  gnome-games                                1:2.26.1-0ubuntu2                  games for the GNOME desktop
ii  gnome-games-data                           1:2.26.1-0ubuntu2                  data files for the GNOME games
ii  gnome-icon-theme                           2.26.0-0ubuntu1                    GNOME Desktop icon theme
ii  gnome-keyring                              2.26.1-0ubuntu1                    GNOME keyring services (daemon and tools)
ii  gnome-media                                2.26.0-0ubuntu3                    GNOME media utilities
ii  gnome-media-common                         2.26.0-0ubuntu3                    GNOME media utilities - common files
ii  gnome-mime-data                            2.18.0-1                           base MIME and Application database for GNOME.
ii  gnome-mount                                0.8-1ubuntu5                       wrapper for (un)mounting and ejecting storage devices
ii  gnome-power-manager                        2.24.2-2ubuntu8                    power management tool for the GNOME desktop
ii  gnome-screensaver                          2.24.0-0ubuntu6                    GNOME screen saver and locker
ii  gnome-system-monitor                       2.26.0.1-0ubuntu1                  Process viewer and system resource monitor for GNOME 2
ii  gnome-system-tools                         2.22.2-0ubuntu3                    Cross-platform configuration utilities for GNOME
ii  gnumeric                                   1.8.4-3ubuntu2                     spreadsheet application for GNOME - main program
ii  gnumeric-common                            1.8.4-3ubuntu2                     spreadsheet application for GNOME - common files
ii  gnumeric-doc                               1.8.4-3ubuntu2                     spreadsheet application for GNOME - documentation
ii  gnumeric-gtk                               1.8.4-3ubuntu2                     spreadsheet application for GNOME - Transitional package
ii  gnupg                                      1.4.9-3ubuntu1                     GNU privacy guard - a free PGP replacement
ii  gpgv                                       1.4.9-3ubuntu1                     GNU privacy guard - signature verification tool
ii  gpicview                                   0.1.11-1                           lightweight image viewer
ii  grep                                       2.5.3~dfsg-6ubuntu1                GNU grep, egrep and fgrep
ii  groff-base                                 1.18.1.1-22build1                  GNU troff text-formatting system (base system components)
ii  grub                                       0.97-29ubuntu53                    GRand Unified Bootloader
ii  grub-common                                1.96+20080724-12ubuntu2            GRand Unified Bootloader, version 2 (common files)
ii  gsfonts                                    1:8.11+urwcyr1.0.7~pre44-3         Fonts for the Ghostscript interpreter(s)
ii  gstreamer0.10-alsa                         0.10.22-5                          GStreamer plugin for ALSA
ii  gstreamer0.10-gnomevfs                     0.10.22-5                          GStreamer plugin for GnomeVFS
ii  gstreamer0.10-plugins-base                 0.10.22-5                          GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-good                 0.10.14-1                          GStreamer plugins from the "good" set
ii  gstreamer0.10-x                            0.10.22-5                          GStreamer plugins for X11 and Pango
ii  gtk2-engines                               1:2.18.1-0ubuntu1                  theme engines for GTK+ 2.x
ii  gtk2-engines-murrine                       0.90.3-1ubuntu1                    cairo-based gtk+-2.0 theme engine
ii  gtk2-engines-pixbuf                        2.16.1-0ubuntu2                    Pixbuf-based theme for GTK+ 2.x
ii  gtk2-engines-xfce                          2.6.0-1                            A GTK+-2.0 theme engine for Xfce
ii  gucharmap                                  1:2.26.1-0ubuntu1                  Unicode character picker and font browser
ii  guile-1.8-libs                             1.8.5+1-4.1ubuntu1                 Main Guile libraries
ii  gvfs                                       1.2.2-0ubuntu1                     userspace virtual filesystem - server
ii  gvfs-backends                              1.2.2-0ubuntu1                     userspace virtual filesystem - backends
ii  gvfs-bin                                   1.2.2-0ubuntu1                     userspace virtual filesystem - binaries
ii  gzip                                       1.3.12-6ubuntu2                    The GNU compression utility
ii  hal                                        0.5.12~rc1+git20090403-0ubuntu1    Hardware Abstraction Layer
ii  hal-cups-utils                             0.6.19+git20090217-0ubuntu7        CUPS integration with HAL
ii  hal-info                                   20090407-0ubuntu1                  Hardware Abstraction Layer - fdi files
ii  hdparm                                     8.9-3ubuntu3                       tune hard disk parameters for high performance
ii  hicolor-icon-theme                         0.10-1ubuntu1                      default fallback theme for FreeDesktop.org icon themes
ii  hostname                                   2.95                               utility to set/show the host name or domain name
ii  hotkey-setup                               0.1-23ubuntu12                     auto-configures laptop hotkeys
ii  hpijs                                      3.9.2-3ubuntu4                     HP Linux Printing and Imaging - gs IJS driver (hpijs)
ii  hplip                                      3.9.2-3ubuntu4                     HP Linux Printing and Imaging System (HPLIP)
ii  hplip-data                                 3.9.2-3ubuntu4                     HP Linux Printing and Imaging - data files
ii  hunspell-en-us                             20070829-2ubuntu1                  English_american dictionary for hunspell
ii  ifupdown                                   0.6.8ubuntu19                      high level tools to configure network interfaces
ii  im-switch                                  1.16ubuntu1                        Input method switch framework
ii  imagemagick                                7:6.4.5.4.dfsg1-1ubuntu3           image manipulation programs
ii  imagemagick-doc                            7:6.4.5.4.dfsg1-1ubuntu3           document files of ImageMagick
ii  info                                       4.11.dfsg.1-4                      Standalone GNU Info documentation browser
ii  initramfs-tools                            0.92bubuntu29                      tools for generating an initramfs
ii  initscripts                                2.86.ds1-61ubuntu11                Scripts for initializing and shutting down the system
ii  inputattach                                1.23-0ubuntu2                      utility to attach serial devices to the input subsystem
ii  installation-report                        2.38ubuntu2                        system installation report
ii  iproute                                    20080725-2                         networking and traffic control tools
ii  iptables                                   1.4.1.1-4ubuntu3                   administration tools for packet filtering and NAT
ii  iputils-arping                             3:20071127-1                       Tool to send ICMP echo requests to an ARP address
ii  iputils-ping                               3:20071127-1                       Tools to test the reachability of network hosts
ii  iputils-tracepath                          3:20071127-1                       Tools to trace the network path to a remote host
ii  iso-codes                                  3.6-1                              ISO language, territory, currency, script codes and their transl
ii  jockey-common                              0.5-0ubuntu10                      user interface and desktop integration for driver management
ii  jockey-gtk                                 0.5-0ubuntu10                      GNOME user interface and desktop integration for driver manageme
ii  kbd                                        1.14.1-4ubuntu4                    Linux console font and keytable utilities
ii  klibc-utils                                1.5.14-1~exp1ubuntu2               small utilities built with klibc for early boot
ii  klogd                                      1.5-5ubuntu3                       Kernel Logging Daemon
ii  language-pack-en                           1:9.04+20090413                    translation updates for language English
ii  language-pack-en-base                      1:9.04+20090413                    translations for language English
ii  language-selector                          0.4.2.2                            Language selector for Ubuntu Linux
ii  language-selector-common                   0.4.2.2                            Language selector for Ubuntu Linux
ii  laptop-detect                              0.13.7ubuntu1                      attempt to detect a laptop
ii  laptop-mode-tools                          1.47-1ubuntu1                      Scripts to spin down hard drive and save power
ii  latex-xft-fonts                            0.1-8                              Xft-compatible versions of some LaTeX fonts
ii  launchpad-integration                      0.1.24                             launchpad integration
ii  less                                       418-1                              Pager program similar to more
ii  lftp                                       3.7.8-1                            Sophisticated command-line FTP/HTTP client programs
ii  libaa1                                     1.4p5-37build1                     ascii art library
ii  libacl1                                    2.2.47-2                           Access control list shared library
ii  libaiksaurus-1.2-0c2a                      1.2.1+dev-0.12-6                   an English-language thesaurus (development)
ii  libaiksaurus-1.2-data                      1.2.1+dev-0.12-6                   an English-language thesaurus (data)
ii  libaiksaurusgtk-1.2-0c2a                   1.2.1+dev-0.12-6                   graphical interface to the Aiksaurus toolkit (library)
ii  libapm1                                    3.2.2-12ubuntu3                    Library for interacting with APM driver in kernel
ii  libapparmor-perl                           2.3+1289-0ubuntu14                 AppArmor library Perl bindings
ii  libapparmor1                               2.3+1289-0ubuntu14                 changehat AppArmor library
ii  libarchive1                                2.4.17-2                           Single library to read/write tar, cpio, pax, zip, iso9660, etc.
ii  libart-2.0-2                               2.3.20-2                           Library of functions for 2D graphics - runtime files
ii  libasound2                                 1.0.18-1ubuntu9                    shared library for ALSA applications
ii  libaspell15                                0.60.6-1                           GNU Aspell spell-checker runtime library
ii  libatk1.0-0                                1.26.0-0ubuntu2                    The ATK accessibility toolkit
ii  libatk1.0-data                             1.26.0-0ubuntu2                    Common files for the ATK accessibility toolkit
ii  libatm1                                    2.4.1-17.2                         shared library for ATM (Asynchronous Transfer Mode)
ii  libattr1                                   1:2.4.43-1                         Extended attribute shared library
ii  libaudiofile0                              0.2.6-7ubuntu1                     Open-source version of SGI's audiofile library
ii  libavahi-client3                           0.6.23-4ubuntu4                    Avahi client library
ii  libavahi-common-data                       0.6.23-4ubuntu4                    Avahi common data files
ii  libavahi-common3                           0.6.23-4ubuntu4                    Avahi common library
ii  libavahi-compat-libdnssd1                  0.6.23-4ubuntu4                    Avahi Apple Bonjour compatibility library
ii  libavahi-core5                             0.6.23-4ubuntu4                    Avahi's embeddable mDNS/DNS-SD library
ii  libavahi-glib1                             0.6.23-4ubuntu4                    Avahi glib integration library
ii  libavahi-gobject0                          0.6.23-4ubuntu4                    Avahi GObject library
ii  libavahi-ui0                               0.6.23-4ubuntu4                    Avahi GTK+ User interface library
ii  libavc1394-0                               0.5.3-1build1                      control IEEE 1394 audio/video devices
ii  libbabl-0.0-0                              0.0.22-1                           Dynamic, any to any, pixel format conversion library
ii  libbeagle1                                 0.3.5-2build1                      library for accessing beagle using C
ii  libbind9-40                                1:9.5.1.dfsg.P2-1                  BIND9 Shared Library used by BIND
ii  libblkid1                                  1.41.4-1ubuntu1                    block device id library
ii  libbluetooth3                              4.32-0ubuntu4                      Library to use the BlueZ Linux Bluetooth stack
ii  libbonobo2-0                               2.24.1-1                           Bonobo CORBA interfaces library
ii  libbonobo2-common                          2.24.1-1                           Bonobo CORBA interfaces library -- support files
ii  libbonoboui2-0                             2.24.1-1ubuntu1                    The Bonobo UI library
ii  libbonoboui2-common                        2.24.1-1ubuntu1                    The Bonobo UI library -- common files
ii  libbrasero-media0                          2.26.0-0ubuntu3                    CD/DVD burning application for GNOME - runtime libraries
ii  libbz2-1.0                                 1.0.5-1ubuntu1                     high-quality block-sorting file compressor library - runtime
ii  libc6                                      2.9-4ubuntu6                       GNU C Library: Shared libraries
ii  libc6-dev                                  2.9-4ubuntu6                       GNU C Library: Development Libraries and Header Files
ii  libc6-i686                                 2.9-4ubuntu6                       GNU C Library: Shared libraries [i686 optimized]
ii  libcaca0                                   0.99.beta16-1                      colour ASCII art library
ii  libcairo-perl                              1.060-1                            Perl interface to the Cairo graphics library
ii  libcairo2                                  1.8.6-1ubuntu2                     The Cairo 2D vector graphics library
ii  libcairomm-1.0-1                           1.6.4-1                            C++ wrappers for Cairo (shared libraries)
ii  libcamel1.2-14                             2.26.1-0ubuntu1                    The Evolution MIME message handling library
ii  libcanberra-gtk-module                     0.11-1ubuntu5                      translates Gtk+ widgets signals to event sounds
ii  libcanberra-gtk0                           0.11-1ubuntu5                      Gtk+ helper for playing widget event sounds with libcanberra
ii  libcanberra0                               0.11-1ubuntu5                      a simple abstract interface for playing event sounds
ii  libcap2                                    2.11-2                             support for getting/setting POSIX.1e capabilities
ii  libcdio-cdda0                              0.78.2+dfsg1-3                     library to read and control digital audio CDs
ii  libcdio-paranoia0                          0.78.2+dfsg1-3                     library to read digital audio CDs with error correction
ii  libcdio7                                   0.78.2+dfsg1-3                     library to read and control CD-ROM
ii  libcdparanoia0                             3.10.2+debian-5                    audio extraction tool for sampling CDs (library)
ii  libck-connector0                           0.3.0-2ubuntu3                     ConsoleKit libraries
ii  libclass-accessor-perl                     0.31-2                             Automated accessor generator
ii  libcomerr2                                 1.41.4-1ubuntu1                    common error description library
ii  libcompress-raw-zlib-perl                  2.015-1                            low-level interface to zlib compression library
ii  libcompress-zlib-perl                      2.015-1                            Perl module for creation and manipulation of gzip files
ii  libcroco3                                  0.6.1-2                            a generic Cascading Style Sheet (CSS) parsing and manipulation t
ii  libcryptui0                                2.26.1-0ubuntu1                    the UI library for DBUS functions exported by seahorse
ii  libcups2                                   1.3.9-17ubuntu1                    Common UNIX Printing System(tm) - libs
ii  libcupsimage2                              1.3.9-17ubuntu1                    Common UNIX Printing System(tm) - image libs
ii  libcurl3-gnutls                            7.18.2-8ubuntu4                    Multi-protocol file transfer library (GnuTLS)
ii  libcwidget3                                0.5.12-4ubuntu1                    high-level terminal interface library for C++ (runtime files)
ii  libdaemon0                                 0.13-2                             lightweight C library for daemons - runtime library
ii  libdatrie0                                 0.1.3-2                            Double-array trie library
ii  libdb4.6                                   4.6.21-12                          Berkeley v4.6 Database Libraries [runtime]
ii  libdb4.7                                   4.7.25-6ubuntu1                    Berkeley v4.7 Database Libraries [runtime]
ii  libdbus-1-3                                1.2.12-0ubuntu2                    simple interprocess messaging system
ii  libdbus-glib-1-2                           0.80-3                             simple interprocess messaging system (GLib-based shared library)
ii  libdevmapper1.02.1                         2:1.02.27-4ubuntu5                 The Linux Kernel Device Mapper userspace library
ii  libdirectfb-1.0-0                          1.0.1-11ubuntu1                    direct frame buffer graphics - shared libraries
ii  libdiscid0                                 0.1.0-1                            Library for creating MusicBrainz DiscIDs
ii  libdjvulibre-text                          3.5.21-3ubuntu1                    Linguistic support files for libdjvulibre
ii  libdjvulibre21                             3.5.21-3ubuntu1                    Runtime support for the DjVu image format
ii  libdmx1                                    1:1.0.2-3                          X11 Distributed Multihead extension library
ii  libdns45                                   1:9.5.1.dfsg.P2-1                  DNS Shared Library used by BIND
ii  libdrm-intel1                              2.4.5-0ubuntu4                     Userspace interface to intel-specific kernel DRM services -- run
ii  libdrm2                                    2.4.5-0ubuntu4                     Userspace interface to kernel DRM services -- runtime
ii  libdv4                                     1.0.0-1ubuntu2                     software library for DV format digital video (runtime lib)
ii  libebook1.2-9                              2.26.1-0ubuntu1                    Client library for evolution address books
ii  libecal1.2-7                               2.26.1-0ubuntu1                    Client library for evolution calendars
ii  libedataserver1.2-11                       2.26.1-0ubuntu1                    Utility library for evolution data servers
ii  libedit2                                   2.11~20080614-1ubuntu1             BSD editline and history libraries
ii  libelf1                                    0.131-4                            library to read and write ELF files
ii  libenchant1c2a                             1.4.2-3.3ubuntu1                   a wrapper library for various spell checker engines
ii  libept0                                    0.5.26build1                       High-level library for managing Debian package information
ii  libesd-alsa0                               0.2.40-0ubuntu3                    Enlightened Sound Daemon (ALSA) - Shared libraries
ii  libevdocument1                             2.26.0-0ubuntu1                    GNOME document viewer backend library
ii  libevview1                                 2.26.0-0ubuntu1                    GNOME document viewer view library
ii  libexif12                                  0.6.16-2.1ubuntu1                  library to parse EXIF files
ii  libexo-0.3-0                               0.3.100-1ubuntu1                   Library with extensions for Xfce
ii  libexpat1                                  2.0.1-4                            XML parsing C library - runtime library
ii  libffi5                                    3.0.7-1ubuntu1                     Foreign Function Interface library runtime
ii  libfftw3-3                                 3.1.2-3.1ubuntu1                   library for computing Fast Fourier Transforms
ii  libflac8                                   1.2.1-1.2                          Free Lossless Audio Codec - runtime C library
ii  libfont-afm-perl                           1.20-1                             Font::AFM - Interface to Adobe Font Metrics files
ii  libfontconfig1                             2.6.0-1ubuntu12                    generic font configuration library - runtime
ii  libfontenc1                                1:1.0.4-3                          X11 font encoding library
ii  libfreetype6                               2.3.9-4build1                      FreeType 2 font engine, shared library files
ii  libfreezethaw-perl                         0.43-4                             converting Perl structures to strings and back
ii  libfribidi0                                0.10.9-1                           Free Implementation of the Unicode BiDi algorithm
ii  libfs6                                     2:1.0.1-1                          X11 Font Services library
ii  libfuse2                                   2.7.4-1.1ubuntu4                   Filesystem in USErspace library
ii  libgadu3                                   1:1.8.0+r592-3                     Gadu-Gadu protocol library - runtime files
ii  libgail-common                             2.16.1-0ubuntu2                    GNOME Accessibility Implementation Library -- common modules
ii  libgail18                                  2.16.1-0ubuntu2                    GNOME Accessibility Implementation Library -- shared libraries
ii  libgamin0                                  0.1.9-2ubuntu4                     Client library for the gamin file and directory monitoring syste
ii  libgc1c2                                   1:6.8-1.2                          conservative garbage collector for C and C++
ii  libgcc1                                    1:4.3.3-5ubuntu4                   GCC support library
ii  libgconf2-4                                2.26.0-0ubuntu1                    GNOME configuration database system (shared libraries)
ii  libgcr0                                    2.26.1-0ubuntu1                    Library for Crypto UI related task - runtime
ii  libgcrypt11                                1.4.1-2ubuntu1                     LGPL Crypto library - runtime library
ii  libgd2-noxpm                               2.0.36~rc1~dfsg-3ubuntu1           GD Graphics Library version 2 (without XPM support)
ii  libgda3-3                                  3.0.2-5ubuntu1                     GNOME Data Access library for GNOME2
ii  libgda3-bin                                3.0.2-5ubuntu1                     Binary files for GNOME Data Access library for GNOME2
ii  libgda3-common                             3.0.2-5ubuntu1                     Common files for GNOME Data Access library for GNOME2
ii  libgdbm3                                   1.8.3-4                            GNU dbm database routines (runtime version)
ii  libgdl-1-0                                 2.26.0-0ubuntu1                    GNOME DevTool libraries
ii  libgdl-1-common                            2.26.0-0ubuntu1                    GNOME DevTool libraries - common files
ii  libgdome2-0                                0.8.1+debian-3                     DOM level2 library for accessing XML files
ii  libgdome2-cpp-smart0c2a                    0.2.6-2                            C++ bindings for GDome2 DOM implementation
ii  libgegl-0.0-0                              0.0.22-0ubuntu3                    Generic Graphics Library
ii  libggz2                                    0.0.14.1-1build1                   GGZ Gaming Zone: common utilities library
ii  libggzcore9                                0.0.14.1-1ubuntu1                  GGZ Gaming Zone: core client frontend library
ii  libggzmod4                                 0.0.14.1-1ubuntu1                  GGZ Gaming Zone: game frontend library
ii  libgimp2.0                                 2.6.6-0ubuntu1                     Libraries for the GNU Image Manipulation Program
ii  libgksu2-0                                 2.0.9-1ubuntu3                     library providing su and sudo functionality
ii  libgl1-mesa-dri                            7.4-0ubuntu3                       A free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx                            7.4-0ubuntu3                       A free implementation of the OpenGL API -- GLX runtime
ii  libglade2-0                                1:2.6.4-1                          library to load .glade files at runtime
ii  libglew1.5                                 1.5.0dfsg1-3ubuntu1                The OpenGL Extension Wrangler - runtime environment
ii  libglib-perl                               1:1.190-2                          Perl interface to the GLib and GObject libraries
ii  libglib2.0-0                               2.20.1-0ubuntu2                    The GLib library of C routines
ii  libglib2.0-data                            2.20.1-0ubuntu2                    Common files for GLib library
ii  libglibmm-2.4-1c2a                         2.20.0-0ubuntu2                    C++ wrapper for the GLib toolkit (shared libraries)
ii  libglu1-mesa                               7.4-0ubuntu3                       The OpenGL utility library (GLU)
ii  libgmp3c2                                  2:4.2.4+dfsg-2ubuntu1              Multiprecision arithmetic library
ii  libgnome-desktop-2-11                      1:2.26.1-0ubuntu1                  Utility library for loading .desktop files - runtime files
ii  libgnome-keyring0                          2.26.1-0ubuntu1                    GNOME keyring services library
ii  libgnome-media0                            2.26.0-0ubuntu3                    runtime libraries for the GNOME media utilities
ii  libgnome-menu2                             2.26.0-0ubuntu1                    an implementation of the freedesktop menu specification for GNOM
ii  libgnome2-0                                2.26.0-0ubuntu2                    The GNOME 2 library - runtime files
ii  libgnome2-canvas-perl                      1.002-1+b1ubuntu3                  Perl interface to the GNOME canvas library
ii  libgnome2-common                           2.26.0-0ubuntu2                    The GNOME 2 library - common files
ii  libgnome2-perl                             1.042-1build2                      Perl interface to the GNOME libraries
ii  libgnome2-vfs-perl                         1.080-1build2                      Perl interface to the 2.x series of the GNOME VFS library
ii  libgnomecanvas2-0                          2.26.0-0ubuntu1                    A powerful object-oriented display - runtime files
ii  libgnomecanvas2-common                     2.26.0-0ubuntu1                    A powerful object-oriented display - common files
ii  libgnomecups1.0-1                          0.2.3-3                            GNOME library for CUPS interaction
ii  libgnomekbd-common                         2.26.0-0ubuntu2                    GNOME library to manage keyboard configuration - common files
ii  libgnomekbd3                               2.26.0-0ubuntu2                    GNOME library to manage keyboard configuration - shared library
ii  libgnomekbdui3                             2.26.0-0ubuntu2                    User interface library for libgnomekbd - shared library
ii  libgnomeprint2.2-0                         2.18.6-1                           The GNOME 2.2 print architecture - runtime files
ii  libgnomeprint2.2-data                      2.18.6-1                           The GNOME 2.2 print architecture - data files
ii  libgnomeprintui2.2-0                       2.18.4-1                           GNOME 2.2 print architecture User Interface - runtime files
ii  libgnomeprintui2.2-common                  2.18.4-1                           GNOME 2.2 print architecture User Interface - common files
ii  libgnomeui-0                               2.24.1-1                           The GNOME 2 libraries (User Interface) - runtime files
ii  libgnomeui-common                          2.24.1-1                           The GNOME 2 libraries (User Interface) - common files
ii  libgnomevfs2-0                             1:2.24.1-0ubuntu1                  GNOME Virtual File System (runtime libraries)
ii  libgnomevfs2-common                        1:2.24.1-0ubuntu1                  GNOME Virtual File System (common files)
ii  libgnomevfs2-extra                         1:2.24.1-0ubuntu1                  GNOME Virtual File System (extra modules)
ii  libgnutls26                                2.4.2-6                            the GNU TLS library - runtime library
ii  libgoffice-0-6                             0.6.6-1ubuntu1                     Document centric objects library - runtime files
ii  libgoffice-0-6-common                      0.6.6-1ubuntu1                     Document centric objects library - common files
ii  libgoffice-gtk-0-6                         0.6.6-1ubuntu1                     Document centric objects library - Transitional package
ii  libgomp1                                   4.3.3-5ubuntu4                     GCC OpenMP (GOMP) support library
ii  libgp11-0                                  2.26.1-0ubuntu1                    Glib wrapper library for PKCS#11 - runtime
ii  libgpg-error0                              1.4-2ubuntu7                       library for common error values and messages in GnuPG components
ii  libgpgme11                                 1.1.8-2ubuntu3                     GPGME - GnuPG Made Easy
ii  libgphoto2-2                               2.4.2-0ubuntu4                     gphoto2 digital camera library
ii  libgphoto2-port0                           2.4.2-0ubuntu4                     gphoto2 digital camera port library
ii  libgpm2                                    1.20.4-3.1ubuntu1                  General Purpose Mouse - shared library
ii  libgraphviz4                               2.20.2-3ubuntu2                    rich set of graph drawing tools
ii  libgs8                                     8.64.dfsg.1-0ubuntu8               The Ghostscript PostScript/PDF interpreter Library
ii  libgsf-1-114                               1.14.11-2ubuntu1                   Structured File Library - runtime version
ii  libgsf-1-common                            1.14.11-2ubuntu1                   Structured File Library - common files
ii  libgsf-gnome-1-114                         1.14.11-2ubuntu1                   Structured File Library - runtime version for GNOME
ii  libgsl0ldbl                                1.12+dfsg-1                        GNU Scientific Library (GSL) -- library package
ii  libgstreamer-plugins-base0.10-0            0.10.22-5                          GStreamer libraries from the "base" set
ii  libgstreamer0.10-0                         0.10.22-1                          Core GStreamer libraries and elements
ii  libgtk-vnc-1.0-0                           0.3.8-2ubuntu2                     A VNC viewer widget for GTK+ (runtime libraries)
ii  libgtk2-perl                               1:1.190-1ubuntu1                   Perl interface to the 2.x series of the Gimp Toolkit library
ii  libgtk2.0-0                                2.16.1-0ubuntu2                    The GTK+ graphical user interface library
ii  libgtk2.0-bin                              2.16.1-0ubuntu2                    The programs for the GTK+ graphical user interface library
ii  libgtk2.0-common                           2.16.1-0ubuntu2                    Common files for the GTK+ graphical user interface library
ii  libgtkhtml2-0                              2.11.1-2ubuntu1                    HTML rendering/editing library - runtime files
ii  libgtkmathview0c2a                         0.8.0-3                            rendering engine for MathML documents
ii  libgtkmm-2.4-1c2a                          1:2.16.0-1                         C++ wrappers for GTK+ 2.4 (shared libraries)
ii  libgtksourceview-common                    1.8.5-2                            common files for the GTK+ syntax highlighting widget
ii  libgtksourceview1.0-0                      1.8.5-2                            shared libraries for the GTK+ syntax highlighting widget
ii  libgtksourceview2.0-0                      2.6.1-0ubuntu1                     shared libraries for the GTK+ syntax highlighting widget
ii  libgtksourceview2.0-common                 2.6.1-0ubuntu1                     common files for the GTK+ syntax highlighting widget
ii  libgtkspell0                               2.0.13-2                           a spell-checking addon for GTK's TextView widget
ii  libgtop2-7                                 2.26.0-0ubuntu2                    gtop system monitoring library
ii  libgtop2-common                            2.26.0-0ubuntu2                    common files for the gtop system monitoring library
ii  libgucharmap7                              1:2.26.1-0ubuntu1                  Unicode browser widget library (shared library)
ii  libgutenprint2                             5.2.3-0ubuntu5                     runtime for the Gutenprint printer driver library
ii  libgvfscommon0                             1.2.2-0ubuntu1                     userspace virtual filesystem - library
ii  libgweather-common                         2.26.1-0ubuntu1                    GWeather common files
ii  libgweather1                               2.26.1-0ubuntu1                    GWeather shared library
ii  libhal-storage1                            0.5.12~rc1+git20090403-0ubuntu1    Hardware Abstraction Layer - shared library for storage devices
ii  libhal1                                    0.5.12~rc1+git20090403-0ubuntu1    Hardware Abstraction Layer - shared library
ii  libhesiod0                                 3.0.2-19build1                     Project Athena's DNS-based directory service - libraries
ii  libhtml-format-perl                        2.04-2                             format HTML syntax trees into text, PostScript or RTF
ii  libhtml-parser-perl                        3.59-1ubuntu1                      A collection of modules that parse HTML text documents
ii  libhtml-tagset-perl                        3.20-2                             Data tables pertaining to HTML
ii  libhtml-tree-perl                          3.23-1                             represent and create HTML syntax trees
ii  libhunspell-1.2-0                          1.2.6-1ubuntu2                     spell checker and morphological analyzer (shared library)
ii  libical0                                   0.43-2                             iCalendar library implementation in C (runtime)
ii  libice6                                    2:1.0.4-1                          X11 Inter-Client Exchange library
ii  libidl0                                    0.8.13-0.1                         library for parsing CORBA IDL files
ii  libidn11                                   1.10-3                             GNU libidn library, implementation of IETF IDN specifications
ii  libiec61883-0                              1.1.0-2ubuntu2                     an partial implementation of IEC 61883
ii  libieee1284-3                              0.2.11-5ubuntu1                    cross-platform library for parallel port access
ii  libijs-0.35                                0.35-6                             IJS raster image transport protocol: shared library
ii  libilmbase6                                1.0.1-2+nmu2                       several utility libraries from ILM used by OpenEXR
ii  libio-compress-base-perl                   2.015-1                            Base Class for IO::Compress modules
ii  libio-compress-zlib-perl                   2.015-1                            Perl interface to zlib
ii  libio-string-perl                          1.08-2                             Emulate IO::File interface for in-core strings
ii  libisc45                                   1:9.5.1.dfsg.P2-1                  ISC Shared Library used by BIND
ii  libisccc40                                 1:9.5.1.dfsg.P2-1                  Command Channel Library used by BIND
ii  libisccfg40                                1:9.5.1.dfsg.P2-1                  Config File Handling Library used by BIND
ii  libiw29                                    29-1.1ubuntu2                      Wireless tools - library
ii  libjasper1                                 1.900.1-5.1                        The JasPer JPEG-2000 runtime library
ii  libjpeg62                                  6b-14                              The Independent JPEG Group's JPEG runtime library
ii  libkeyutils1                               1.2-9                              Linux Key Management Utilities (library)
ii  libklibc                                   1.5.14-1~exp1ubuntu2               minimal libc subset for use with initramfs
ii  libkpathsea4                               2007.dfsg.2-4ubuntu2               TeX Live: path search library for TeX (runtime part)
ii  libkrb53                                   1.6.dfsg.4~beta1-5ubuntu2          MIT Kerberos runtime libraries
ii  liblaunchpad-integration1                  0.1.24                             library for launchpad integration
ii  liblcms1                                   1.18.dfsg-0ubuntu1                 Color management library
ii  libldap-2.4-2                              2.4.15-1ubuntu3                    OpenLDAP libraries
ii  liblink-grammar4                           4.3.9-2                            Carnegie Mellon University's link grammar parser for English
ii  liblircclient0                             0.8.4a-0ubuntu5                    infra-red remote control support - client library
ii  liblocale-gettext-perl                     1.05-4build1                       Using libc functions for internationalization in Perl
ii  liblockfile1                               1.08-3                             NFS-safe locking library, includes dotlockfile program
ii  libloudmouth1-0                            1.4.2-2                            Lightweight C Jabber library
ii  libltdl7                                   2.2.6a-1ubuntu1                    A system independent dlopen wrapper for GNU libtool
ii  liblwres40                                 1:9.5.1.dfsg.P2-1                  Lightweight Resolver Library used by BIND
ii  libmad0                                    0.15.1b-4                          MPEG audio decoder library
ii  libmagic1                                  4.26-2ubuntu3                      File type determination library using "magic" numbers
ii  libmagickcore1                             7:6.4.5.4.dfsg1-1ubuntu3           low-level image manipulation library
ii  libmagickwand1                             7:6.4.5.4.dfsg1-1ubuntu3           image manipulation library
ii  libmailtools-perl                          2.04-1                             Manipulate email in perl programs
ii  libmbca0                                   0.0.4+bzr66-0ubuntu1               Mobile Broadband Configuration Assistant
ii  libmeanwhile1                              1.0.2-3                            open implementation of the Lotus Sametime Community Client proto
ii  libmetacity0                               1:2.25.144-0ubuntu2                library of lightweight GTK2 based Window Manager
ii  libmldbm-perl                              2.01-2                             Store multidimensional hash structures in perl tied hashes
ii  libmng1                                    1.0.9-1                            Multiple-image Network Graphics library
ii  libmpcdec3                                 1.2.2-1build1                      Musepack (MPC) format library
ii  libmpfr1ldbl                               2.4.0-1ubuntu3                     multiple precision floating-point computation
ii  libmusicbrainz4c2a                         2.1.5-2ubuntu1                     Second generation incarnation of the CD Index - library
ii  libnautilus-burn4                          2.25.3-0ubuntu1                    Nautilus Burn Library - runtime version
ii  libnautilus-extension1                     1:2.26.2-0ubuntu1                  libraries for nautilus components - runtime version
ii  libncurses5                                5.7+20090207-1ubuntu1              shared libraries for terminal handling
ii  libncursesw5                               5.7+20090207-1ubuntu1              shared libraries for terminal handling (wide character support)
ii  libnet-dbus-perl                           0.33.6-1build2                     Extension for the DBus bindings
ii  libnewt0.52                                0.52.2-11.3ubuntu3                 Not Erik's Windowing Toolkit - text mode windowing with slang
ii  libnl1                                     1.1-3                              library for dealing with netlink sockets
ii  libnm-glib0                                0.7.1~rc4.1.cf199a964-0ubuntu2     network management framework (GLib shared library)
ii  libnm-util1                                0.7.1~rc4.1.cf199a964-0ubuntu2     network management framework (shared library)
ii  libnotify-bin                              0.4.5-0ubuntu1                     sends desktop notifications to a notification daemon
ii  libnotify1                                 0.4.5-0ubuntu1                     sends desktop notifications to a notification daemon
ii  libnspr4-0d                                4.7.3-0ubuntu2                     NetScape Portable Runtime Library
ii  libnss-mdns                                0.10-3ubuntu2                      NSS module for Multicast DNS name resolution
ii  libnss3-1d                                 3.12.2~rc1-0ubuntu2                Network Security Service libraries
ii  libntfs-3g49                               1:2009.2.1-0ubuntu2                ntfs-3g filesystem in userspace (FUSE) library
ii  libofa0                                    0.9.3-3                            Library for acoustic fingerprinting
ii  libogg0                                    1.1.3-4build1                      Ogg Bitstream Library
ii  liboil0.3                                  0.3.15-1ubuntu3                    Library of Optimized Inner Loops
ii  liboobs-1-4                                2.22.0-2ubuntu1                    GObject based interface to system-tools-backends - shared librar
ii  libopenexr6                                1.6.1-3ubuntu1                     runtime files for the OpenEXR image library
ii  libopenobex1                               1.5-1                              OBEX protocol library
ii  liborbit2                                  1:2.14.17-0.1                      libraries for ORBit2 - a CORBA ORB
ii  libotr2                                    3.2.0-1                            Off-the-Record Messaging library
ii  libots0                                    0.5.0-2                            Open Text Summarizer (library)
ii  libpam-ck-connector                        0.3.0-2ubuntu3                     ConsoleKit PAM module
ii  libpam-gnome-keyring                       2.26.1-0ubuntu1                    PAM module to unlock the GNOME keyring upon login
ii  libpam-modules                             1.0.1-9ubuntu1                     Pluggable Authentication Modules for PAM
ii  libpam-runtime                             1.0.1-9ubuntu1                     Runtime support for the PAM library
ii  libpam0g                                   1.0.1-9ubuntu1                     Pluggable Authentication Modules library
ii  libpanel-applet2-0                         1:2.26.0-0ubuntu7                  library for GNOME Panel applets
ii  libpango1.0-0                              1.24.1-0ubuntu1                    Layout and rendering of internationalized text
ii  libpango1.0-common                         1.24.1-0ubuntu1                    Modules and configuration files for the Pango
ii  libpangomm-1.4-1                           2.24.0-1                           C++ Wrapper for pango (shared libraries)
ii  libpaper-utils                             1.1.23+nmu1                        library for handling paper characteristics (utilities)
ii  libpaper1                                  1.1.23+nmu1                        library for handling paper characteristics
ii  libparse-debianchangelog-perl              1.1.1-2ubuntu1                     parse Debian changelogs and output them in other formats
ii  libparted1.8-10                            1.8.8.git.2008.03.24-11.1ubuntu6   The GNU Parted disk partitioning shared library
ii  libpcap0.8                                 1.0.0-1                            system interface for user-level packet capture
ii  libpci3                                    1:3.0.0-4ubuntu8                   Linux PCI Utilities (shared library)
ii  libpciaccess0                              0.10.5-1                           Generic PCI access library for X
ii  libpcre3                                   7.8-2ubuntu1                       Perl 5 Compatible Regular Expression Library - runtime files
ii  libpcsclite1                               1.4.102-1ubuntu2                   Middleware to access a smart card using PC/SC (library)
ii  libperl5.10                                5.10.0-19ubuntu1                   Shared Perl library
ii  libpixman-1-0                              0.13.2-1                           pixel-manipulation library for X and cairo
ii  libpng12-0                                 1.2.27-2ubuntu2                    PNG library - runtime
ii  libpolkit-dbus2                            0.9-2ubuntu1                       library for accessing PolicyKit via D-Bus
ii  libpolkit-gnome0                           0.9-1ubuntu3                       PolicyKit-gnome library
ii  libpolkit-grant2                           0.9-2ubuntu1                       library for obtaining privileges via PolicyKit
ii  libpolkit2                                 0.9-2ubuntu1                       library for accessing PolicyKit
ii  libpoppler-glib4                           0.10.5-1ubuntu2                    PDF rendering library (GLib-based shared library)
ii  libpoppler4                                0.10.5-1ubuntu2                    PDF rendering library
ii  libpopt0                                   1.14-4                             lib for parsing cmdline parameters
ii  libproxy0                                  0.2.3-0ubuntu5                     automatic proxy configuration management library (shared)
ii  libpth20                                   2.0.7-12                           The GNU Portable Threads
ii  libpurple-bin                              1:2.5.5-1ubuntu8                   multi-protocol instant messaging library - extra utilities
ii  libpurple0                                 1:2.5.5-1ubuntu8                   multi-protocol instant messaging library
ii  libpython2.6                               2.6.2-0ubuntu1                     Shared Python runtime library (version 2.6)
ii  librarian0                                 0.8.1-1ubuntu2                     Rarian is a documentation meta-data library (library package)
ii  libraw1394-8                               1.3.0-4ubuntu1                     library for direct access to IEEE 1394 bus (aka FireWire)
ii  libreadline5                               5.2-4                              GNU readline and history libraries, run-time libraries
ii  librecode0                                 3.6-15                             Shared library on which recode is based
ii  librpc-xml-perl                            0.64-1                             Perl module implementation of XML-RPC
ii  librsvg2-2                                 2.26.0-0ubuntu1                    SAX-based renderer library for SVG files (runtime)
ii  librsvg2-common                            2.26.0-0ubuntu1                    SAX-based renderer library for SVG files (extra runtime)
ii  libsane                                    1.0.19-23ubuntu7                   API library for scanners
ii  libsasl2-2                                 2.1.22.dfsg1-23ubuntu3             Cyrus SASL - authentication abstraction library
ii  libsasl2-modules                           2.1.22.dfsg1-23ubuntu3             Cyrus SASL - pluggable authentication modules
ii  libscim8c2a                                1.4.7-3ubuntu12                    library for SCIM platform
ii  libsdl1.2debian                            1.2.13-4ubuntu3                    Simple DirectMedia Layer
ii  libsdl1.2debian-alsa                       1.2.13-4ubuntu3                    Simple DirectMedia Layer (with X11 and ALSA options)
ii  libselinux1                                2.0.65-5build1                     SELinux shared libraries
ii  libsensors3                                1:2.10.7-1                         library to read temperature/voltage/fan sensors
ii  libsepol1                                  2.0.30-2ubuntu1                    Security Enhanced Linux policy library for changing policy binar
ii  libsexy2                                   0.1.11-2                           collection of additional GTK+ widgets - library
ii  libshout3                                  2.2.2-5                            MP3/Ogg Vorbis broadcast streaming library
ii  libsigc++-2.0-0c2a                         2.0.18-2                           type-safe Signal Framework for C++ - runtime
ii  libsilc-1.1-2                              1.1.7-2ubuntu1                     SILC library (silc-toolkit)
ii  libslang2                                  2.1.3-3ubuntu3                     The S-Lang programming library - runtime version
ii  libslp1                                    1.2.1-7.5                          OpenSLP libraries
ii  libsm6                                     2:1.1.0-1                          X11 Session Management library
ii  libsmbclient                               2:3.3.2-1ubuntu3                   shared library for communication with SMB/CIFS servers
ii  libsmbios2                                 2.2.13-0ubuntu2                    Provide access to (SM)BIOS information -- dynamic library
ii  libsnmp-base                               5.4.1~dfsg-12ubuntu3               SNMP (Simple Network Management Protocol) MIBs and documentation
ii  libsnmp15                                  5.4.1~dfsg-12ubuntu3               SNMP (Simple Network Management Protocol) library
ii  libsoup-gnome2.4-1                         2.26.0-0ubuntu2                    an HTTP library implementation in C -- Shared library
ii  libsoup2.4-1                               2.26.0-0ubuntu2                    an HTTP library implementation in C -- Shared library
ii  libspectre1                                0.2.2.ds-1                         Library for rendering Postscript documents
ii  libspeex1                                  1.2~rc1-1                          The Speex codec runtime library
ii  libsqlite3-0                               3.6.10-1                           SQLite 3 shared library
ii  libss2                                     1.41.4-1ubuntu1                    command-line interface parsing library
ii  libssl0.9.8                                0.9.8g-15ubuntu3                   SSL shared libraries
ii  libstartup-notification0                   0.9-1                              library for program launch feedback (shared library)
ii  libstdc++6                                 4.3.3-5ubuntu4                     The GNU Standard C++ Library v3
ii  libsysfs2                                  2.1.0-5                            interface library to sysfs
ii  libt1-5                                    5.1.2-3                            Type 1 font rasterizer library - runtime
ii  libtag1c2a                                 1.5-3                              TagLib Audio Meta-Data Library
ii  libtagc0                                   1.5-3                              TagLib Audio Meta-Data Library (C bindings)
ii  libtalloc1                                 1.2.0~git20080616-1                hierarchical pool based memory allocator
ii  libtasn1-3                                 1.5-1                              Manage ASN.1 structures (runtime)
ii  libtdb1                                    1.1.3~git20081222-2build1          Trivial Database - shared library
ii  libterm-readkey-perl                       2.30-4                             A perl module for simple terminal control
ii  libtext-charwidth-perl                     0.04-5build1                       get display widths of characters on the terminal
ii  libtext-iconv-perl                         1.7-1build1                        converts between character sets in Perl
ii  libtext-wrapi18n-perl                      0.06-6                             internationalized substitute of Text::Wrap
ii  libthai-data                               0.1.9-4                            Data files for Thai language support library
ii  libthai0                                   0.1.9-4                            Thai language support library
ii  libtheora0                                 1.0-2                              The Theora Video Compression Codec
ii  libthunar-vfs-1-2                          1.0.0-1ubuntu3                     VFS abstraction used in thunar
ii  libtie-ixhash-perl                         1.21-2                             ordered associative arrays for Perl
ii  libtiff4                                   3.8.2-11                           Tag Image File Format (TIFF) library
ii  libtimedate-perl                           1.1600-9                           Time and date functions for Perl
ii  libtotem-plparser12                        2.26.1-0ubuntu1                    Totem Playlist Parser library - runtime version
ii  libtrackerclient0                          0.6.93-0ubuntu1                    metadata database, indexer and search tool - library
ii  libts-0.0-0                                1.0-4ubuntu2                       touch screen library
ii  libtunepimp5                               0.5.3-7ubuntu3                     MusicBrainz tagging library
ii  libudev0                                   141-1                              udev library
ii  liburi-perl                                1.37+dfsg-1ubuntu1                 Manipulates and accesses URI strings
ii  libusb-0.1-4                               2:0.1.12-13                        userspace USB programming library
ii  libusplash0                                0.5.31                             userspace bootsplash library
ii  libuuid-perl                               0.02-3build1                       Perl extension for using UUID interfaces as defined in e2fsprogs
ii  libuuid1                                   1.41.4-1ubuntu1                    universally unique id library
ii  libv4l-0                                   0.5.8-1                            Collection of video4linux support libraries
ii  libvisual-0.4-0                            0.4.0-2.1+build1                   Audio visualization framework
ii  libvisual-0.4-plugins                      0.4.0.dfsg.1-2ubuntu4              Audio visualization framework plugins
ii  libvolume-id1                              141-1                              volume identification library
ii  libvorbis0a                                1.2.0.dfsg-3.1                     The Vorbis General Audio Compression Codec
ii  libvorbisenc2                              1.2.0.dfsg-3.1                     The Vorbis General Audio Compression Codec
ii  libvorbisfile3                             1.2.0.dfsg-3.1                     The Vorbis General Audio Compression Codec
ii  libvte-common                              1:0.20.0-0ubuntu2                  Terminal emulator widget for GTK+ 2.0 - common files
ii  libvte9                                    1:0.20.0-0ubuntu2                  Terminal emulator widget for GTK+ 2.0 - runtime files
ii  libwavpack1                                4.50.1-1                           an audio codec (lossy and lossless) - library
ii  libwbclient0                               2:3.3.2-1ubuntu3                   Samba winbind client library
ii  libwmf0.2-7                                0.2.8.4-6ubuntu1                   Windows metafile conversion library
ii  libwnck-common                             2.26.0-0ubuntu1                    Window Navigator Construction Kit - common files
ii  libwnck22                                  2.26.0-0ubuntu1                    Window Navigator Construction Kit - runtime files
ii  libwpd8c2a                                 0.8.14-1                           Library for handling WordPerfect documents (shared library)
ii  libwpg-0.1-1                               0.1.3-1                            WordPerfect graphics import/convert library (shared library)
ii  libwrap0                                   7.6.q-16                           Wietse Venema's TCP wrappers library
ii  libwv-1.2-3                                1.2.4-2ubuntu2                     Library for accessing Microsoft Word documents
ii  libwww-perl                                5.820-1                            WWW client/server library for Perl (aka LWP)
ii  libx11-6                                   2:1.1.99.2-1ubuntu2                X11 client-side library
ii  libx11-data                                2:1.1.99.2-1ubuntu2                X11 client-side library
ii  libx86-1                                   1.1+ds1-2                          x86 real-mode library
ii  libxapian15                                1.0.7-4                            Search engine library
ii  libxau6                                    1:1.0.4-1                          X11 authorisation library
ii  libxaw7                                    2:1.0.5-1                          X11 Athena Widget library
ii  libxcb-render-util0                        0.2.1+git1-1                       utility libraries for X C Binding -- render-util
ii  libxcb-render0                             1.1.93-0ubuntu3                    X C Binding, render extension
ii  libxcb1                                    1.1.93-0ubuntu3                    X C Binding
ii  libxcomposite1                             1:0.4.0-3                          X11 Composite extension library
ii  libxcursor1                                1:1.1.9-1                          X cursor management library
ii  libxdamage1                                1:1.1.1-4                          X11 damaged region extension library
ii  libxdmcp6                                  1:1.0.2-3                          X11 Display Manager Control Protocol library
ii  libxext6                                   2:1.0.99.1-0ubuntu3                X11 miscellaneous extension library
ii  libxfce4menu-0.1-0                         4.6.0-1~ubuntu1                    freedesktop.org compliant menu implementation for Xfce
ii  libxfce4util4                              4.6.0-1ubuntu2                     Utility functions library for Xfce4
ii  libxfcegui4-4                              4.6.0-1~ubuntu1                    Basic GUI C functions for Xfce4
ii  libxfconf-0-2                              4.6.0-1~ubuntu1                    Client library for Xfce4 configure interface
ii  libxfixes3                                 1:4.0.3-2                          X11 miscellaneous 'fixes' extension library
ii  libxfont1                                  1:1.3.3-1ubuntu1                   X11 font rasterisation library
ii  libxft2                                    2.1.13-3ubuntu1                    FreeType-based font drawing library for X
ii  libxi6                                     2:1.2.0-1ubuntu1                   X11 Input extension library
ii  libxinerama1                               2:1.0.3-2                          X11 Xinerama extension library
ii  libxkbfile1                                1:1.0.5-1ubuntu2                   X11 keyboard file manipulation library
ii  libxklavier12                              3.9-0ubuntu1                       X Keyboard Extension high-level API
ii  libxml-parser-perl                         2.36-1.1build2                     Perl module for parsing XML files
ii  libxml-twig-perl                           1:3.32-2ubuntu1                    Perl module for processing huge XML documents in tree mode
ii  libxml-xpath-perl                          1.13-6                             Perl module for processing XPath
ii  libxml2                                    2.6.32.dfsg-5ubuntu4               GNOME XML library
ii  libxml2-utils                              2.6.32.dfsg-5ubuntu4               XML utilities
ii  libxmu6                                    2:1.0.4-1                          X11 miscellaneous utility library
ii  libxmuu1                                   2:1.0.4-1                          X11 miscellaneous micro-utility library
ii  libxp6                                     1:1.0.0.xsf1-2                     X Printing Extension (Xprint) client library
ii  libxpm4                                    1:3.5.7-1                          X11 pixmap library
ii  libxrandr2                                 2:1.3.0-1build1                    X11 RandR extension library
ii  libxrender1                                1:0.9.4-2                          X Rendering Extension client library
ii  libxres1                                   2:1.0.3-1                          X11 Resource extension library
ii  libxslt1.1                                 1.1.24-2ubuntu2                    XSLT processing library - runtime library
ii  libxss1                                    1:1.1.3-1                          X11 Screen Saver extension library
ii  libxt6                                     1:1.0.5-3ubuntu1                   X11 toolkit intrinsics library
ii  libxtrap6                                  2:1.0.0-5build1                    X11 event trapping extension library
ii  libxtst6                                   2:1.0.3-1ubuntu2                   X11 Testing -- Resource extension library
ii  libxv1                                     2:1.0.4-1                          X11 Video extension library
ii  libxvmc1                                   2:1.0.4-2ubuntu1                   X11 Video extension library
ii  libxxf86dga1                               2:1.0.2-1                          X11 Direct Graphics Access extension library
ii  libxxf86misc1                              1:1.0.1-3                          X11 XFree86 miscellaneous extension library
ii  libxxf86vm1                                1:1.0.2-1                          X11 XFree86 video mode extension library
ii  libzephyr3                                 2.1.20070719.SNAPSHOT-3            Project Athena's notification service - non-Kerberos libraries
ii  link-grammar-dictionaries-en               4.3.9-2                            Carnegie Mellon University's link grammar parser for English
ii  linux-firmware                             1.11                               Firmware for Linux kernel drivers
ii  linux-generic                              2.6.28.11.15                       Complete Generic Linux kernel
ii  linux-headers-2.6.28-11                    2.6.28-11.42                       Header files related to Linux kernel version 2.6.28
ii  linux-headers-2.6.28-11-generic            2.6.28-11.42                       Linux kernel headers for version 2.6.28 on x86/x86_64
ii  linux-headers-generic                      2.6.28.11.15                       Generic Linux kernel headers
ii  linux-image-2.6.28-11-generic              2.6.28-11.42                       Linux kernel image for version 2.6.28 on x86/x86_64
ii  linux-image-generic                        2.6.28.11.15                       Generic Linux kernel image
ii  linux-libc-dev                             2.6.28-11.42                       Linux Kernel Headers for development
ii  linux-restricted-modules-2.6.28-11-generic 2.6.28-11.15                       Non-free Linux kernel modules for version 2.6.28 on x86/x86_64
ii  linux-restricted-modules-common            2.6.28-11.15                       Non-free Linux 2.6.28 modules helper script
ii  linux-restricted-modules-generic           2.6.28.11.15                       Restricted Linux modules for generic kernels
ii  linux-sound-base                           1.0.18.dfsg-1ubuntu8               base package for ALSA and OSS sound systems
ii  listen                                     0.5-6ubuntu1                       music player and manager for GNOME
ii  locales                                    2.9+cvs20090214-7                  common files for locale support
ii  lockfile-progs                             0.1.11ubuntu2                      Programs for locking and unlocking files and mailboxes
ii  login                                      1:4.1.1-6ubuntu6                   system login tools
ii  logrotate                                  3.7.7-3ubuntu1                     Log rotation utility
ii  lsb-base                                   3.2-20ubuntu4                      Linux Standard Base 3.2 init script functionality
ii  lsb-release                                3.2-20ubuntu4                      Linux Standard Base version reporting utility
ii  lshw                                       02.13-2ubuntu2                     information about hardware configuration
ii  lsof                                       4.78.dfsg.1-4                      List open files
ii  ltrace                                     0.5.1-2ubuntu1                     Tracks runtime library calls in dynamically linked programs
ii  lzma                                       4.43-14ubuntu1                     Compression method of 7z format in 7-Zip program
ii  make                                       3.81-5                             The GNU version of the "make" utility.
ii  makedev                                    2.3.1-88                           creates device files in /dev
ii  man-db                                     2.5.5-1build1                      on-line manual pager
ii  manpages                                   3.15-1                             Manual pages about using a GNU/Linux system
ii  mawk                                       1.3.3-13ubuntu1                    a pattern scanning and text processing language
ii  memtest86+                                 2.11-3ubuntu1                      thorough real-mode memory tester
ii  metacity-common                            1:2.25.144-0ubuntu2                Shared files of lightweight GTK2 based Window Manager
ii  mime-support                               3.44-1                             MIME files 'mime.types' & 'mailcap', and support programs
ii  min12xxw                                   0.0.9-1ubuntu2                     Printer driver for KonicaMinolta PagePro 1[234]xxW
ii  mktemp                                     1.5-9                              tool for creating temporary files
ii  mlocate                                    0.21.1-1ubuntu1                    quickly find files on the filesystem based on their name
ii  mobile-broadband-provider-info             20090309-0ubuntu1                  database of mobile broadband service providers
ii  module-init-tools                          3.7~pre9-2                         tools for managing Linux kernel modules
ii  mount                                      2.14.2-1ubuntu4                    Tools for mounting and manipulating filesystems
ii  mousepad                                   0.2.16-1ubuntu2                    simple Xfce oriented text editor
ii  mozilla-thunderbird                        2.0.0.21+nobinonly-0ubuntu1.9.04.1 Transition package for mozilla-thunderbird rename
ii  mscompress                                 0.3-3                              Microsoft "compress.exe/expand.exe" compatible (de)compressor
ii  mtr-tiny                                   0.75-2                             Full screen ncurses traceroute tool
ii  nano                                       2.0.9-2                            free curses-based text editor, inspired by Pico
ii  ncurses-base                               5.7+20090207-1ubuntu1              basic terminal type definitions
ii  ncurses-bin                                5.7+20090207-1ubuntu1              terminal-related programs and man pages
ii  net-tools                                  1.60-21ubuntu1                     The NET-3 networking toolkit
ii  netbase                                    4.34ubuntu2                        Basic TCP/IP networking system
ii  netcat                                     1.10-38                            TCP/IP swiss army knife -- transitional package
ii  netcat-traditional                         1.10-38                            TCP/IP swiss army knife
ii  network-manager                            0.7.1~rc4.1.cf199a964-0ubuntu2     network management framework daemon
ii  network-manager-gnome                      0.7.1~rc4.1-0ubuntu2               network management framework (GNOME frontend)
ii  notification-daemon                        0.4.0-0ubuntu3                     a daemon that displays passive pop-up notifications
ii  ntfs-3g                                    1:2009.2.1-0ubuntu2                read-write NTFS driver for FUSE
ii  ntpdate                                    1:4.2.4p4+dfsg-7ubuntu5            client for setting system time from NTP servers
ii  nvidia-173-modaliases                      173.14.16-0ubuntu1                 Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-180-modaliases                      180.44-0ubuntu1                    Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-71-modaliases                       71.86.08-0ubuntu1                  Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-96-modaliases                       96.43.10-0ubuntu1                  Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-common                              0.2.11                             Find obsolete NVIDIA drivers
ii  obex-data-server                           0.4.4-0ubuntu1                     D-Bus service for OBEX client and server side functionality
ii  onboard                                    0.91ubuntu2                        Simple On-screen Keyboard
ii  openprinting-ppds                          20090218-0ubuntu3                  OpenPrinting printer support - PostScript PPD files
ii  openssh-client                             1:5.1p1-5ubuntu1                   secure shell client, an rlogin/rsh/rcp replacement
ii  openssl                                    0.9.8g-15ubuntu3                   Secure Socket Layer (SSL) binary and related cryptographic tools
ii  orage                                      4.6.0-1ubuntu1                     Calendar for Xfce Desktop Environment
ii  oss-compat                                 0.0.4+nmu2                         OSS compatibility package
ii  parted                                     1.8.8.git.2008.03.24-11.1ubuntu6   The GNU Parted disk partition resizing program
ii  passwd                                     1:4.1.1-6ubuntu6                   change and administer password and group data
ii  pciutils                                   1:3.0.0-4ubuntu8                   Linux PCI Utilities
ii  pcmciautils                                014-4ubuntu3                       PCMCIA utilities for Linux 2.6
ii  perl                                       5.10.0-19ubuntu1                   Larry Wall's Practical Extraction and Report Language
ii  perl-base                                  5.10.0-19ubuntu1                   minimal Perl system
ii  perl-modules                               5.10.0-19ubuntu1                   Core Perl modules
ii  pidgin                                     1:2.5.5-1ubuntu8                   graphical multi-protocol instant messaging client for X
ii  pidgin-data                                1:2.5.5-1ubuntu8                   multi-protocol instant messaging client - data files
ii  pidgin-otr                                 3.2.0-3ubuntu1                     Off-the-Record Messaging plugin for pidgin
ii  pm-utils                                   1.2.2.4-0ubuntu4                   utilities and scripts for power management
ii  pnm2ppa                                    1.12-16.2ubuntu1                   PPM to PPA converter
ii  policykit                                  0.9-2ubuntu1                       framework for managing administrative policies and privileges
ii  policykit-gnome                            0.9-1ubuntu3                       GNOME dialogs for PolicyKit
ii  poppler-utils                              0.10.5-1ubuntu2                    PDF utilitites (based on libpoppler)
ii  popularity-contest                         1.46ubuntu1                        Vote for your favourite packages automatically
ii  powermgmt-base                             1.30+nmu1                          Common utils and configs for power management
ii  ppp                                        2.4.5~git20081126t100229-0ubuntu2  Point-to-Point Protocol (PPP) - daemon
ii  pppconfig                                  2.3.18ubuntu2                      A text menu based utility for configuring ppp
ii  pppoeconf                                  1.18ubuntu1                        configures PPPoE/ADSL connections
ii  procps                                     1:3.2.7-11ubuntu2                  /proc file system utilities
ii  psfontmgr                                  0.11.10-0.2ubuntu1                 PostScript font manager -- part of Defoma, Debian Font Manager
ii  psmisc                                     22.6-1                             Utilities that use the proc filesystem
ii  psutils                                    1.17-26                            A collection of PostScript document handling utilities
ii  pxljr                                      1.1-0ubuntu6                       Driver for HP's Color LaserJet 35xx/36xx color laser printers
ii  python                                     2.6.2-0ubuntu1                     An interactive high-level object-oriented language (default vers
ii  python-apport                              1.0-0ubuntu5                       apport crash report handling library
ii  python-apt                                 0.7.9~exp2ubuntu10                 Python interface to libapt-pkg
ii  python-cairo                               1.4.12-1.2ubuntu1                  Python bindings for the Cairo vector graphics library
ii  python-central                             0.6.11ubuntu7                      register and build utility for Python packages
ii  python-cups                                1.9.45-0ubuntu2                    Python bindings for CUPS
ii  python-cupshelpers                         1.1.3+git20090218-0ubuntu19        Python modules for printer configuration with CUPS
ii  python-dbus                                0.83.0-1ubuntu1                    simple interprocess messaging system (Python interface)
ii  python-debian                              0.1.12ubuntu2                      Python modules to work with Debian-related data formats
ii  python-gconf                               2.26.1-0ubuntu1                    Python bindings for GConf2
ii  python-gdata                               1.2.4-0ubuntu1                     Google Data Python client library
ii  python-gdbm                                2.6.2-0ubuntu1                     GNU dbm database support for Python
ii  python-glade2                              2.14.1-1ubuntu1                    GTK+ bindings: Glade support
ii  python-gnome2                              2.26.1-0ubuntu1                    Python bindings for the GNOME desktop environment
ii  python-gnome2-desktop                      2.26.0-0ubuntu3                    Python bindings for the GNOME desktop environment
ii  python-gnome2-extras                       2.19.1-0ubuntu14                   Python bindings for the GNOME desktop environment
ii  python-gnomecanvas                         2.26.1-0ubuntu1                    Python bindings for gnomecanvas (debug extension)
ii  python-gnupginterface                      0.3.2-9ubuntu2                     Python interface to GnuPG (GPG)
ii  python-gobject                             2.16.1-1ubuntu2                    Python bindings for the GObject library
ii  python-gst0.10                             0.10.14-1ubuntu1                   generic media-playing framework (Python bindings)
ii  python-gtk2                                2.14.1-1ubuntu1                    Python bindings for the GTK+ widget set
ii  python-gtkhtml2                            2.19.1-0ubuntu14                   Python bindings for the GtkHTML2 library
ii  python-imaging                             1.1.6-3ubuntu1                     Python Imaging Library
ii  python-launchpad-bugs                      0.3.5                              simple Python Interface to Bugs in Launchpad
ii  python-launchpad-integration               0.1.24                             library for launchpad integration
ii  python-libxml2                             2.6.32.dfsg-5ubuntu4               Python bindings for the GNOME XML library
ii  python-minimal                             2.6.2-0ubuntu1                     A minimal subset of the Python language (default version)
ii  python-musicbrainz2                        0.6.0-2                            An interface to the MusicBrainz XML web service
ii  python-mutagen                             1.14-2                             audio metadata editing library
ii  python-newt                                0.52.2-11.3ubuntu3                 A NEWT module for Python
ii  python-notify                              0.1.1-2build2                      Python bindings for libnotify
ii  python-ogg                                 1.3+repack-2ubuntu1                Python interface to the Ogg library
ii  python-pkg-resources                       0.6c9-0ubuntu4                     Package Discovery and Resource Access using pkg_resources
ii  python-problem-report                      1.0-0ubuntu5                       Python library to handle problem reports
ii  python-pymad                               0.5.4-3.2build2                    Python wrapper to the MPEG Audio Decoder library
ii  python-pyogg                               1.3+repack-2ubuntu1                transitional dummy package
ii  python-pyorbit                             2.24.0-0ubuntu3                    A Python language binding for the ORBit2 CORBA implementation
ii  python-pysqlite2                           2.5.0-2ubuntu1                     Python interface to SQLite 3
ii  python-pyvorbis                            1.3-2ubuntu1                       A Python interface to the Ogg Vorbis library
ii  python-rdflib                              2.4.0-5ubuntu1                     RDF library containing an RDF triple store and RDF/XML parser/se
ii  python-sexy                                0.1.9-1ubuntu2                     python language bindings for libsexy
ii  python-smbc                                1.0.6-0ubuntu2                     Python bindings for Samba clients (libsmbclient)
ii  python-software-properties                 0.71.5                             manage the repositories that you install software from
ii  python-support                             0.8.7ubuntu4                       automated rebuilding support for Python modules
ii  python-tunepimp                            0.5.3-7ubuntu3                     Python bindings for MusicBrainz tagging library
ii  python-usb                                 0.4.1-4ubuntu1                     USB interface for Python
ii  python-virtkey                             0.50ubuntu2                        Library to emulate keyboard keypresses.
ii  python-vte                                 1:0.20.0-0ubuntu2                  Python bindings for the VTE widget set
ii  python-xapian                              1.0.7-3.1ubuntu2                   Xapian search engine interface for Python
ii  python-xdg                                 0.15-1.1ubuntu5                    A python library to access freedesktop.org standards
ii  python-xkit                                0.4.2                              library for the manipulation of the xorg.conf
ii  python2.6                                  2.6.2-0ubuntu1                     An interactive high-level object-oriented language (version 2.6)
ii  python2.6-minimal                          2.6.2-0ubuntu1                     A minimal subset of the Python language (version 2.6)
ii  radeontool                                 1.5+git76606164-0ubuntu2           utility to control ATI Radeon backlight functions on laptops
ii  rarian-compat                              0.8.1-1ubuntu2                     Rarian is a documentation meta-data library (compatibility tools
ii  readahead                                  1:0.20050517.0220-1ubuntu5         read files into the page cache
ii  readline-common                            5.2-4                              GNU readline and history libraries, common files
ii  reiserfsprogs                              1:3.6.19-6                         User-level tools for ReiserFS filesystems
ii  rss-glx                                    0.8.2-1ubuntu3                     Really Slick Screensavers GLX Port
ii  rsync                                      3.0.5-1ubuntu2                     fast remote file copy program (like rcp)
ii  samba-common                               2:3.3.2-1ubuntu3                   common files used by both the Samba server and client
ii  sane-utils                                 1.0.19-23ubuntu7                   API library for scanners -- utilities
ii  scim                                       1.4.7-3ubuntu12                    smart common input method platform
ii  scim-bridge-agent                          0.4.14-2ubuntu5                    IME server of scim-bridge communicate with SCIM
ii  scim-bridge-client-gtk                     0.4.14-2ubuntu5                    IME server of scim-bridge communicate with SCIM
ii  scim-gtk2-immodule                         1.4.7-3ubuntu12                    GTK+2 input method module with SCIM as backend
ii  scim-modules-socket                        1.4.7-3ubuntu12                    socket modules for SCIM platform
ii  scim-modules-table                         0.5.8-1                            generic tables IM engine module for SCIM platform
ii  scim-tables-additional                     0.5.8-1                            miscellaneous input method data tables for SCIM platform
ii  screen                                     4.0.3-11ubuntu4                    terminal multiplexor with VT100/ANSI terminal emulation
ii  screen-profiles                            1.44-0ubuntu1                      a set of useful profiles and a profile-switcher for GNU screen
ii  screensaver-default-images                 0.2-1                              Wallpapers for image processing screensavers
ii  seahorse                                   2.26.1-0ubuntu1                    A Gnome front end for GnuPG
ii  seahorse-plugins                           2.26.1-0ubuntu1                    seahorse plugins and utilities for encryption in GNOME
ii  sed                                        4.1.5-8                            The GNU sed stream editor
ii  sgml-base                                  1.26                               SGML infrastructure and SGML catalog file support
ii  sgml-data                                  2.0.3                              common SGML and XML data
ii  shared-mime-info                           0.60-1                             FreeDesktop.org shared MIME database and spec
ii  smartdimmer                                0.8b4-1ubuntu2                     Change LCD brightness on Geforce cards
ii  smbclient                                  2:3.3.2-1ubuntu3                   command-line SMB/CIFS clients for Unix
ii  software-properties-gtk                    0.71.5                             manage the repositories that you install software from
ii  splix                                      2.0.0-0.1ubuntu3                   Driver for Samsung's SPL2 (bw) and SPLc (color) laser printers
ii  ssh-askpass-gnome                          1:5.1p1-5ubuntu1                   interactive X program to prompt users for a passphrase for ssh-a
ii  ssl-cert                                   1.0.23ubuntu1                      simple debconf wrapper for OpenSSL
ii  startup-tasks                              0.3.9-8                            definitions of essential tasks to run on startup
ii  strace                                     4.5.17+cvs080723-2ubuntu1          A system call tracer
ii  sudo                                       1.6.9p17-1ubuntu3                  Provide limited super user privileges to specific users
ii  synaptic                                   0.62.5ubuntu2.1                    Graphical package manager
ii  sysklogd                                   1.5-5ubuntu3                       System Logging Daemon
ii  system-config-printer-common               1.1.3+git20090218-0ubuntu19        Printer configuration GUI
ii  system-config-printer-gnome                1.1.3+git20090218-0ubuntu19        Printer configuration GUI
ii  system-services                            0.3.9-8                            definitions of essential system services
ii  system-tools-backends                      2.6.0-2ubuntu8                     System Tools to manage computer configuration -- scripts
ii  sysv-rc                                    2.86.ds1-61ubuntu11                System-V-like runlevel change mechanism
ii  sysvinit-utils                             2.86.ds1-61ubuntu11                System-V-like utilities
ii  tango-icon-theme                           0.8.90-1                           Tango icon theme
ii  tango-icon-theme-common                    0.7-0ubuntu1                       Tango Icon theme - common icons
ii  tar                                        1.20-1                             GNU version of the tar archiving utility
ii  tasksel                                    2.73ubuntu18                       Tool for selecting tasks for installation on Debian systems
ii  tasksel-data                               2.73ubuntu18                       Official tasks used for installation of Debian systems
ii  tcl8.4                                     8.4.19-2                           Tcl (the Tool Command Language) v8.4 - run-time files
ii  tcpd                                       7.6.q-16                           Wietse Venema's TCP wrapper utilities
ii  tcpdump                                    3.9.8-4ubuntu2                     A powerful tool for network monitoring and data acquisition
ii  telnet                                     0.17-36                            The telnet client
ii  thunar                                     1.0.0-1ubuntu3                     File Manager for Xfce
ii  thunar-archive-plugin                      0.2.4-4                            Archive plugin for Thunar file manager
ii  thunar-data                                1.0.0-1ubuntu3                     Provides thunar documentation, icons and translations
ii  thunar-media-tags-plugin                   0.1.2+svn-r04939-0ubuntu2          Media tags plugin for Thunar file manager
ii  thunar-thumbnailers                        0.4.1-0ubuntu1                     thumbnailers for Thunar file manager
ii  thunar-volman                              0.3.80-0ubuntu1                    Thunar extension for volumes management
ii  thunderbird                                2.0.0.21+nobinonly-0ubuntu1.9.04.1 mail/news client with RSS and integrated spam filter support
ii  time                                       1.7-23                             The GNU time program for measuring cpu resource usage
ii  toshset                                    1.73-3                             Access much of the Toshiba laptop hardware interface
ii  totem                                      2.26.1-0ubuntu5                    A simple media player for the GNOME desktop (dummy package)
ii  totem-common                               2.26.1-0ubuntu5                    Data files for the Totem media player
ii  totem-gstreamer                            2.26.1-0ubuntu5                    A simple media player for the GNOME desktop based on GStreamer
ii  totem-mozilla                              2.26.1-0ubuntu5                    Totem Mozilla plugin
ii  totem-plugins                              2.26.1-0ubuntu5                    Plugins for the Totem media player
ii  transmission-common                        1.51-0ubuntu3                      lightweight BitTorrent client (common files)
ii  transmission-gtk                           1.51-0ubuntu3                      lightweight BitTorrent client (graphical interface)
ii  ttf-arabeyes                               2.0-2                              Arabeyes GPL TrueType Arabic fonts
ii  ttf-arphic-uming                           0.2.20080216.1-3ubuntu2            "AR PL UMing" Chinese Unicode TrueType font collection Mingti st
ii  ttf-bitstream-vera                         1.10-7                             The Bitstream Vera family of free TrueType fonts
ii  ttf-dejavu-core                            2.28-1                             Vera font family derivate with additional characters
ii  ttf-freefont                               20080323-3                         Freefont Serif, Sans and Mono Truetype fonts
ii  ttf-indic-fonts-core                       1:0.5.4ubuntu2                     Core collection of free Indian language fonts
ii  ttf-lao                                    0.0.20060226-2                     TrueType font for Lao language
ii  ttf-opensymbol                             1:3.0.1-9ubuntu3                   OpenSymbol TrueType font
ii  ttf-sazanami-gothic                        20040629-2ubuntu2                  Sazanami Gothic Japanese TrueType font
ii  ttf-sazanami-mincho                        20040629-2ubuntu2                  Sazanami Mincho Japanese TrueType font
ii  ttf-thai-tlwg                              1:0.4.11-2                         Thai fonts in TrueType format
ii  ttf-unfonts-core                           1.0.1-7ubuntu1                     Un series Korean TrueType fonts
ii  tzdata                                     2009f-0ubuntu1                     time zone and daylight-saving time data
ii  ubufox                                     0.7-0ubuntu1                       Ubuntu Firefox specific configuration defaults and apt support
ii  ubuntu-keyring                             2008.03.04                         GnuPG keys of the Ubuntu archive
ii  ubuntu-minimal                             1.140                              Minimal core of Ubuntu
ii  ubuntu-standard                            1.140                              The Ubuntu standard system
ii  ucf                                        3.0014                             Update Configuration File: preserve user changes to config files
ii  udev                                       141-1                              rule-based device node and kernel event manager
ii  ufw                                        0.27-0ubuntu2                      program for managing a netfilter firewall
ii  unattended-upgrades                        0.39                               automatic installation of security upgrades
ii  unzip                                      5.52-12ubuntu1                     De-archiver for .zip files
ii  update-inetd                               4.31                               inetd configuration file updater
ii  update-manager                             1:0.111.7                          GNOME application that manages apt updates
ii  update-manager-core                        1:0.111.7                          manage release upgrades
ii  update-motd                                1.11.1                             Modular framework to dynamically generate the message of the day
ii  update-notifier                            0.76.7                             Daemon which notifies about package updates
ii  update-notifier-common                     0.76.7                             Files shared between update-notifier and adept
ii  upstart                                    0.3.9-8                            event-based init daemon
ii  upstart-compat-sysv                        0.3.9-8                            compatibility for System-V-like init
ii  upstart-logd                               0.3.9-8                            boot logging daemon
ii  usbutils                                   0.73-8ubuntu3                      Linux USB utilities
ii  usplash                                    0.5.31                             Userspace bootsplash utility
ii  util-linux                                 2.14.2-1ubuntu4                    Miscellaneous system utilities
ii  uuid-runtime                               1.41.4-1ubuntu1                    universally unique id library
ii  vbetool                                    1.1-2                              run real-mode video BIOS code to alter hardware state
ii  vim-common                                 2:7.2.079-1ubuntu5                 Vi IMproved - Common files
ii  vim-runtime                                2:7.2.079-1ubuntu5                 Vi IMproved - Runtime files
ii  vim-tiny                                   2:7.2.079-1ubuntu5                 Vi IMproved - enhanced vi editor - compact version
ii  vinagre                                    2.26.1-0ubuntu1                    VNC client for the GNOME Desktop
ii  w3m                                        0.5.2-2build1                      WWW browsable pager with excellent tables/frames support
ii  wdiff                                      0.5-18                             Compares two files word by word
ii  wget                                       1.11.4-2ubuntu1                    retrieves files from the web
ii  whiptail                                   0.52.2-11.3ubuntu3                 Displays user-friendly dialog boxes from shell scripts
ii  wireless-crda                              1.7                                Wireless Central Regulatory Domain Agent
ii  wireless-tools                             29-1.1ubuntu2                      Tools for manipulating Linux Wireless Extensions
ii  wodim                                      9:1.1.9-1ubuntu1                   command line CD/DVD writing tool
ii  wpasupplicant                              0.6.6-2ubuntu1                     client support for WPA and WPA2 (IEEE 802.11i)
ii  x-ttcidfont-conf                           32                                 TrueType and CID fonts configuration for X
ii  x11-apps                                   7.3+4                              X applications
ii  x11-common                                 1:7.4~5ubuntu18                    X Window System (X.Org) infrastructure
ii  x11-session-utils                          7.3+1                              X session utilities
ii  x11-utils                                  7.4+1build1                        X11 utilities
ii  x11-xfs-utils                              7.4+1build1                        X font server utilities
ii  x11-xkb-utils                              7.4+1ubuntu2                       X11 XKB utilities
ii  x11-xserver-utils                          7.4+1                              X server utilities
ii  xauth                                      1:1.0.3-2                          X authentication utility
ii  xbitmaps                                   1.0.1-2ubuntu1                     Base X bitmaps
ii  xchat                                      2.8.6-2.1ubuntu4                   IRC client for X similar to AmIRC
ii  xchat-common                               2.8.6-2.1ubuntu4                   Common files for X-Chat
ii  xcursor-themes                             1.0.1-5ubuntu1                     Base X cursor themes
ii  xdg-user-dirs                              0.10-1ubuntu2                      tool to manage well known user directories
ii  xdg-utils                                  1.0.2-6.1                          desktop integration utilities from freedesktop.org
ii  xfce4-appfinder                            4.6.0-1                            Application finder for the Xfce4 Desktop Environment
ii  xfce4-battery-plugin                       0.5.1-0ubuntu1                     battery monitor plugin for the Xfce4 panel
ii  xfce4-clipman-plugin                       2:0.9.0-0ubuntu1                   clipboard history plugin for the Xfce4 panel
ii  xfce4-cpugraph-plugin                      0.4.0-0ubuntu1                     CPU load graph plugin for the Xfce4 panel
ii  xfce4-dict                                 0.5.2-0ubuntu1                     Dictionary plugin for Xfce4 panel
ii  xfce4-dict-plugin                          0.5.2-0ubuntu1                     transitionnal dummy package for xfce4-dict
ii  xfce4-fsguard-plugin                       0.4.2-0ubuntu1                     filesystem monitor plugin for the Xfce4 panel
ii  xfce4-governor-plugin                      0.1.0-0ubuntu1                     governor plugin for the Xfce4 panel
ii  xfce4-mailwatch-plugin                     1.1.0-0ubuntu1                     mail watcher plugin for the Xfce4 panel
ii  xfce4-mixer                                1:4.6.0-1ubuntu2                   Xfce mixer application
ii  xfce4-mount-plugin                         0.5.5-1                            mount plugin for the Xfce4 panel
ii  xfce4-netload-plugin                       0.4.0-3ubuntu3                     network load monitor plugin for the Xfce4 panel
ii  xfce4-notes-plugin                         1.6.3-0ubuntu2                     Notes plugin for the Xfce4 desktop
ii  xfce4-panel                                4.6.0-1ubuntu1                     The Xfce4 desktop environment panel
ii  xfce4-places-plugin                        1.1.0-2                            quick access to folders, documents and removable media
ii  xfce4-quicklauncher-plugin                 1.9.4-2ubuntu2                     rapid launcher plugin for the Xfce4 panel
ii  xfce4-screenshooter                        1.5.1-0ubuntu1                     screenshots utility for Xfce
ii  xfce4-session                              4.6.0-1ubuntu2                     Xfce4 Session Manager
ii  xfce4-settings                             4.6.0-1ubuntu2                     graphical application for managing Xfce settings
ii  xfce4-smartbookmark-plugin                 0.4.2-1ubuntu4                     search the web via the Xfce4 panel
ii  xfce4-systemload-plugin                    1:0.4.2-1ubuntu3                   system load monitor plugin for the Xfce4 panel
ii  xfce4-terminal                             0.2.10-1ubuntu2                    Xfce terminal emulator
ii  xfce4-utils                                4.6.0-1ubuntu2                     Various tools for Xfce
ii  xfce4-verve-plugin                         0.3.6-0ubuntu1                     Verve (command line) plugin for Xfce 4.4 panel
ii  xfce4-weather-plugin                       0.6.2-1ubuntu2                     weather information plugin for the Xfce4 panel
ii  xfce4-xkb-plugin                           0.5.3.2-0ubuntu1                   xkb layout switch plugin for the Xfce4 panel
ii  xfconf                                     4.6.0-1~ubuntu1                    utilities for managing settings in Xfce
ii  xfdesktop4                                 4.6.0-1ubuntu1                     xfce desktop background, icons and root menu manager
ii  xfdesktop4-data                            4.6.0-1ubuntu1                     xfce desktop background, icons and root menu (common files)
ii  xfonts-100dpi                              1:1.0.0-4                          100 dpi fonts for X
ii  xfonts-75dpi                               1:1.0.0-4                          75 dpi fonts for X
ii  xfonts-base                                1:1.0.0-5                          standard fonts for X
ii  xfonts-encodings                           1:1.0.2-3                          Encodings for X.Org fonts
ii  xfonts-scalable                            1:1.0.0-6ubuntu0.8.04.1            scalable fonts for X
ii  xfonts-utils                               1:7.4+1ubuntu1                     X Window System font utility programs
ii  xfprint4                                   4.6.0-1ubuntu3                     Printer GUI for Xfce4
ii  xfswitch-plugin                            0.0.1-0ubuntu1                     fast user switching plugin for the Xfce panel
ii  xfwm4                                      4.6.0-1ubuntu3                     window manager of the Xfce project
ii  xfwm4-themes                               4.6.0-1                            Theme files for xfwm4
ii  xinit                                      1.0.9-2                            X server initialisation tool
ii  xinput                                     1.4.0-1                            Runtime configuration and test of XInput devices
ii  xkb-data                                   1.5-2ubuntu11                      X Keyboard Extension (XKB) configuration data
ii  xml-core                                   0.12                               XML infrastructure and XML catalog file support
ii  xorg                                       1:7.4~5ubuntu18                    X.Org X Window System
ii  xsane                                      0.996-1ubuntu2                     featureful graphical frontend for SANE (Scanner Access Now Easy)
ii  xsane-common                               0.996-1ubuntu2                     featureful graphical frontend for SANE (Scanner Access Now Easy)
ii  xscreensaver-data                          5.07-0ubuntu3                      data files to be shared among screensaver frontends
ii  xscreensaver-gl                            5.07-0ubuntu3                      GL(Mesa) screen hacks for xscreensaver
ii  xserver-common                             2:1.6.0-0ubuntu14                  common files used by various X servers
ii  xserver-xorg                               1:7.4~5ubuntu18                    the X.Org X server
ii  xserver-xorg-core                          2:1.6.0-0ubuntu14                  Xorg X server - core server
ii  xserver-xorg-input-all                     1:7.4~5ubuntu18                    the X.Org X server -- input driver metapackage
ii  xserver-xorg-input-evdev                   1:2.1.1-1ubuntu4                   X.Org X server -- evdev input driver
ii  xserver-xorg-input-kbd                     1:1.3.1-2ubuntu1                   X.Org X server -- keyboard input driver
ii  xserver-xorg-input-mouse                   1:1.4.0-1                          X.Org X server -- mouse input driver
ii  xserver-xorg-input-synaptics               0.99.3-2ubuntu4                    Synaptics TouchPad driver for X.Org/XFree86 server
ii  xserver-xorg-input-wacom                   1:0.8.2.2-0ubuntu2                 X.Org X server -- Wacom input driver
ii  xserver-xorg-video-all                     1:7.4~5ubuntu18                    the X.Org X server -- output driver metapackage
ii  xserver-xorg-video-apm                     1:1.2.1-1                          X.Org X server -- APM display driver
ii  xserver-xorg-video-ark                     1:0.7.1-1                          X.Org X server -- ark display driver
ii  xserver-xorg-video-ati                     1:6.12.1-0ubuntu2                  X.Org X server -- ATI display driver wrapper
ii  xserver-xorg-video-chips                   1:1.2.1-1                          X.Org X server -- Chips display driver
ii  xserver-xorg-video-cirrus                  1:1.2.1-3                          X.Org X server -- Cirrus display driver
ii  xserver-xorg-video-fbdev                   1:0.4.0-3                          X.Org X server -- fbdev display driver
ii  xserver-xorg-video-geode                   2.11.1-1                           X.Org server -- Geode GX2/LX display driver
ii  xserver-xorg-video-i128                    1:1.3.1-2ubuntu1                   X.Org X server -- i128 display driver
ii  xserver-xorg-video-i740                    1:1.2.0-2                          X.Org X server -- i740 display driver
ii  xserver-xorg-video-intel                   2:2.6.3-0ubuntu9                   X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-mach64                  6.8.0-3                            X.Org X server -- ATI Mach64 display driver
ii  xserver-xorg-video-mga                     1:1.4.9.dfsg-3                     X.Org X server -- MGA display driver
ii  xserver-xorg-video-neomagic                1:1.2.2-1                          X.Org X server -- Neomagic display driver
ii  xserver-xorg-video-nv                      1:2.1.12-1ubuntu5                  X.Org X server -- NV display driver
ii  xserver-xorg-video-openchrome              1:0.2.903+svn713-1ubuntu1          X.Org X server -- VIA display driver
ii  xserver-xorg-video-r128                    6.8.0+git20090201.08d56c88-1       X.Org X server -- ATI r128 display driver
ii  xserver-xorg-video-radeon                  1:6.12.1-0ubuntu2                  X.Org X server -- ATI Radeon display driver
ii  xserver-xorg-video-rendition               1:4.2.0.dfsg.1-2ubuntu1            X.Org X server -- Rendition display driver
ii  xserver-xorg-video-s3                      1:0.6.1-1                          X.Org X server -- legacy S3 display driver
ii  xserver-xorg-video-s3virge                 1:1.10.2-1                         X.Org X server -- S3 ViRGE display driver
ii  xserver-xorg-video-savage                  1:2.2.1-4ubuntu2                   X.Org X server -- Savage display driver
ii  xserver-xorg-video-siliconmotion           1:1.7.0-1                          X.Org X server -- SiliconMotion display driver
ii  xserver-xorg-video-sis                     1:0.10.1-1                         X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb                  1:0.9.0-4                          X.Org X server -- SiS USB display driver
ii  xserver-xorg-video-tdfx                    1:1.4.0-2                          X.Org X server -- tdfx display driver
ii  xserver-xorg-video-trident                 1:1.3.0-1ubuntu1                   X.Org X server -- Trident display driver
ii  xserver-xorg-video-tseng                   1:1.2.0-1ubuntu1                   X.Org X server -- Tseng display driver
ii  xserver-xorg-video-v4l                     1:0.2.0-1ubuntu5                   X.Org X server -- Video 4 Linux display driver
ii  xserver-xorg-video-vesa                    1:2.0.0-1ubuntu6                   X.Org X server -- VESA display driver
ii  xserver-xorg-video-vmware                  1:10.16.5-2                        X.Org X server -- VMware display driver
ii  xserver-xorg-video-voodoo                  1:1.2.0-1ubuntu1                   X.Org X server -- Voodoo display driver
ii  xsltproc                                   1.1.24-2ubuntu2                    XSLT command line processor
ii  xterm                                      241-1ubuntu1                       X terminal emulator
ii  xubuntu-artwork                            0.26                               Xubuntu themes and artwork
ii  xubuntu-artwork-usplash                    0.26                               Xubuntu usplash image
ii  xubuntu-default-settings                   0.56                               default settings for Xubuntu
ii  xubuntu-desktop                            2.82                               Xubuntu desktop system
ii  xubuntu-docs                               9.04.2                             xubuntu documentation
ii  xulrunner-1.9                              1.9.0.8+nobinonly-0ubuntu2         XUL + XPCOM application runner
ii  xulrunner-1.9-gnome-support                1.9.0.8+nobinonly-0ubuntu2         Support for Gnome in xulrunner-1.9 applications
ii  yelp                                       2.25.1-0ubuntu5                    Help browser for GNOME 2
ii  zenity                                     2.26.0-0ubuntu2                    Display graphical dialog boxes from shell scripts
ii  zip                                        2.32-1                             Archiver for .zip files
ii  zlib1g                                     1:1.2.3.3.dfsg-12ubuntu2           compression library - runtime

```

---

### Post by Jose Catre-Vandis on 2009-06-01
Bear in mind you can run whatever applications you like if you install them through the repos. You might also doing a command line only install and build up from there?

---

