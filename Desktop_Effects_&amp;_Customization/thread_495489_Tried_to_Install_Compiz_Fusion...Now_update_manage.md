---
title: "Tried to Install Compiz Fusion...Now update manager says can't install anything!"
date: 2007-07-08
forum: Desktop Effects &amp; Customization
---

### Post by sbjaved on 2007-07-08
Okay...I followed the official documentation guide for installing Compiz-Fusion in Feisty at: **[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)**

But while "sudo apt-get update & install..." I get this error:

(Reading database ... 132831 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.1+git20070706~3v1ubuntu3_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070706~3v1ubuntu3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070706~3v1ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Now update manager says **nothing can be installed or removed. try running apt-get install -f**. Even running that doesn't fix it. Okay, I don't want Compiz Fusion, just help me get my Update Manager back! 

Anyone?

---

### Post by hyperair on 2007-07-08
That's what happens if you interrupt an installation or removal of a package.You have to run ```
sudo apt-get install -f
``` in a terminal and see if it works, or post the output back here.

---

### Post by sbjaved on 2007-07-08
Here's the output:

saad@saad-desktop:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python-crypto gimp-gap libconvert-binhex-perl liferea-mozilla
  libsoap-lite-perl libmono-security1.0-cil fakeroot debhelper
  module-assistant gnome-bin intltool-debian libxml-libxml-common-perl
  libgconf2-ruby libmono-sharpzip0.84-cil libcairo-ruby libgtk1.2
  libcrypt-ssleay-perl xserver-xorg-dev libatk1-ruby libglib1.2
  libnet-ssleay-perl python-paramiko mplayer-skins
  libxml-namespacesupport-perl libmono-system-web1.0-cil g++-4.1 libgnome32
  gnome-libs-data libipod-cil libglib2-ruby libtk-tablematrix-perl po-debconf
  libterm-readkey-perl python-pyogg libnspr4-0d libsgutils1 libart2 libdv-bin
  libgnorbagtk0 libpango1-ruby python-dsv g++ python2.4-minimal python2.4
  libarchive-zip-perl libossp-uuid-perl libnss-dev libgtk-jni
  libmono-cairo2.0-cil libstdc++6-4.1-dev libossp-uuid15 python-serial
  libipodui-cil firefox-dev libcairo-java libberylsettings0 gettext
  libgdk-pixbuf2-ruby librexml-ruby boo python-imaging libggi2 libgii1
  libio-stringy-perl libhtml-tableextract-perl libxml-libxml-perl libgnomeui32
  libxml-sax-perl python-apsw gnome-raw-thumbnailer libmono1.0-cil wacom-tools
  libxml1 ffmpeg libmono-data-tds1.0-cil libdb3 libglib-java
  libmono-system-data1.0-cil gimp-dcraw libgii1-target-x libgdk-pixbuf2
  libcairo-ruby1.8 libdate-manip-perl libhttp-cache-transparent-perl
  libwww-mechanize-perl dpkg-dev libnspr-dev libipoddevice0 libmime-perl
  python-wxversion libmime-lite-perl libmozjs0d libgtk1.2-common imlib-base
  libfcgi-perl libxml-writer-perl liborbit0 gdk-imlib11 perl-tk html2text
  libgnomesupport0 libemeraldengine0 libgtk2-ruby python-wxgtk2.6
  libio-socket-ssl-perl libuninameslist0 libxul-common libswt3.2-gtk-jni
  libberyldecoration0 dh-make libboost-python1.33.1 libnss3-0d dpatch
  libxmltv-perl libgnorba27 build-essential
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
1 not fully installed or removed.
Need to get 0B/168kB of archives.
After unpacking 1315kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 132831 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.1+git20070706~3v1ubuntu3_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070706~3v1ubuntu3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070706~3v1ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
saad@saad-desktop:~$

---

### Post by hyperair on 2007-07-08
Ah, do this then: 
```
sudo apt-get remove compiz compiz-core
sudo apt-get update
sudo apt-get install ubuntu-desktop compiz compiz-fusion* desktop-effects compizconfig-setings-manager

```

Post the output if it doesn't work.

---

### Post by sbjaved on 2007-07-08
> **hyperair said:**
> Ah, do this then: 
```
sudo apt-get remove compiz compiz-core
sudo apt-get update
sudo apt-get install ubuntu-desktop compiz compiz-fusion* desktop-effects compizconfig-setings-manager

```

Post the output if it doesn't work.
saad@saad-desktop:~$ sudo apt-get remove compiz compiz-core
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz-fusion-plugins-extra: Depends: compiz-core but it is not going to be installed
  compiz-fusion-plugins-main: Depends: compiz-core but it is not going to be installed
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not going to be installed
  compiz-plugins: Depends: compiz-core (= 1:0.3.6-1ubuntu13) but it is not going to be installed
  desktop-effects: Depends: compiz but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by hyperair on 2007-07-09
Ok, that doesn't look too good. Could you try:
```

sudo apt-get remove compiz* desktop-effects
sudo apt-get update
sudo apt-get install ubuntu-desktop compiz compiz-fusion* desktop-effects compizconfig-setings-manager

```

instead?

---

### Post by edwin.e.johnson on 2007-07-09
i had a problem like that during one of my many installs of compiz and beryl i found that i had disabled some of my repo's and it couldn't pull everything...

---

