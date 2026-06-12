---
title: "automount woes"
date: 2005-09-08
forum: Desktop Environments
---

### Post by vh1 on 2005-09-08
hey there
I'm having troubles with the automounting in ubuntu.

I've installed kubuntu-desktop from the official kde ftp site, and removed all un-needed gnome packages. the automounting worked fine then. I would put in the ubuntu hoary cd and it would show up on my desktop as desired.

but, kubuntu-desktop also downloads a lot of packages that I don't need. so, using debfoster, I removed what I wouldn't need (or so I thought).

only thing is, out of all the removed packages in the keepers file, I can't seem to figure out which one would control the automounting.

here are the contents of my keepers file. I apologize, it's kinda long.
```
acpi
apmd
arts
dbus-1-utils
dcoprss
debfoster
firefox
gdm
grub
gtk-theme-switch
gtk2-engines-gtk-qt
hal-device-manager
kaboodle
kcharselect
kcoloredit
kdeadmin-kfile-plugins
kdebase
kdegraphics-kfile-plugins
kdemultimedia-kappfinder-data
kdemultimedia-kfile-plugins
kdenetwork-filesharing
kdenetwork-kfile-plugins
kdessh
kdf
kdict
kdvi
kfloppy
kgamma
kget
kgpg
kjots
kleopatra
kmix
kmrml
knetworkconf
knewsticker
konq-plugins
kontact
konversation
kopete
kpackage
kpdf
kpf
krec
kscd
kscreensaver
ksim
ksirc
ksnapshot
ksvg
ksync
ksysv
kuickshow
kuser
kview
kwalletmanager
kynaptic
libarts1-audiofile
libarts1-mpeglib
linux-386
lisa
lsb
msttcorefonts
networkstatus
nfs-common
noatun
nvidia-settings
powermanagement-interface
python-adns
python-apt
python-cddb
python-clientcookie
python-crypto
python-egenix-mxproxy
python-egenix-mxstack
python-egenix-mxtexttools
python-epydoc
python-eunuchs
python-examples
python-gadfly
python-gd
python-gdbm
python-gdchart
python-genetic
python-geoip
python-gnupginterface
python-gst
python-htmlgen
python-htmltmpl
python-id3lib
python-imaging-sane
python-jabber
python-ldap
python-musicbrainz
python-mysqldb
python-netcdf
python-newt
python-numarray
python-opengl
python-osd
python-parted
python-pexpect
python-pgsql
python-pisock
python-pqueue
python-pyao
python-pylibacl
python-pyorbit
python-pyvorbis
python-pyxattr
python-reportlab
python-simpletal
python-soappy
python-sqlite
python-stats
python-syck
python-unit
python-xdg
python-xmpp
python2.4-dictclient
python2.4-librdf
python2.4-libxslt1
python2.4-pycurl
python2.4-samba
ttf-bitstream-vera
ttf-freefont
ubuntu-base
x-window-system-core
xnest
xorg-driver-synaptics
xscreensaver-gl
xterm
-akregator
-amarok
-amarok-arts
-anacron
-bicyclerepair
-bogofilter
-cdparanoia
-cdrecord
-cupsys
-cupsys-driver-gimpprint
-cupsys-driver-gimpprint-data
-dc
-dictionaries-common
-diveintopython
-doc-base
-doc-debian
-dvd+rw-tools
-esound
-fetchmail
-foomatic-db
-foomatic-db-engine
-foomatic-db-gimp-print
-foomatic-db-hpijs
-foomatic-filters
-foomatic-filters-ppds
-fortune-mod
-fortunes-min
-fping
-hpijs
-hwdb-client
-ijsgimpprint
-irssi-text
-juk
-k3b
-k3blibs
-kaffeine
-kalarm
-kandy
-karm
-kaudiocreator
-kcalc
-kcron
-kdat
-kdelirc
-kdepim-kfile-plugins
-kdepim-wizards
-kedit
-kfax
-khexedit
-kiconedit
-klaptopdaemon
-kmailcvt
-kmid
-kmilo
-kolourpaint
-konserve
-konsolekalendar
-kooka
-korn
-kpilot
-kpovmodeler
-kppp
-krdc
-krfb
-kruler
-ktimer
-ktnef
-kwifimanager
-lftp
-libdb4.2++
-libdb4.3
-libflac++4
-libgsl0
-libijs-0.35
-libkgantt0
-libkscan1
-libmad0
-libmal1
-libmusicbrainz4
-libmyspell3
-libneon23
-libperl5.8
-librecode0
-libslp1
-libsqlite3-0
-libstartup-notification0
-libstlport4.6
-libtiff-tools
-libtunepimp-bin
-libtunepimp2
-libunicode-string-perl
-libwvstreams3-base
-libxaw7
-mkisofs
-openoffice.org
-openoffice.org-bin
-openoffice.org-debian-files
-openoffice.org-kde
-openoffice.org-l10n-en
-pnm2ppa
-powernowd
-python-glade2
-rdesktop
-readahead
-samba-common
-screen
-secpolicy
-slocate
-smbclient
-ttf-arabeyes
-ttf-arphic-bkai00mp
-ttf-arphic-bsmi00lp
-ttf-arphic-gbsn00lp
-ttf-arphic-gkai00mp
-ttf-baekmuk
-ttf-indic-fonts
-ttf-kochi-gothic
-ttf-kochi-mincho
-ttf-malayalam-fonts
-ttf-opensymbol
-ubuntu-docs
-ubuntu-quickguide
-wvdial
-xpdf-common
-xpdf-utils
```
for anyone who's never used debfoster, the lines that start with '-' mean that package was removed.

another weird thing is that when I put in an audio cd, it is displayed on the desktop fine. but even though kscd is set to autoplay, it doesn't.

---

### Post by mlomker on 2005-09-08
Have you double-checked your settings in the Control Center under Desktop, Behavior, Device Icons?  Hit the defaults button and see if that changes anything.

---

### Post by vh1 on 2005-09-08
[QUOTE=mlomker]Have you double-checked your settings in the Control Center under Desktop, Behavior, Device Icons?  Hit the defaults button and see if that changes anything.[/QUOTE]
 yup, it's set to display the proper things.

if I do an `apt-get install kubuntu-desktop` the icons will show up fine, without changing any settings

---

### Post by vh1 on 2005-09-09
a couple more dianostics

if I plug in my camera, it comes up on the desktop fine. audio cd's show up fine.

I know I can install magicdev or gnome-volume-manager and link to them in my ~/.kde/Autostart directory, but a) those are gnome applications and b) not what kubuntu originally uses.

so obviously I have removed the required package. I just need help finding out which one it was

---

