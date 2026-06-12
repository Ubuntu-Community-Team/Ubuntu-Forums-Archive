---
title: "DPKG Error phython-gnome2"
date: 2009-02-23
forum: General Help
---

### Post by CsmcDem on 2009-02-23
Hello I'm using ubuntu server 8.04 and I need to install ruby, but every time I go to install it via apt-get I get an error. I tried installing other things, and I get the same error. I tried this command ```
sudo rm -rfv /var/lib/dpkg/status && sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
``` like I saw in another post, but it didn't help.

Here's the error I am getting
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ruby is already the newest version.
ruby set to manually installed.
The following packages were automatically installed and are no longer required:
  sg3-utils bluez-gnome python-gtk2-doc python-zopeinterface python-twisted-core
  python-opengl libmtp7 liblzo1 python-beagle gnome-games-extra-data hal-cups-utils
  libgail-gnome-module gstreamer0.10-plugins-ugly tracker libxml-libxml-common-perl
  untex python-software-properties libdatetime-locale-perl ubuntu-gdm-themes
  python-gnomecanvas libmime-encwords-perl libbtctl4 libparams-validate-perl libotr2
  python-twisted-web gnome-bluetooth libxml-namespacesupport-perl tracker-utils mdetect
  libclass-accessor-perl libxml-atom-perl gnome-cards-data ggzcore-bin
  libgtksourceview1.0-0 libclass-trigger-perl python-gtkglext1 ubuntu-artwork
  libsqlite3-dev libggzmod4 ubuntu-sounds ubuntu-wallpapers libsgutils1
  libclass-errorhandler-perl wv libgpod3 pidgin-data libapr1-dev libgadu3
  libxml-libxslt-perl festlex-cmu python-configobj guile-1.8-libs libapache-ruby1.8
  python-serial guile-1.6-libs gnome-utils libttf2 libhesiod0 acl python-pam
  python-openssl human-theme courier-ssl libmime-charset-perl bluez-utils libxevie1
  bluez-audio liburi-fetch-perl python-soappy libwv-1.2-3 gtk2-engines-ubuntulooks
  python-brlapi libxml-libxml-perl unattended-upgrades libggz2 python-ctypes
  festlex-poslex at-spi libxml-sax-perl libdatetime-perl python-pyopenssl python-louie
  libgtksourceview-common system-config-printer-common human-icon-theme libqthreads-12
  gnome-games-data festvox-kallpc16k libjson-perl libnet-openid-consumer-perl
  libgpod-common liblpint-bonobo0 libgnome-speech7 software-properties-gtk uuid-dev
  python-setuptools python-coherence python-cups libexpat1-dev tracker-search-tool
  python-fpconst libpurple-bin libimage-size-perl libmeanwhile1 python-pkg-resources
  displayconfig-gtk festival gtk2-engines-murrine libclass-data-inheritable-perl
  libggzcore9 libzephyr3 libgnomebt0 libjcode-pm-perl dbconfig-common
  liblwp-authen-wsse-perl libaprutil1-dev python-gnome2-desktop
  liblucene-queryparser-perl libdatetime-timezone-perl libtracker-gtk0 libguile-ltdl-1
  libestools1.2 python-twisted-bin libcrypt-dh-perl libclass-singleton-perl libmpeg2-4
  o3read libyaml-tiny-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 541 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up python-gnome2 (2.22.0-1) ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: Trying to overwrite gtk-2.0/gconf.so which is already provided by /usr/share/python-support/python-gconf
dpkg: error processing python-gnome2 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 python-gnome2
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Please help!

---

### Post by CsmcDem on 2009-03-09
anyone?

---

