---
title: "apt-get Update errors"
date: 2005-11-01
forum: Desktop Environments
---

### Post by ylawayjdp on 2005-11-01
Hi I have had some problems with my apt-get upgrade, when I update I get this out put in konsole (see below).  Why are 86 updates being held back? Is it because they are programs I have installed myself from the repositories and not the normal packages?  

Also wine is not being updated every time it has an error 1 which apparently is a broken pipe.  

Some recent system history: I did have some problems updating to breezy but eventually managed it then my hard drive apparently had an error on it (found in start up scan after 1st reboot after breezy update.)  However ran a scan and repair as suggested (fsdk?).  The system is running fine I would just like to have this issue sorted or explained so I understand what is going on.

Thanks in advance
J

 [INDENT]Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  acpi-support alsa-base alsa-utils amule bind9-host bogofilter
  build-essential capplets-data dnsutils ffmpeg g++ gcc gnome-app-install
  gnome-applets gnome-applets-data gnome-control-center gnome-menus
  gnome-panel gnome-panel-data gnome-terminal gnome-themes grip
  gstreamer0.8-lame gstreamer0.8-misc gstreamer0.8-plugins gstreamer0.8-sid
  gstreamer0.8-swfdec gstreamer0.8-vorbis hal-device-manager htmldoc iproute
  language-support-en lbreakout2 lbreakout2-data libfaac0 libopenal0
  libpt-plugins-alsa libpt-plugins-v4l2 librdf0 libsdl-mixer1.2 libsdl-perl
  libswfdec0.3 libwine linux-image-386 linux-restricted-modules-386 lshw
  mail-notification nvidia-glx openjade openoffice.org openoffice.org-bin
  openoffice.org-gtk-gnome openoffice.org-l10n-en openoffice.org2
  openoffice.org2-calc openoffice.org2-common openoffice.org2-core
  openoffice.org2-draw openoffice.org2-impress openoffice.org2-l10n-en-us
  openoffice.org2-math openoffice.org2-writer python-epydoc python-fuse
  python-mysqldb python-twisted python2.4-glade2 python2.4-gtk2
  python2.4-id3lib python2.4-librdf python2.4-musicbrainz python2.4-mysqldb
  python2.4-numarray python2.4-pgsql python2.4-twisted rhythmbox totem
  totem-gstreamer ttf-indic-fonts ubuntu-docs vdr w3m wvdial xpdf xpdf-common
  xpdf-reader xpdf-utils
The following packages will be upgraded:
  wine
1 upgraded, 0 newly installed, 0 to remove and 87 not upgraded.
10 not fully installed or removed.
Need to get 0B/14.5MB of archives.
After unpacking 53.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 135676 files and directories currently installed.)
Preparing to replace wine 0.0.20050419-1~5.04ubp1 (using .../wine_0.0.20050725-0ubuntu1_i386.deb) ...
Unpacking replacement wine ...
Replacing files in old package libwine ...
dpkg: error processing /var/cache/apt/archives/wine_0.0.20050725-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/wine/glu32.dll.so', which is also in package libwine-gl
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/wine_0.0.20050725-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/INDENT]

---

### Post by beefsprocket on 2005-11-01
Without knowing if you have extra repositories in your sources file, it is hard to tell where the problem begins and ends. I'd suggest removing the wine installation anyways and using the new version from winehq (they have their own respoitory setup for apt use). Also, apt-get -f install might do some good in resolving any other problem(s) that crops up.

---

### Post by ylawayjdp on 2005-11-01
I will try the apt-get -f install my sources file is the standard breezy sources file from the update wiki. 

here is my source file 
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

Is that of any help I will run apt-get with -f and report back
thanks

---

### Post by Kyral on 2005-11-01
Yah try that or

sudo apt-get dist-upgrade

---

### Post by ylawayjdp on 2005-11-07
I tried the above and I am still getting errors with the upgades mentions broken pipes.

What does broken pipe mean?

If "sudo apt-get -f upgrade" and "sudo apt-get dist-upgrade" are not resolving my issue what can I do.  I can post my terminal output if you would like.

J

---

