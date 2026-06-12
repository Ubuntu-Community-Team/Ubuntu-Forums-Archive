---
title: "skype 1.3 beta and microphone problem"
date: 2006-07-12
forum: Desktop Environments
---

### Post by dag0 on 2006-07-12
hi folks :-)

I just did a fresh install of Ubuntu Dapper Drake 6.06 on my computer and Skype 1.3 beta. When I do the test call it won't record my talk with the mic. "Check your sound settings..." I did and I checked that the mic is not muted. I'm using ALSA mixer. My sound card is: Turtle Beach Santa Cruz. Preferences of the sound it says: Sound Fusion CS46xx (ALSA mixer). 
I have perfect sound of the lady at test call in my headset, but I hear myself also in the headset.

Is there any chance to fix this or is it the soundcard who is making this problem ? Should I replace it with Soundblaser card ?

Dag

---

### Post by nmilkosky on 2006-07-12
This is how I fixed that for me: First of all make sure the mic is plugged in correctly.
2. Go to volume control in sound and video. If its not there- check it off (enable it to be seen) in alacarte menu editor.
3. Turn one mic thingy off(the right-side one with the picture of a mic)
4. Turn both capture thingys on.
5. Just press the X button in the corner and exit.
If you go back to the menu(volume control), you'll have to reconfigure it again.
It should work now.
[IMG]http://images.nmnetworks.net/micguide.png[/IMG]

---

### Post by dag0 on 2006-07-12
Hi again :-)

It did not work..

I tried to mark the mic on the right side exactly like you showed me but it dont work. And it dont remember I marked it off. When I start the volume control again it is not marked off..

The mic is connected correctly. My wife use skype in heer winxp partition. 

So, any other tips ? 

Thanks

Dag

---

### Post by mvaranda on 2006-07-12
Skype 1.3 rocks...

The only thing is that we need to enable mic on "capture" tab as explained in the second post in this thread.

the 1.2 used to work only in my wired server (and with the patch to work-around the device release). Now, with 1.3, all my laptops using wifi 802.11 are working fine and no more problems with releasing DSP device :-)

Good job Skype devs !

Cheers

---

### Post by AiBo on 2006-07-18
Can anyone help me make sense of this error when I try to run skype:

~$ skype
*** glibc detected *** free(): invalid pointer: 0x08a222b0 ***
Aborted



Thanks alot!

---

### Post by raditzman on 2006-07-19
> **AiBo said:**
> Can anyone help me make sense of this error when I try to run skype:

~$ skype
*** glibc detected *** free(): invalid pointer: 0x08a222b0 ***
Aborted



Thanks alot!
Hi, the only thing I can think off is removing with --purge like this 
```
sudo apt-get remove --purge skype
```

This will remove skype, including all its configuration files (possibly left-over from a previous instalation which are messing things up.)

Then you can do:
```
sudo dpkg -i PACKAGE
```

Where PACKAGE is the skype file for ubuntu you can get from [http://skype.com/download/skype/linux/13beta.html]("http://skype.com/download/skype/linux/13beta.html") 


If this doesn't work, perhaps it is due to the glibc version you're using, are you using a very customized ubuntu? Tell me what package of glibc you're using if the previous didn't work with
```
dpkg -l | grep glib

```

Take care
Dan

---

### Post by brian g on 2006-07-26
> **dag0 said:**
> hi folks :-)

I just did a fresh install of Ubuntu Dapper Drake 6.06 on my computer and Skype 1.3 beta. When I do the test call it won't record my talk with the mic. "Check your sound settings..." I did and I checked that the mic is not muted. I'm using ALSA mixer. My sound card is: Turtle Beach Santa Cruz. Preferences of the sound it says: Sound Fusion CS46xx (ALSA mixer). 
I have perfect sound of the lady at test call in my headset, but I hear myself also in the headset.

Is there any chance to fix this or is it the soundcard who is making this problem ? Should I replace it with Soundblaser card ?

Dagsame soundcard and skype version, same problem.

---

### Post by whiteB on 2006-07-31
He,
  Convert the RPM of skype 1.3 to debian package and install.
  I also having the problem with skype1.3 debian beta package.
  When i converted the rpm to debian and installed ,everything is 
  working..You should use UBUNTU Latest..

---

### Post by AiBo on 2006-07-31
Dan

Thanks for your suggestions!  Sorry I did not recieve notification of your reply.  I tried all you suggested.

I do not think my ubuntu is overly customized.  I am still quite the newbie so I haven't done all that much.

Here are the results 

XX@XX-laptop:~/Desktop/SharedDailyBackups$ sudo dpkg -i skype-beta-1.3.0.30-1_i386.deb
Selecting previously deselected package skype.
(Reading database ... 138062 files and directories currently installed.)
Unpacking skype (from skype-beta-1.3.0.30-1_i386.deb) ...
Setting up skype (1.3.0.30-1) ...
XX@XX-laptop:~/Desktop/SharedDailyBackups$ dpkg -l | grep glib ii  libavahi-glib1                         0.6.10-0ubuntu3  Avahi glib integration library
ii  libdbus-glib-1-2                       0.60-6ubuntu8  simple interprocess messaging system (GLib-b
ii  libglib-perl                           1.103-1  Perl interface to the GLib and GObject libra
ii  libglib1.2                             1.2.10-10.1build1  The GLib library of C routines
ii  libglib2.0-0                           2.10.3-0ubuntu1  The GLib library of C routines
ii  libglib2.0-data                        2.10.3-0ubuntu1  Common files for GLib library
ii  libglibmm-2.4-1c2a                     2.10.4-0ubuntu1  C++ wrapper for the GLib toolkit (shared lib
ii  libpoppler1-glib                       0.5.1-0ubuntu7  PDF rendering library (GLib-based shared lib
XX@XX-laptop:~/Desktop/SharedDailyBackups$ skype
*** glibc detected *** free(): invalid pointer: 0x08aaa760 ***
Aborted
XX@XX-laptop:~/Desktop/SharedDailyBackups$
 
Thanks in advance for any other suggestions you might have!

RGE

Update:

I did a fresh install of dapper.  Skype worked...well all but not being able to record my voice!  But at least it loaded and I could test call and hear the computer voice.

Then I install SCIM which I need as I switch between Chinese and English all day in my work.

I also updated via update manager....

guess what...type skype into terminal gives me:

XX@XX-laptop:~$ skype
*** glibc detected *** free(): invalid pointer: 0x08aa7030 ***
Aborted

---

### Post by AiBo on 2006-08-03
oh yeah I have kde and gnome installed...

dpkg -l | grep glib gives me the following:


remote incremental backup
ii  readahead                              0.20050517.0220-0ubuntu3    read files into the page cache
ii  readline-common                        5.1-7build1    GNU readline and history libraries, common f
ii  reiser4progs                           1.0.5-1    administration utilities for the Reiser4 fil
ii  reiserfsprogs                          3.6.19-1    User-level tools for ReiserFS filesystems
ii  reportbug                              3.18ubuntu1    reports bugs in the Debian distribution
ii  rhythmbox                              0.9.3.1-0ubuntu9    music player and organizer for GNOME
ii  rss-glx                                0.8.0-1ubuntu7    Really Slick Screensavers GLX Port
ii  rsync                                  2.6.6-1ubuntu2    fast remote file copy program (like rcp)
ii  samba-common                           3.0.22-1ubuntu3.1    Samba common files used by both the server a
ii  scim                                   1.4.4-1ubuntu12    smart common input method platform
ii  scim-chewing                           0.2.1-2ubuntu4    Chewing IM engine module for SCIM
ii  scim-gtk2-immodule                     1.4.4-1ubuntu12    GTK+2 input method module with SCIM as backe
ii  scim-modules-socket                    1.4.4-1ubuntu12    socket modules for SCIM platform
ii  scim-modules-table                     0.5.6-1build1    generic tables IM engine module for SCIM pla
ii  scim-pinyin                            0.5.91-0ubuntu3    smart pinyin IM engine for SCIM platform
ii  scim-qtimm                             0.9.4-0ubuntu4    SCIM context plugin for qt-immodule
ii  scim-tables-zh                         0.5.6-1build1    Chinese input method data tables for SCIM pl
ii  screen                                 4.0.2-4.1ubuntu5    a terminal multiplexor with VT100/ANSI termi
ii  screensaver-default-images             0.2-1    Wallpapers for image processing screensavers
ii  scrollkeeper                           0.3.14-11ubuntu6    A free electronic cataloging system for docu
ii  sed                                    4.1.4-5    The GNU sed stream editor
ii  serpentine                             0.6.91-0ubuntu3    an application for mastering audio CD
ii  sessreg                                1.0.0-0ubuntu2    X Display Manager session registration utili
ii  sgml-base                              1.26    SGML infrastructure and SGML catalog file su
ii  sgml-data                              2.0.3    common SGML and XML data
ii  shared-mime-info                       0.17-0ubuntu11    FreeDesktop.org shared MIME database and spe
ii  skim                                   1.4.4-0ubuntu7    smart common input method platform for KDE
ii  skype                                  1.3.0.30-1    Free Internet Telephony - The whole world ca
ii  slocate                                3.0.beta.r3-1    Secure replacement of findutil's locate
ii  smartdimmer                            0.1-2    Change LCD brightness on Geforce 6200Go card
ii  smbclient                              3.0.22-1ubuntu3.1    a LanManager-like simple client for Unix
ii  smproxy                                1.0.1-0ubuntu1    X client - smproxy
ii  sound-juicer                           2.14.4-0ubuntu1    GNOME 2 CD Ripper
ii  speedcrunch                            0.6beta2-0ubuntu1    high precision calculator
ii  ssh-askpass-gnome                      4.2p1-7ubuntu3    under X, asks user for a passphrase for ssh-
ii  strace                                 4.5.12-1ubuntu1    A system call tracer
ii  streamtuner                            0.99.99-5ubuntu6    A GUI audio stream directory browser
ii  sudo                                   1.6.8p12-1ubuntu6    Provide limited super user privileges to spe
ii  synaptic                               0.57.8ubuntu11    Graphical package manager
ii  sysklogd                               1.4.1-17ubuntu7    System Logging Daemon
ii  system-tools-backends                  1.4.2-0ubuntu5    System Tools to manage computer configuratio
ii  sysv-rc                                2.86.ds1-6ubuntu32    Standard boot mechanism using symlinks in /e
ii  sysvinit                               2.86.ds1-6ubuntu32    System-V like init
ii  tangerine-icon-theme                   0.13-0ubuntu1    Tangerine Icon theme
ii  tango-icon-theme                       0.7.2-0ubuntu3    Tango Icon theme
ii  tango-icon-theme-common                0.2-0ubuntu1    Tango Icon theme - common icons
ii  tar                                    1.15.1-2ubuntu2    GNU tar
ii  tcl8.4                                 8.4.12-0ubuntu1    Tcl (the Tool Command Language) v8.4 - run-t
ii  tcpd                                   7.6.dbs-8ubuntu1    Wietse Venema's TCP wrapper utilities
ii  tcpdump                                3.9.4-2    A powerful tool for network monitoring and d
ii  telnet                                 0.17-32    The telnet client
ii  thunderbird-locale-en-gb               1.5.0.2ubuntu1-3    Thunderbird English language/region package
ii  thunderbird-locale-zh-cn               1.5.0.2ubuntu1-3    Thunderbird Chinese language/region package
ii  time                                   1.7-21    The GNU time program for measuring cpu resou
ii  tk8.4                                  8.4.12-0ubuntu1    Tk toolkit for Tcl and X11, v8.4 - run-time
ii  toshset                                1.71-1    Access much of the Toshiba laptop hardware i
ii  totem                                  1.4.3-0ubuntu1    A simple media player for the Gnome desktop
ii  totem-gstreamer                        1.4.3-0ubuntu1    A simple media player for the Gnome desktop
ii  tsclient                               0.140-3ubuntu1    front-end for viewing of remote desktops in
ii  ttf-arabeyes                           1.1-4    Arabeyes GPL TrueType Arabic fonts
ii  ttf-arphic-ukai                        0.1.20060108-0.dot.1ubuntu1    "AR PL ZenKai Uni" Chinese Unicode TrueType
ii  ttf-arphic-uming                       0.1.20060513-1    "AR PL ShanHeiSun Uni" Chinese Unicode TrueT
ii  ttf-baekmuk                            2.2-1ubuntu1    Baekmuk series TrueType fonts
ii  ttf-bengali-fonts                      0.4.7    Free TrueType fonts for the Bengali language
ii  ttf-bitstream-vera                     1.10-3ubuntu1    The Bitstream Vera family of free TrueType f
ii  ttf-dejavu                             2.5-0ubuntu2    Bitstream Vera fonts with additional charact
ii  ttf-devanagari-fonts                   0.4.7    Free TrueType fonts for languages using the
ii  ttf-freefont                           20060126b-2ubuntu3    Freefont Serif, Sans and Mono Truetype fonts
ii  ttf-gentium                            1.02-1ubuntu1    Gentium TrueType font
ii  ttf-gujarati-fonts                     0.4.7    Free TrueType fonts for the Gujarati languag
ii  ttf-indic-fonts                        0.4.7    Metapackage for free Indian language fonts
ii  ttf-kannada-fonts                      0.4.7    Free TrueType fonts for the Kannada language
ii  ttf-kochi-gothic                       1.0.20030809-3    Kochi Subst Gothic Japanese TrueType font wi
ii  ttf-kochi-mincho                       1.0.20030809-3    Kochi Subst Mincho Japanese TrueType font wi
ii  ttf-lao                                0.0.20060226-1build1    TrueType font for Lao language
ii  ttf-malayalam-fonts                    0.4.7    Free TrueType fonts for the Malayalam langua
ii  ttf-mgopen                             1.1-2    Magenta Open Truetype fonts
ii  ttf-opensymbol                         2.0.2-2ubuntu12.1    The OpenSymbol TrueType font
ii  ttf-oriya-fonts                        0.4.7    Free TrueType fonts for the Oriya language
ii  ttf-punjabi-fonts                      0.4.7    Free TrueType fonts for the Punjabi language
ii  ttf-tamil-fonts                        0.4.7    Free TrueType fonts for the Tamil language
ii  ttf-telugu-fonts                       0.4.7    Free TrueType fonts for the Telugu language
ii  ttf-thai-tlwg                          0.4.4-0ubuntu1    Thai fonts in TrueType format
ii  ubuntu-artwork                         28    Ubuntu themes and artwork
ii  ubuntu-base                            0.119    The Ubuntu base system (transitional package
ii  ubuntu-desktop                         0.119    The Ubuntu desktop system
ii  ubuntu-docs                            6.06.2    The Ubuntu Documentation Project
ii  ubuntu-keyring                         2005.01.12.1    GnuPG keys of the Ubuntu archive
ii  ubuntu-minimal                         0.119    Minimal core of Ubuntu
ii  ubuntu-sounds                          0.3    Ubuntu's GNOME audio theme
ii  ubuntu-standard                        0.119    The Ubuntu standard system
ii  ucf                                    2.004    Update Configuration File: preserves user ch
ii  udev                                   079-0ubuntu34    rule-based device node and kernel event mana
ii  unattended-upgrades                    0.1ubuntu3    Install security upgrades automatically
ii  unzip                                  5.52-6ubuntu4    De-archiver for .zip files
ii  update-manager                         0.42.2ubuntu22    GNOME application that manages apt updates
ii  update-notifier                        0.42.6    Daemon which notifies about package updates
ii  usbutils                               0.71+cvs20051029-4ubuntu1    USB console utilities
ii  usplash                                0.2-4    Userspace bootsplash utility
ii  util-linux                             2.12r-4ubuntu6    Miscellaneous system utilities
ii  vbetool                                0.6-1    run real-mode video BIOS code to alter hardw
ii  viewres                                1.0.1-0ubuntu1    X client - viewres
ii  vim                                    6.4-006+2ubuntu6    Vi IMproved - enhanced vi editor
ii  vim-common                             6.4-006+2ubuntu6    Vi IMproved - Common files
ii  vim-runtime                            6.4-006+2ubuntu6    Vi IMproved - Runtime files
ii  vino                                   2.13.5-0ubuntu6    VNC server for GNOME
ii  vnc-common                             3.3.7-8ubuntu2    Virtual network computing server software
ii  vorbis-tools                           1.1.1-3    several Ogg Vorbis tools
ii  w3m                                    0.5.1-4ubuntu2    WWW browsable pager with excellent tables/fr
ii  wamerican                              6-2    American English dictionary words for /usr/s
ii  wbritish                               6-2    British English dictionary words for /usr/sh
ii  wget                                   1.10.2-1ubuntu1    retrieves files from the web
ii  whiptail                               0.51.6-31ubuntu1    Displays user-friendly dialog boxes from she
ii  whois                                  4.7.11ubuntu1    the GNU whois client
ii  wireless-tools                         27+28pre13-1ubuntu2    Tools for manipulating Linux Wireless Extens
ii  wlassistant                            0.5.5-0ubuntu2    User friendly KDE frontend for wireless netw
ii  wpasupplicant                          0.4.8-3ubuntu1.1    Client support for WPA and WPA2 (IEEE 802.11
ii  wvdial                                 1.55-1ubuntu3    PPP dialer with built-in intelligence
ii  x-ttcidfont-conf                       20ubuntu1    Configure TrueType and CID fonts for X
ii  x-window-system-core                   7.0.0-0ubuntu45    X Window System core components
ii  x11-common                             7.0.0-0ubuntu45    X Window System (X.Org) infrastructure
ii  x11perf                                1.0.1-0ubuntu1    X client - x11perf
ii  xauth                                  1.0.1-0ubuntu1    X authentication utility
ii  xbase-clients                          7.0.0-0ubuntu45    X Window System client utility transitional
ii  xbiff                                  1.0.1-0ubuntu1    X client - xbiff
ii  xcalc                                  1.0.1-0ubuntu1    X client - xcalc
ii  xclipboard                             1.0.1-0ubuntu1    X client - xclipboard
ii  xclock                                 1.0.1-0ubuntu1    X client - xclock
ii  xconsole                               1.0.1-0ubuntu1    X client - xconsole
ii  xcursor-themes                         1.0.1-0ubuntu3    Base X cursor themes
ii  xcursorgen                             1.0.0-0ubuntu1    X cursor generation
ii  xditview                               1.0.1-0ubuntu1    X client - xditview
ii  xdpyinfo                               1.0.1-0ubuntu1    X display information
ii  xdriinfo                               1.0.0-0ubuntu2    X DRI information utility
ii  xev                                    1.0.1-0ubuntu1    X client - xev
ii  xeyes                                  1.0.1-0ubuntu1    X client - xeyes
ii  xf86dga                                1.0.1-0ubuntu1    X client - xf86dga
ii  xfd                                    1.0.1-0ubuntu1    X client - xfd
ii  xfonts-100dpi                          6.8.2.1-5    100 dpi fonts for X
ii  xfonts-75dpi                           6.8.2.1-5    75 dpi fonts for X
ii  xfonts-base                            6.8.2.1-5    standard fonts for X
ii  xfonts-intl-arabic                     1.2.1-4ubuntu1    International fonts for X -- Arabic
ii  xfonts-scalable                        6.8.2.1-5    scalable fonts for X
ii  xfonts-utils                           6.8.2.1-5    utilities for X font packages
ii  xfontsel                               1.0.1-0ubuntu1    X client - xfontsel
ii  xfsprogs                               2.7.7-1    Utilities for managing the XFS filesystem
ii  xgamma                                 1.0.1-0ubuntu1    X client - xgamma
ii  xgc                                    1.0.1-0ubuntu1    X client - xgc
ii  xhost                                  1.0.0-0ubuntu1    X authentication manipulation
ii  xinit                                  1.0.1-0ubuntu3    X server initialisation tool
ii  xkbutils                               1.0.1-0ubuntu1    X11 XKB utilities
ii  xkeyboard-config                       0.8-7    XKB data
ii  xkill                                  1.0.1-0ubuntu1    X client - xkill
ii  xload                                  1.0.1-0ubuntu1    X client - xload
ii  xlogo                                  1.0.1-0ubuntu1    X client - xlogo
ii  xlsatoms                               1.0.1-0ubuntu1    X client - xlsatoms
ii  xlsclients                             1.0.1-0ubuntu1    X client - xlsclients
ii  xlsfonts                               1.0.1-0ubuntu1    X client - xlsfonts
ii  xmag                                   1.0.1-0ubuntu1    X client - xmag
ii  xman                                   1.0.1-0ubuntu2    X client - xman
ii  xmessage                               1.0.1-0ubuntu1    X client - xmessage
ii  xml-core                               0.09    XML infrastructure and XML catalog file supp
ii  xmms                                   1.2.10+cvs20050809-4ubuntu5    Versatile X audio player
ii  xmodmap                                1.0.0-0ubuntu1    X input map modification
ii  xmore                                  1.0.1-0ubuntu1    X client - xmore
ii  xpmutils                               3.5.4.2-0ubuntu3    X11 pixmap utilities
ii  xprop                                  1.0.1-0ubuntu1    X window property utility
ii  xrandr                                 1.0.1-0ubuntu1    X Rotation, Reflection and Resize utility
ii  xrdb                                   1.0.1-0ubuntu2    X resource modification
ii  xrefresh                               1.0.1-0ubuntu1    X client - xrefresh
ii  xresprobe                              0.4.23    X Resolution Probe
ii  xrgb                                   1.0.0-0ubuntu2    X RGB database and utilities
ii  xsane                                  0.97-4ubuntu6    GTK+-based X11 frontend for SANE (Scanner Ac
ii  xsane-common                           0.97-4ubuntu6    GTK+-based X11 frontend for SANE (Scanner Ac
ii  xscreensaver-data                      4.23-4ubuntu8    data files to be shared among screensaver fr
ii  xscreensaver-gl                        4.23-4ubuntu8    GL(Mesa) screen hacks for xscreensaver
ii  xserver-xorg                           7.0.0-0ubuntu45    the X.Org X server
ii  xserver-xorg-core                      1.0.2-0ubuntu10.1    X.Org X server -- core server
ii  xserver-xorg-driver-all                7.0.0-0ubuntu45    the X.Org X server -- output driver metapack
ii  xserver-xorg-driver-apm                1.0.1.5-0ubuntu1    X.Org X server -- APM display driver
ii  xserver-xorg-driver-ark                0.5.0.5-0ubuntu1    X.Org X server -- ark display driver
ii  xserver-xorg-driver-ati                6.5.7.3-0ubuntu7    X.Org X server -- ATI display driver
ii  xserver-xorg-driver-chips              1.0.1.3-0ubuntu1    X.Org X server -- Chips display driver
ii  xserver-xorg-driver-cirrus             1.0.0.5-0ubuntu1    X.Org X server -- Cirrus display driver
ii  xserver-xorg-driver-cyrix              1.0.0.5-0ubuntu1    X.Org X server -- Cyrix display driver
ii  xserver-xorg-driver-dummy              0.1.0.5-0ubuntu1    X.Org X server -- dummy display driver
ii  xserver-xorg-driver-fbdev              0.1.0.5-0ubuntu1    X.Org X server -- fbdev display driver
ii  xserver-xorg-driver-glint              1.0.1.3-0ubuntu1    X.Org X server -- Glint display driver
ii  xserver-xorg-driver-i128               1.1.0.5-0ubuntu1    X.Org X server -- i128 display driver
ii  xserver-xorg-driver-i740               1.0.0.5-0ubuntu1    X.Org X server -- i740 display driver
ii  xserver-xorg-driver-i810               1.4.1.3-0ubuntu6    X.Org X server -- Intel i8xx, i9xx display d
ii  xserver-xorg-driver-imstt              1.0.0.5-0ubuntu1    X.Org X server -- IMSTT display driver
ii  xserver-xorg-driver-mga                1.2.1.3-0ubuntu1    X.Org X server -- MGA display driver
ii  xserver-xorg-driver-neomagic           1.0.0.5-0ubuntu1    X.Org X server -- Neomagic display driver
ii  xserver-xorg-driver-newport            0.1.4.1-0ubuntu1    X.Org X server -- Newport display driver
ii  xserver-xorg-driver-nsc                2.7.6.5-0ubuntu1    X.Org X server -- NSC display driver
ii  xserver-xorg-driver-nv                 1.0.1.5-0ubuntu4    X.Org X server -- NV display driver
ii  xserver-xorg-driver-rendition          4.0.1.3-0ubuntu1    X.Org X server -- Rendition display driver
ii  xserver-xorg-driver-s3                 0.3.5.4-0ubuntu2    X.Org X server -- legacy S3 display driver
ii  xserver-xorg-driver-s3virge            1.8.6.5-0ubuntu1    X.Org X server -- S3 ViRGE display driver
ii  xserver-xorg-driver-savage             2.0.2.3-0ubuntu1    X.Org X server -- Savage display driver
ii  xserver-xorg-driver-siliconmotion      1.3.1.5-0ubuntu1    X.Org X server -- SiliconMotion display driv
ii  xserver-xorg-driver-sis                0.8.1.3-0ubuntu1    X.Org X server -- SiS display driver
ii  xserver-xorg-driver-sisusb             0.7.1.3-0ubuntu1    X.Org X server -- SiS USB display driver
ii  xserver-xorg-driver-tdfx               1.1.1.3-0ubuntu1    X.Org X server -- tdfx display driver
ii  xserver-xorg-driver-tga                1.0.0.5-0ubuntu1    X.Org X server -- TGA display driver
ii  xserver-xorg-driver-trident            1.0.1.2-0ubuntu1    X.Org X server -- Trident display driver
ii  xserver-xorg-driver-tseng              1.0.0.5-0ubuntu1    X.Org X server -- Tseng display driver
ii  xserver-xorg-driver-v4l                0.0.1.5-0ubuntu1    X.Org X server -- Video4Linux driver
ii  xserver-xorg-driver-vesa               1.0.1.3-0ubuntu1    X.Org X server -- VESA display driver
ii  xserver-xorg-driver-vga                4.0.0.5-0ubuntu1    X.Org X server -- VGA display driver
ii  xserver-xorg-driver-via                0.1.33.2-0ubuntu4    X.Org X server -- VIA display driver
ii  xserver-xorg-driver-vmware             10.11.1.3-0ubuntu1    X.Org X server -- VMware display driver
ii  xserver-xorg-driver-voodoo             1.0.0.5-0ubuntu1    X.Org X server -- Voodoo display driver
ii  xserver-xorg-input-all                 7.0.0-0ubuntu45    the X.Org X server -- input driver metapacka
ii  xserver-xorg-input-elographics         1.0.0.5-0ubuntu1    X.Org X server -- ELOGraphics input driver
ii  xserver-xorg-input-evdev               1.1.2-0ubuntu3    X.Org X server -- evdev input driver
ii  xserver-xorg-input-kbd                 1.0.1.3-0ubuntu3    X.Org X server -- keyboard input driver
ii  xserver-xorg-input-mouse               1.0.3.1+cvs.20060109-0ubuntu1.1    X.Org X server -- mouse input driver
ii  xserver-xorg-input-synaptics           0.14.3+seriouslythistime-0ubuntu3    Synaptics TouchPad driver for X.Org server
ii  xserver-xorg-input-wacom               0.7.2-0ubuntu6    X.Org X server -- Wacom input driver
ii  xset                                   1.0.0-0ubuntu1    X server option modification
ii  xsetmode                               1.0.0-0ubuntu1    X Input Device modification
ii  xsetpointer                            1.0.0-0ubuntu1    X Input Device modification
ii  xsetroot                               1.0.1-0ubuntu1    X client - xsetroot
ii  xsltproc                               1.1.15-1ubuntu1    XSLT command line processor
ii  xsm                                    1.0.1-0ubuntu1    X client - xsm
ii  xstdcmap                               1.0.1-0ubuntu1    X client - xstdcmap
ii  xterm                                  208-3.1ubuntu3    X terminal emulator
ii  xtrap                                  1.0.1-0ubuntu2    X client - xtrap
ii  xutils                                 7.0.0-0ubuntu45    X Window System miscellaneous utility transi
ii  xvidtune                               1.0.1-0ubuntu1    X client - xvidtune
ii  xvinfo                                 1.0.1-0ubuntu1    XVideo information
ii  xvncviewer                             3.3.7-8ubuntu2    Virtual network computing client software fo
ii  xwd                                    1.0.1-0ubuntu1    X client - xwd
ii  xwininfo                               1.0.1-0ubuntu1    X client - xwininfo
ii  xwud                                   1.0.1-0ubuntu1    X client - xwud
ii  yelp                                   2.14.3-0ubuntu1    Help browser for GNOME 2
ii  zenity                                 2.14.3-0ubuntu1    Display graphical dialog boxes from shell sc
ii  zip                                    2.31-3    Archiver for .zip files
ii  zlib1g                                 1.2.3-6ubuntu4    compression library - runtime
ai@ai-laptop:~$ dpkg -l | grep glib
ii  libavahi-glib1                         0.6.10-0ubuntu3    Avahi glib integration library
ii  libdbus-glib-1-2                       0.60-6ubuntu8    simple interprocess messaging system (GLib-b
ii  libglib-perl                           1.103-1    Perl interface to the GLib and GObject libra
ii  libglib1.2                             1.2.10-10.1build1    The GLib library of C routines
ii  libglib2.0-0                           2.10.3-0ubuntu1    The GLib library of C routines
ii  libglib2.0-data                        2.10.3-0ubuntu1    Common files for GLib library
ii  libpoppler1-glib                       0.5.1-0ubuntu7    PDF rendering library (GLib-based shared lib

---

### Post by AiBo on 2006-08-03
oh yeah I have kde and gnome installed...

dpkg -l | grep glib gives me the following:


remote incremental backup
ii  readahead                              0.20050517.0220-0ubuntu3    read files into the page cache
ii  readline-common                        5.1-7build1    GNU readline and history libraries, common f
ii  reiser4progs                           1.0.5-1    administration utilities for the Reiser4 fil
ii  reiserfsprogs                          3.6.19-1    User-level tools for ReiserFS filesystems
ii  reportbug                              3.18ubuntu1    reports bugs in the Debian distribution
ii  rhythmbox                              0.9.3.1-0ubuntu9    music player and organizer for GNOME
ii  rss-glx                                0.8.0-1ubuntu7    Really Slick Screensavers GLX Port
ii  rsync                                  2.6.6-1ubuntu2    fast remote file copy program (like rcp)
ii  samba-common                           3.0.22-1ubuntu3.1    Samba common files used by both the server a
ii  scim                                   1.4.4-1ubuntu12    smart common input method platform
ii  scim-chewing                           0.2.1-2ubuntu4    Chewing IM engine module for SCIM
ii  scim-gtk2-immodule                     1.4.4-1ubuntu12    GTK+2 input method module with SCIM as backe
ii  scim-modules-socket                    1.4.4-1ubuntu12    socket modules for SCIM platform
ii  scim-modules-table                     0.5.6-1build1    generic tables IM engine module for SCIM pla
ii  scim-pinyin                            0.5.91-0ubuntu3    smart pinyin IM engine for SCIM platform
ii  scim-qtimm                             0.9.4-0ubuntu4    SCIM context plugin for qt-immodule
ii  scim-tables-zh                         0.5.6-1build1    Chinese input method data tables for SCIM pl
ii  screen                                 4.0.2-4.1ubuntu5    a terminal multiplexor with VT100/ANSI termi
ii  screensaver-default-images             0.2-1    Wallpapers for image processing screensavers
ii  scrollkeeper                           0.3.14-11ubuntu6    A free electronic cataloging system for docu
ii  sed                                    4.1.4-5    The GNU sed stream editor
ii  serpentine                             0.6.91-0ubuntu3    an application for mastering audio CD
ii  sessreg                                1.0.0-0ubuntu2    X Display Manager session registration utili
ii  sgml-base                              1.26    SGML infrastructure and SGML catalog file su
ii  sgml-data                              2.0.3    common SGML and XML data
ii  shared-mime-info                       0.17-0ubuntu11    FreeDesktop.org shared MIME database and spe
ii  skim                                   1.4.4-0ubuntu7    smart common input method platform for KDE
ii  skype                                  1.3.0.30-1    Free Internet Telephony - The whole world ca
ii  slocate                                3.0.beta.r3-1    Secure replacement of findutil's locate
ii  smartdimmer                            0.1-2    Change LCD brightness on Geforce 6200Go card
ii  smbclient                              3.0.22-1ubuntu3.1    a LanManager-like simple client for Unix
ii  smproxy                                1.0.1-0ubuntu1    X client - smproxy
ii  sound-juicer                           2.14.4-0ubuntu1    GNOME 2 CD Ripper
ii  speedcrunch                            0.6beta2-0ubuntu1    high precision calculator
ii  ssh-askpass-gnome                      4.2p1-7ubuntu3    under X, asks user for a passphrase for ssh-
ii  strace                                 4.5.12-1ubuntu1    A system call tracer
ii  streamtuner                            0.99.99-5ubuntu6    A GUI audio stream directory browser
ii  sudo                                   1.6.8p12-1ubuntu6    Provide limited super user privileges to spe
ii  synaptic                               0.57.8ubuntu11    Graphical package manager
ii  sysklogd                               1.4.1-17ubuntu7    System Logging Daemon
ii  system-tools-backends                  1.4.2-0ubuntu5    System Tools to manage computer configuratio
ii  sysv-rc                                2.86.ds1-6ubuntu32    Standard boot mechanism using symlinks in /e
ii  sysvinit                               2.86.ds1-6ubuntu32    System-V like init
ii  tangerine-icon-theme                   0.13-0ubuntu1    Tangerine Icon theme
ii  tango-icon-theme                       0.7.2-0ubuntu3    Tango Icon theme
ii  tango-icon-theme-common                0.2-0ubuntu1    Tango Icon theme - common icons
ii  tar                                    1.15.1-2ubuntu2    GNU tar
ii  tcl8.4                                 8.4.12-0ubuntu1    Tcl (the Tool Command Language) v8.4 - run-t
ii  tcpd                                   7.6.dbs-8ubuntu1    Wietse Venema's TCP wrapper utilities
ii  tcpdump                                3.9.4-2    A powerful tool for network monitoring and d
ii  telnet                                 0.17-32    The telnet client
ii  thunderbird-locale-en-gb               1.5.0.2ubuntu1-3    Thunderbird English language/region package
ii  thunderbird-locale-zh-cn               1.5.0.2ubuntu1-3    Thunderbird Chinese language/region package
ii  time                                   1.7-21    The GNU time program for measuring cpu resou
ii  tk8.4                                  8.4.12-0ubuntu1    Tk toolkit for Tcl and X11, v8.4 - run-time
ii  toshset                                1.71-1    Access much of the Toshiba laptop hardware i
ii  totem                                  1.4.3-0ubuntu1    A simple media player for the Gnome desktop
ii  totem-gstreamer                        1.4.3-0ubuntu1    A simple media player for the Gnome desktop
ii  tsclient                               0.140-3ubuntu1    front-end for viewing of remote desktops in
ii  ttf-arabeyes                           1.1-4    Arabeyes GPL TrueType Arabic fonts
ii  ttf-arphic-ukai                        0.1.20060108-0.dot.1ubuntu1    "AR PL ZenKai Uni" Chinese Unicode TrueType
ii  ttf-arphic-uming                       0.1.20060513-1    "AR PL ShanHeiSun Uni" Chinese Unicode TrueT
ii  ttf-baekmuk                            2.2-1ubuntu1    Baekmuk series TrueType fonts
ii  ttf-bengali-fonts                      0.4.7    Free TrueType fonts for the Bengali language
ii  ttf-bitstream-vera                     1.10-3ubuntu1    The Bitstream Vera family of free TrueType f
ii  ttf-dejavu                             2.5-0ubuntu2    Bitstream Vera fonts with additional charact
ii  ttf-devanagari-fonts                   0.4.7    Free TrueType fonts for languages using the
ii  ttf-freefont                           20060126b-2ubuntu3    Freefont Serif, Sans and Mono Truetype fonts
ii  ttf-gentium                            1.02-1ubuntu1    Gentium TrueType font
ii  ttf-gujarati-fonts                     0.4.7    Free TrueType fonts for the Gujarati languag
ii  ttf-indic-fonts                        0.4.7    Metapackage for free Indian language fonts
ii  ttf-kannada-fonts                      0.4.7    Free TrueType fonts for the Kannada language
ii  ttf-kochi-gothic                       1.0.20030809-3    Kochi Subst Gothic Japanese TrueType font wi
ii  ttf-kochi-mincho                       1.0.20030809-3    Kochi Subst Mincho Japanese TrueType font wi
ii  ttf-lao                                0.0.20060226-1build1    TrueType font for Lao language
ii  ttf-malayalam-fonts                    0.4.7    Free TrueType fonts for the Malayalam langua
ii  ttf-mgopen                             1.1-2    Magenta Open Truetype fonts
ii  ttf-opensymbol                         2.0.2-2ubuntu12.1    The OpenSymbol TrueType font
ii  ttf-oriya-fonts                        0.4.7    Free TrueType fonts for the Oriya language
ii  ttf-punjabi-fonts                      0.4.7    Free TrueType fonts for the Punjabi language
ii  ttf-tamil-fonts                        0.4.7    Free TrueType fonts for the Tamil language
ii  ttf-telugu-fonts                       0.4.7    Free TrueType fonts for the Telugu language
ii  ttf-thai-tlwg                          0.4.4-0ubuntu1    Thai fonts in TrueType format
ii  ubuntu-artwork                         28    Ubuntu themes and artwork
ii  ubuntu-base                            0.119    The Ubuntu base system (transitional package
ii  ubuntu-desktop                         0.119    The Ubuntu desktop system
ii  ubuntu-docs                            6.06.2    The Ubuntu Documentation Project
ii  ubuntu-keyring                         2005.01.12.1    GnuPG keys of the Ubuntu archive
ii  ubuntu-minimal                         0.119    Minimal core of Ubuntu
ii  ubuntu-sounds                          0.3    Ubuntu's GNOME audio theme
ii  ubuntu-standard                        0.119    The Ubuntu standard system
ii  ucf                                    2.004    Update Configuration File: preserves user ch
ii  udev                                   079-0ubuntu34    rule-based device node and kernel event mana
ii  unattended-upgrades                    0.1ubuntu3    Install security upgrades automatically
ii  unzip                                  5.52-6ubuntu4    De-archiver for .zip files
ii  update-manager                         0.42.2ubuntu22    GNOME application that manages apt updates
ii  update-notifier                        0.42.6    Daemon which notifies about package updates
ii  usbutils                               0.71+cvs20051029-4ubuntu1    USB console utilities
ii  usplash                                0.2-4    Userspace bootsplash utility
ii  util-linux                             2.12r-4ubuntu6    Miscellaneous system utilities
ii  vbetool                                0.6-1    run real-mode video BIOS code to alter hardw
ii  viewres                                1.0.1-0ubuntu1    X client - viewres
ii  vim                                    6.4-006+2ubuntu6    Vi IMproved - enhanced vi editor
ii  vim-common                             6.4-006+2ubuntu6    Vi IMproved - Common files
ii  vim-runtime                            6.4-006+2ubuntu6    Vi IMproved - Runtime files
ii  vino                                   2.13.5-0ubuntu6    VNC server for GNOME
ii  vnc-common                             3.3.7-8ubuntu2    Virtual network computing server software
ii  vorbis-tools                           1.1.1-3    several Ogg Vorbis tools
ii  w3m                                    0.5.1-4ubuntu2    WWW browsable pager with excellent tables/fr
ii  wamerican                              6-2    American English dictionary words for /usr/s
ii  wbritish                               6-2    British English dictionary words for /usr/sh
ii  wget                                   1.10.2-1ubuntu1    retrieves files from the web
ii  whiptail                               0.51.6-31ubuntu1    Displays user-friendly dialog boxes from she
ii  whois                                  4.7.11ubuntu1    the GNU whois client
ii  wireless-tools                         27+28pre13-1ubuntu2    Tools for manipulating Linux Wireless Extens
ii  wlassistant                            0.5.5-0ubuntu2    User friendly KDE frontend for wireless netw
ii  wpasupplicant                          0.4.8-3ubuntu1.1    Client support for WPA and WPA2 (IEEE 802.11
ii  wvdial                                 1.55-1ubuntu3    PPP dialer with built-in intelligence
ii  x-ttcidfont-conf                       20ubuntu1    Configure TrueType and CID fonts for X
ii  x-window-system-core                   7.0.0-0ubuntu45    X Window System core components
ii  x11-common                             7.0.0-0ubuntu45    X Window System (X.Org) infrastructure
ii  x11perf                                1.0.1-0ubuntu1    X client - x11perf
ii  xauth                                  1.0.1-0ubuntu1    X authentication utility
ii  xbase-clients                          7.0.0-0ubuntu45    X Window System client utility transitional
ii  xbiff                                  1.0.1-0ubuntu1    X client - xbiff
ii  xcalc                                  1.0.1-0ubuntu1    X client - xcalc
ii  xclipboard                             1.0.1-0ubuntu1    X client - xclipboard
ii  xclock                                 1.0.1-0ubuntu1    X client - xclock
ii  xconsole                               1.0.1-0ubuntu1    X client - xconsole
ii  xcursor-themes                         1.0.1-0ubuntu3    Base X cursor themes
ii  xcursorgen                             1.0.0-0ubuntu1    X cursor generation
ii  xditview                               1.0.1-0ubuntu1    X client - xditview
ii  xdpyinfo                               1.0.1-0ubuntu1    X display information
ii  xdriinfo                               1.0.0-0ubuntu2    X DRI information utility
ii  xev                                    1.0.1-0ubuntu1    X client - xev
ii  xeyes                                  1.0.1-0ubuntu1    X client - xeyes
ii  xf86dga                                1.0.1-0ubuntu1    X client - xf86dga
ii  xfd                                    1.0.1-0ubuntu1    X client - xfd
ii  xfonts-100dpi                          6.8.2.1-5    100 dpi fonts for X
ii  xfonts-75dpi                           6.8.2.1-5    75 dpi fonts for X
ii  xfonts-base                            6.8.2.1-5    standard fonts for X
ii  xfonts-intl-arabic                     1.2.1-4ubuntu1    International fonts for X -- Arabic
ii  xfonts-scalable                        6.8.2.1-5    scalable fonts for X
ii  xfonts-utils                           6.8.2.1-5    utilities for X font packages
ii  xfontsel                               1.0.1-0ubuntu1    X client - xfontsel
ii  xfsprogs                               2.7.7-1    Utilities for managing the XFS filesystem
ii  xgamma                                 1.0.1-0ubuntu1    X client - xgamma
ii  xgc                                    1.0.1-0ubuntu1    X client - xgc
ii  xhost                                  1.0.0-0ubuntu1    X authentication manipulation
ii  xinit                                  1.0.1-0ubuntu3    X server initialisation tool
ii  xkbutils                               1.0.1-0ubuntu1    X11 XKB utilities
ii  xkeyboard-config                       0.8-7    XKB data
ii  xkill                                  1.0.1-0ubuntu1    X client - xkill
ii  xload                                  1.0.1-0ubuntu1    X client - xload
ii  xlogo                                  1.0.1-0ubuntu1    X client - xlogo
ii  xlsatoms                               1.0.1-0ubuntu1    X client - xlsatoms
ii  xlsclients                             1.0.1-0ubuntu1    X client - xlsclients
ii  xlsfonts                               1.0.1-0ubuntu1    X client - xlsfonts
ii  xmag                                   1.0.1-0ubuntu1    X client - xmag
ii  xman                                   1.0.1-0ubuntu2    X client - xman
ii  xmessage                               1.0.1-0ubuntu1    X client - xmessage
ii  xml-core                               0.09    XML infrastructure and XML catalog file supp
ii  xmms                                   1.2.10+cvs20050809-4ubuntu5    Versatile X audio player
ii  xmodmap                                1.0.0-0ubuntu1    X input map modification
ii  xmore                                  1.0.1-0ubuntu1    X client - xmore
ii  xpmutils                               3.5.4.2-0ubuntu3    X11 pixmap utilities
ii  xprop                                  1.0.1-0ubuntu1    X window property utility
ii  xrandr                                 1.0.1-0ubuntu1    X Rotation, Reflection and Resize utility
ii  xrdb                                   1.0.1-0ubuntu2    X resource modification
ii  xrefresh                               1.0.1-0ubuntu1    X client - xrefresh
ii  xresprobe                              0.4.23    X Resolution Probe
ii  xrgb                                   1.0.0-0ubuntu2    X RGB database and utilities
ii  xsane                                  0.97-4ubuntu6    GTK+-based X11 frontend for SANE (Scanner Ac
ii  xsane-common                           0.97-4ubuntu6    GTK+-based X11 frontend for SANE (Scanner Ac
ii  xscreensaver-data                      4.23-4ubuntu8    data files to be shared among screensaver fr
ii  xscreensaver-gl                        4.23-4ubuntu8    GL(Mesa) screen hacks for xscreensaver
ii  xserver-xorg                           7.0.0-0ubuntu45    the X.Org X server
ii  xserver-xorg-core                      1.0.2-0ubuntu10.1    X.Org X server -- core server
ii  xserver-xorg-driver-all                7.0.0-0ubuntu45    the X.Org X server -- output driver metapack
ii  xserver-xorg-driver-apm                1.0.1.5-0ubuntu1    X.Org X server -- APM display driver
ii  xserver-xorg-driver-ark                0.5.0.5-0ubuntu1    X.Org X server -- ark display driver
ii  xserver-xorg-driver-ati                6.5.7.3-0ubuntu7    X.Org X server -- ATI display driver
ii  xserver-xorg-driver-chips              1.0.1.3-0ubuntu1    X.Org X server -- Chips display driver
ii  xserver-xorg-driver-cirrus             1.0.0.5-0ubuntu1    X.Org X server -- Cirrus display driver
ii  xserver-xorg-driver-cyrix              1.0.0.5-0ubuntu1    X.Org X server -- Cyrix display driver
ii  xserver-xorg-driver-dummy              0.1.0.5-0ubuntu1    X.Org X server -- dummy display driver
ii  xserver-xorg-driver-fbdev              0.1.0.5-0ubuntu1    X.Org X server -- fbdev display driver
ii  xserver-xorg-driver-glint              1.0.1.3-0ubuntu1    X.Org X server -- Glint display driver
ii  xserver-xorg-driver-i128               1.1.0.5-0ubuntu1    X.Org X server -- i128 display driver
ii  xserver-xorg-driver-i740               1.0.0.5-0ubuntu1    X.Org X server -- i740 display driver
ii  xserver-xorg-driver-i810               1.4.1.3-0ubuntu6    X.Org X server -- Intel i8xx, i9xx display d
ii  xserver-xorg-driver-imstt              1.0.0.5-0ubuntu1    X.Org X server -- IMSTT display driver
ii  xserver-xorg-driver-mga                1.2.1.3-0ubuntu1    X.Org X server -- MGA display driver
ii  xserver-xorg-driver-neomagic           1.0.0.5-0ubuntu1    X.Org X server -- Neomagic display driver
ii  xserver-xorg-driver-newport            0.1.4.1-0ubuntu1    X.Org X server -- Newport display driver
ii  xserver-xorg-driver-nsc                2.7.6.5-0ubuntu1    X.Org X server -- NSC display driver
ii  xserver-xorg-driver-nv                 1.0.1.5-0ubuntu4    X.Org X server -- NV display driver
ii  xserver-xorg-driver-rendition          4.0.1.3-0ubuntu1    X.Org X server -- Rendition display driver
ii  xserver-xorg-driver-s3                 0.3.5.4-0ubuntu2    X.Org X server -- legacy S3 display driver
ii  xserver-xorg-driver-s3virge            1.8.6.5-0ubuntu1    X.Org X server -- S3 ViRGE display driver
ii  xserver-xorg-driver-savage             2.0.2.3-0ubuntu1    X.Org X server -- Savage display driver
ii  xserver-xorg-driver-siliconmotion      1.3.1.5-0ubuntu1    X.Org X server -- SiliconMotion display driv
ii  xserver-xorg-driver-sis                0.8.1.3-0ubuntu1    X.Org X server -- SiS display driver
ii  xserver-xorg-driver-sisusb             0.7.1.3-0ubuntu1    X.Org X server -- SiS USB display driver
ii  xserver-xorg-driver-tdfx               1.1.1.3-0ubuntu1    X.Org X server -- tdfx display driver
ii  xserver-xorg-driver-tga                1.0.0.5-0ubuntu1    X.Org X server -- TGA display driver
ii  xserver-xorg-driver-trident            1.0.1.2-0ubuntu1    X.Org X server -- Trident display driver
ii  xserver-xorg-driver-tseng              1.0.0.5-0ubuntu1    X.Org X server -- Tseng display driver
ii  xserver-xorg-driver-v4l                0.0.1.5-0ubuntu1    X.Org X server -- Video4Linux driver
ii  xserver-xorg-driver-vesa               1.0.1.3-0ubuntu1    X.Org X server -- VESA display driver
ii  xserver-xorg-driver-vga                4.0.0.5-0ubuntu1    X.Org X server -- VGA display driver
ii  xserver-xorg-driver-via                0.1.33.2-0ubuntu4    X.Org X server -- VIA display driver
ii  xserver-xorg-driver-vmware             10.11.1.3-0ubuntu1    X.Org X server -- VMware display driver
ii  xserver-xorg-driver-voodoo             1.0.0.5-0ubuntu1    X.Org X server -- Voodoo display driver
ii  xserver-xorg-input-all                 7.0.0-0ubuntu45    the X.Org X server -- input driver metapacka
ii  xserver-xorg-input-elographics         1.0.0.5-0ubuntu1    X.Org X server -- ELOGraphics input driver
ii  xserver-xorg-input-evdev               1.1.2-0ubuntu3    X.Org X server -- evdev input driver
ii  xserver-xorg-input-kbd                 1.0.1.3-0ubuntu3    X.Org X server -- keyboard input driver
ii  xserver-xorg-input-mouse               1.0.3.1+cvs.20060109-0ubuntu1.1    X.Org X server -- mouse input driver
ii  xserver-xorg-input-synaptics           0.14.3+seriouslythistime-0ubuntu3    Synaptics TouchPad driver for X.Org server
ii  xserver-xorg-input-wacom               0.7.2-0ubuntu6    X.Org X server -- Wacom input driver
ii  xset                                   1.0.0-0ubuntu1    X server option modification
ii  xsetmode                               1.0.0-0ubuntu1    X Input Device modification
ii  xsetpointer                            1.0.0-0ubuntu1    X Input Device modification
ii  xsetroot                               1.0.1-0ubuntu1    X client - xsetroot
ii  xsltproc                               1.1.15-1ubuntu1    XSLT command line processor
ii  xsm                                    1.0.1-0ubuntu1    X client - xsm
ii  xstdcmap                               1.0.1-0ubuntu1    X client - xstdcmap
ii  xterm                                  208-3.1ubuntu3    X terminal emulator
ii  xtrap                                  1.0.1-0ubuntu2    X client - xtrap
ii  xutils                                 7.0.0-0ubuntu45    X Window System miscellaneous utility transi
ii  xvidtune                               1.0.1-0ubuntu1    X client - xvidtune
ii  xvinfo                                 1.0.1-0ubuntu1    XVideo information
ii  xvncviewer                             3.3.7-8ubuntu2    Virtual network computing client software fo
ii  xwd                                    1.0.1-0ubuntu1    X client - xwd
ii  xwininfo                               1.0.1-0ubuntu1    X client - xwininfo
ii  xwud                                   1.0.1-0ubuntu1    X client - xwud
ii  yelp                                   2.14.3-0ubuntu1    Help browser for GNOME 2
ii  zenity                                 2.14.3-0ubuntu1    Display graphical dialog boxes from shell sc
ii  zip                                    2.31-3    Archiver for .zip files
ii  zlib1g                                 1.2.3-6ubuntu4    compression library - runtime
XX@XX-laptop:~$ dpkg -l | grep glib
ii  libavahi-glib1                         0.6.10-0ubuntu3    Avahi glib integration library
ii  libdbus-glib-1-2                       0.60-6ubuntu8    simple interprocess messaging system (GLib-b
ii  libglib-perl                           1.103-1    Perl interface to the GLib and GObject libra
ii  libglib1.2                             1.2.10-10.1build1    The GLib library of C routines
ii  libglib2.0-0                           2.10.3-0ubuntu1    The GLib library of C routines
ii  libglib2.0-data                        2.10.3-0ubuntu1    Common files for GLib library
ii  libpoppler1-glib                       0.5.1-0ubuntu7    PDF rendering library (GLib-based shared lib

---

### Post by raditzman on 2006-08-03
Hi.... It seems the problem maybe some kind of incompatability between SCIM stuff and skype, the glibc versions you're using are the same as mine.... I'm not a big expert on SCIM on glibc, but I'm sure that has to be it. Is there any alternative to SCIM? Or maybe you can go to /var/cache/apt/archives/ directory and open the .deb files that were installed when you installed SCIM, to see what files they installed... Because Skype is closed-source, and their release rate and determination to support Linux is very low, this kind of rare incompatabilities may take a long time to be solved. They 're not seriously supporting Linux. If I were you, i'd try openwengo, or something...

---

### Post by Matchless on 2006-08-06
Hi,
   This may not be your problem, but you can try it. I have had exactly the same issue with the mic in kubuntu dapper on Skype beta 1.3 If you have blow in the headphones, your mic should be OK. When making a test call, try to make a test recording for as long as 10 seconds or at least untill the cuoff beep is heard, when it is played back you may hear a couple of sounds right at the end. Now make an actual call to another user, the mic should work. I have had this on 3 PC's with kubuntu. Basically it works, but fails the test call.

---

### Post by sr243 on 2006-08-30
hey aibo, try downloading the static binary version of skype 1.2.  I use scim, and it seems that this is the only version of skype that works for me.

warning: it took about a minute for it to load for me.

here's the link!
[http://www.skype.com/go/getskype-linux-static](http://www.skype.com/go/getskype-linux-static)

---

### Post by AiBo on 2006-08-30
sr243

Thanks for the suggestion.  I downloaded the version you suggested.  All went well until I made the test call, got 3 seconds of 'hello, welcome....' and the nothing.  An attempt to redial is met with the standard skype message "Problems with sound device."

All or any furhter advivce would be greatly appreciated...

---

### Post by mc^2 on 2006-12-02
I had a problem with the mic too. Not only it didn't work in skype but I was also unable to record anything in gnome-sound-recorder. I found a not very nice but working workaround. I've got ALSA over nvidia hda if that changes anything. So:

You go to the Volume Control as described, find Edit->Preferences, mark just about all (what I need is actually: the mic, Analog Mix, Capture and Input Source (but I found it a bit hard to say which input source goes to which capture (I've got three of them) so marking all Input sources might be a good idea).

Now, you turn on the Mic, the Analog Mix (all the way up), one of the captures and select the Input Source to Mix. Done. Now you just have to set up the Mic volume.

---

### Post by mooscape on 2006-12-15
NMILKOVSKY

Thank you for clear instructions.  I had the same problem and this worked perfectly.

---

