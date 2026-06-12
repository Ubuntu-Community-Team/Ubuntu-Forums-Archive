---
title: "broken package manager"
date: 2011-08-07
forum: Desktop Environments
---

### Post by bobdobbs on 2011-08-07
Hi.

Whenever I try to install something with apt-get, I get a list of errors. Most of the time, the package I want to install gets installed anyway.
However, this time samba stopped working, and I discovered that it was no longer on my system. I'm not sure how this happened - I haven't tried to remove it. 

So, I tried to reinstall it with 'apt-get install samba'. This time, the package did not install, and I got a long output from the terminal:

```

language-support-ss - metapackage for Swati language support                                                  
language-support-writing-ss - Writing aids metapackage for Swati                                              
bugsquish - Bugs are trying to suck blood out of your arm!                                                    
create-resources - shared resources for use by creative applications                                          
ggz-game-servers - GGZ Gaming Zone: game servers collection                                                   
ggz-kde-games - GGZ Gaming Zone: game clients collection for KDE                                              
gkrellmitime - Internet time plugin for gkrellm                                                               
libhdfeos-dev - Development files for the HDF-EOS4 library                                                    
libhdfeos0 - Earth Observation System extensions to HDF4
libhe5-hdfeos-dev - Development files for the HDF-EOS5 library
libhe5-hdfeos0 - Earth Observation System extensions to HDF5
nfswatch - Program to monitor NFS traffic for the console
openocd - Open on-chip JTAG debug solution for ARM and MIPS systems
swatch - Log file viewer with regexp matching, highlighting & hooks
swath - Thai word segmentation program
swisswatch - Swiss Railway Clock for the X Window System
thailatex - Thai support for LaTeX
wmitime - clock dock app showing time and internet time
wmtz - WindowMaker dock app that displays the time in different zones
language-pack-kde-ss - KDE translation updates for language Swati
language-pack-kde-ss-base - KDE translations for language Swati
language-pack-ss - translation updates for language Swati
language-pack-ss-base - translations for language Swati
swat - Samba Web Administration Tool
root@faustina:/home/mantis# apt-get install swat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
swat is already the newest version.
The following packages were automatically installed and are no longer required:
  openoffice.org-l10n-en-gb ttf-sil-gentium openoffice.org-java-common openoffice.org-filter-mobiledev
  ttf-sil-gentium-basic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mercurial (1.4.3-1) ...
dpkg: error processing mercurial (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up samba-common (2:3.4.7~dfsg-1ubuntu3.7) ...
dpkg: error processing samba-common (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (>= 2:3.4.0~pre1-2); however:
  Package samba-common is not configured yet.
dpkg: error processing samba-common-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
                                                          dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.7); however:
  Package samba-common is not configured yet.
 samba depends on samba-common-bin; however:
  Package samba-common-bin is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.7); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbfs:
 smbfs depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.7); however:
  Package samba-common is not configured yet.
dpkg: error processing smbfs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of swat:
 swat depends on samba (= 2:3.4.7~dfsg-1ubuntu3.7); howeverNo apport report written because MaxReports is reached already
           No apport report written because MaxReports is reached already
                                                                         No apport report written because MaxReports is reached already
                         No apport report written because MaxReports is reached already
                                                                                       No apport report written because MaxReports is reached already
                                       :
  Package samba is not configured yet.
dpkg: error processing swat (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of winbind:
 winbind depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.7); however:
  Package samba-common is not configured yet.
dpkg: error processing winbind (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpam-smbpass:
 libpam-smbpass depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.7); however:
  Package samba-common is not configured yet.
dpkg: error processing libpam-smbpass (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mercurial
 samba-common
 samba-common-bin
 samba
 smbclient
 smbfs
 swat
 winbind
 libpam-smbpass
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've tried:
'apt-get -f install'
This gives me the exact same message.

Is this something that I can recover from? Or do I have to reinstall ubuntu?

---

### Post by ~!geek!~ on 2011-08-07
Try to run apt-get with --fix-missing options

After this run 
> sudo apt-get autoremove

Now try to run 
>  sudo apt-get update
 to test if package manager is fixed!!!

---

### Post by bobdobbs on 2011-08-07
> **~!geek!~ said:**
> Try to run apt-get with --fix-missing options

After this run 


Now try to run 

 to test if package manager is fixed!!!

'apt-get --fix-missing install samba' just gave me the same error output as before.

After it ran I update anyway and got the usual pile of errors. Then I ran 
'apt-get --fix-missing install samba' again, and got the same errors.

What next?

---

### Post by westie457 on 2011-08-07
> **bobdobbs said:**
> 'apt-get --fix-missing install samba' just gave me the same error output as before.

After it ran I update anyway and got the usual pile of errors. Then I ran 
'[COLOR="Red"]apt-get --fix-missing install samba[/COLOR]' again, and got the same errors.

What next?

The bit in red probably should be ```
sudo apt-get install samba --fix -missing
```

NO it is not Ignore it.

---

### Post by westie457 on 2011-08-07
Take a look at this Web page: [http://www.cyberciti.biz/tips/troubleshooting-debian-ubuntu-package-upgrades-removals.html](http://www.cyberciti.biz/tips/troubleshooting-debian-ubuntu-package-upgrades-removals.html)

While not dealing with your specific issue it might give you some pointers to sort things.

---

### Post by bobdobbs on 2011-08-07
> **westie457 said:**
> The bit in red probably should be ```
sudo apt-get install samba --fix -missing
```

NO it is not Ignore it.

I still get the same errors from this command.

---

### Post by bobdobbs on 2011-08-07
> **westie457 said:**
> Take a look at this Web page: [http://www.cyberciti.biz/tips/troubleshooting-debian-ubuntu-package-upgrades-removals.html](http://www.cyberciti.biz/tips/troubleshooting-debian-ubuntu-package-upgrades-removals.html)

While not dealing with your specific issue it might give you some pointers to sort things.


That page suggests purging trouble packages, and then reinstalling them.

I started the process...

```

root@faustina:/home/mantis# apt-get purge samba-common samba-common-bin smbclient winbind libpam-smbpass
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  samba-doc openbsd-inetd
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  kubuntu-desktop* libpam-smbpass* nautilus-share* samba-common* samba-common-bin* smb4k* smbclient* smbfs*
  ubuntu-desktop* winbind*
0 upgraded, 0 newly installed, 10 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 77.0MB disk space will be freed.

```

However, I don't want to remove ubuntu-desktop or kde.
Given that the package manager is screwed, I don't know if I'll be able to get them back again.

What else can I try?

---

### Post by oldos2er on 2011-08-07
9.04 is no longer supported, its repositories have moved to old-releases. You probably should upgrade to at least 10.04.

Just FYI, it is safe to remove a *buntu-desktop package, which are metapackages. [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

---

### Post by bobdobbs on 2011-08-07
Hi Anne.

I'm on a recently cleanly installed version of 10.04.
If possible, I'd like to clean up this mess so I can upgrade to the latest version of ubuntu.

> **oldos2er said:**
> 9.04 is no longer supported, its repositories have moved to old-releases. 
You probably should upgrade to at least 10.04.

Just FYI, it is safe to remove a *buntu-desktop package, which are metapackages. [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

Cool.

I ran this:
'apt-get purge samba-common samba-common-bin smbclient winbind libpam-smbpass'
And that removed the packages. Then I ran:
'apt-get install samba nautilus-share'

I got this long error output:

> 
dpkg: warning: files list file for package `pinentry-qt4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `erc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `install-info' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-voodoo' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtk-vnc-1.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `knotes' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libexpat1-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `virtuoso-minimal' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `jockey-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dvd+rw-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavcodec-extra-52' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `system-config-printer-gnome' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `usb-creator-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkrossui4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-thesaurus-en-us' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdict-1.0-6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gitk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `hicolor-icon-theme' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgimp2.0-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgvfscommon0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-fstab' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcdaudio1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sqlite3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `epiphany' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt4-sql-sqlite' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-mako' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sensible-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mono-gac' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cedet-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `adium-theme-ubuntu' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkmime4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `seahorse' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gedit-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-apm' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wireshark' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `softflowd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgl1-mesa-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bsdutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `perl-modules' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lftp' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `avahi-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgssrpc4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ucf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-thesaurus-en-au' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkdnssd4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdemultimedia-kio-plugins' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dolphin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `psmisc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdbusmenu-glib1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgpg-error0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavc1394-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpython2.6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libusb-0.1-4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxfixes-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmysql-ruby' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkdcraw8' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbinio1ldbl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `autotools-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gnomeapplet' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkdeui5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpci3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xfonts-terminus' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `hpijs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gambas2-gb-settings' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openshot-doc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cvsservice' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gstreamer0.10-plugins-bad-multiverse' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblo7' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml-sax-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpam0g' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnotify0.4-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpopt0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-reportlab' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wamerican' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ncurses-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tcl8.5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tcl8.4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libglitz-glx1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-zope.interface' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `whois' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libplasma-geolocation-interface4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mesa-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libv4l-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apt-xapian-index' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libakonadiprivate1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lib32asound2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfuse2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mjpegtools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwildmidi0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdvdread4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-selector' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdesudo' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-ibus' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-minimal' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mscompress' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libspeex1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgssapi-krb5-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ffmpeg2theora' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqtgui4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdebase-workspace' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kcm-touchpad' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ibus-gtk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libflac++6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkmediaplayer4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `binfmt-support' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgeoip1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpoppler-qt4-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libctemplate0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `miro' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apturl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-themes-selected' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-en' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lib32v4l-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openmovieeditor' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linkchecker' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wpasupplicant' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gstreamer0.10-nice' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `g++-4.4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome-desktop-2-17' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `procps' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libiodbc2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `texi2html' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cpp-4.4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `metacity' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxinerama-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libk3b6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdebase-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjpeg62' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `getlibs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-style-human' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnomepanel2.24-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compiz' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjline-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `fontconfig' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-settings-daemon' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lsb-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtasn1-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `plasma-widget-quickaccess' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `emacs23-bin-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gconf-editor' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tk8.5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tk8.4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgd2-xpm' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavahi-client-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `jack' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-papyon' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `konsole' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtk2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtop2-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libuuid1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-system-monitor' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `screensaver-default-images' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ruby1.8-elisp' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lzma' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxinerama1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsdl1.2debian' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `evolution-data-server-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-wnck' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `plymouth-x11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpisync1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgegl-0.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `eog' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-tk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-sis' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kontact' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cvs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kde-window-manager' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-dbus' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xcursor-themes' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwps-0.1-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libogg-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkblog4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjs-jquery' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgcrypt11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtie-ixhash-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libupnp3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-v4l' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-ubuntuone-client' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsox-fmt-alsa' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libexif12' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdbm3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkdewebkit5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pulseaudio-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libhtml-format-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcairo2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libibus1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `erlang-public-key' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgstfarsight0.10-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `myspell-en-au' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `man-db' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpango-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libffi5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `banshee' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libenca0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgraphite3' missing, assuming package has no files currently installed.
(Reading database ... 35%
dpkg: warning: files list file for package `libgamin0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `module-init-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libflac8' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libvorbis-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gettext-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libvorbisfile3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gambas2-gb-qt' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libperl5.10' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-user-guide' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `elib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgmp3c2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `systemsettings' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kde-zeroconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xscreensaver-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `desktop-file-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `example-content' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gpgv' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdelibs4c2a' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `login' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgoocanvas3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `telnet' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11-xkb-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kmousetool' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gstreamer0.10-plugins-base-apps' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wireless-crda' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `laptop-detect' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-uniconvertor' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `makedev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `initramfs-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11proto-input-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libprotobuf5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-twisted-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gdm' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `menu' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gdb' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcelt0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gtkspell' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsdl1.2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-terminal' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kvkbd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ant-optional-gcj' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxmuu1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libclass-accessor-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml-parser-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libunicode-string-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcb-shm0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwxgtk2.8-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `finger' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdbi-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kubuntu-default-settings' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pulseaudio-module-x11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmaa2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openprinting-ppds' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xfonts-mathml' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsysfs2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bcmwl-modaliases' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `debianutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `knm-runtime' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfreetype6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sudo' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kommander-kde3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgpgme++2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsane' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libzip1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `coreutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `skype' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libatk1.0-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-system-data2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `empathy' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `esound-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtheora-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gvfs-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgl1-mesa-dri' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxdmcp6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmpfr1ldbl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpq5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `shared-mime-info' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libraw1394-11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdelibs5-plugins' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpolkit-gobject-1-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-sip' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-headers-2.6.32-32-generic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libart-2.0-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmagickcore2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `jackd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mono-runtime' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdepimlibs-kio-plugins' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gnome2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gimp' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libffado2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dash' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `memtest86+' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libelf1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `hddtemp' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gtk2-engines-murrine' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdepasswd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-aptdaemon' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `miro-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ktorrent-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjaxp1.3-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `librecode0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnomekbd4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dstat' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpth20' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `debconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kbluetooth' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mono-2.0-gac' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pitivi' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjson-glib-1.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgssdp-1.0-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apturl-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `nfdump' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsyndication4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-lxml' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `java-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdata1.4-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `chromium' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgpod-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `empathy-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `plasma-widget-facebook' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `outrec' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sane-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libclutter-1.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtext-wrapi18n-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `plasma-widget-kubuntu-feedback' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfftw3-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kino' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnotify-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbonoboui2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-client-core-5.1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tcpd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-pkg-resources' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmimelib4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kfilereplace-kde3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtkspell0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkfile4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libexempi3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml-libxml-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-input-vmmouse' missing, assuming package has no files currently installed.
(Reading database ... 81163 files and directories currently installed.)
Unpacking samba-common (from .../samba-common_2%3a3.4.7~dfsg-1ubuntu3.7_all.deb) ...
Selecting previously deselected package samba-common-bin.
Unpacking samba-common-bin (from .../samba-common-bin_2%3a3.4.7~dfsg-1ubuntu3.7_amd64.deb) ...
Selecting previously deselected package nautilus-share.
Unpacking nautilus-share (from .../nautilus-share_0.7.2-12build1_amd64.deb) ...
Selecting previously deselected package samba.
Unpacking samba (from .../samba_2%3a3.4.7~dfsg-1ubuntu3.7_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for ufw ...
Setting up mercurial (1.4.3-1) ...
dpkg: error processing mercurial (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up samba-common (2:3.4.7~dfsg-1ubuntu3.7) ...
dpkg: error processing samba-common (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (>= 2:3.4.0~pre1-2); however:
  Package samba-common is not configured yet.
dpkg: error processing samba-common-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-share:
 nautilus-share depends on samba-common (>= 3.0.27a); however:
  Package samba-common is not configured yet.
 nautilus-share depends on samba-common-bin | samba-common (<< 2:3.4.0~pre2-1~0); however:
  Package samba-common-bin is not configured yet.
  Version of samba-common on system is 2:3.4.7~dfsg-1ubuntu3.7.
dpkg: error processing nautilus-share (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.7); however:
  Package samba-common is not configured yet.
 samba depends on samba-common-bin; however:
  Package samba-common-biNo apport report written because the error message indicates its a followup error from a previous failure.
                     No apport report written because MaxReports is reached already
                                                                                   No apport report written because MaxReports is reached already
                                   n is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mercurial
 samba-common
 samba-common-bin
 nautilus-share
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)


There was more, but that's as far as I could scroll back to paste.

What can I do now?

---

### Post by oldos2er on 2011-08-08
I did a little googling but can't find any concrete solution to your problem. But give these two commands a try ```
sudo dpkg --configure -a

sudo apt-get --fix-missing
``` I know you tried something similar already.

---

### Post by bobdobbs on 2011-08-08
> **oldos2er said:**
> I did a little googling but can't find any concrete solution to your problem. But give these two commands a try ```
sudo dpkg --configure -a

sudo apt-get --fix-missing
``` I know you tried something similar already.

I've already tried 'apt-get --fix-missing'. I found that when I was initially googling. It doesn't do anything.

'dpkg --configure -a' just returns the same long error output as before.

---

### Post by bobdobbs on 2011-08-14
bump

---

### Post by bobdobbs on 2011-08-15
bump

---

### Post by bobdobbs on 2011-08-26
> **bobdobbs said:**
> bump

bump

---

### Post by elliotn on 2011-08-26
did you try
sudo apt-get install -f

---

### Post by bobdobbs on 2011-08-26
> **elliotn said:**
> did you try
sudo apt-get install -f

Yes. That's pretty much the first thing I tried. From time to time I try it again. This is the result I get at the moment:


```
root@faustina:/home/mantis# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mercurial (1.4.3-1) ...
dpkg: error processing mercurial (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up samba-common (2:3.4.7~dfsg-1ubuntu3.7) ...
dpkg: error processing samba-common (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 mercurial
 samba-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by wildmanne39 on 2011-08-26
Hi, here is a link were the problem was fixed.
[http://allforlinux.com/2010/07/solving-e-sub-process-usrbindpkg-returned-an-error-code1/](http://allforlinux.com/2010/07/solving-e-sub-process-usrbindpkg-returned-an-error-code1/)

---

### Post by bobdobbs on 2011-08-26
> **wildmanne39 said:**
> Hi, here is a link were the problem was fixed.
[http://allforlinux.com/2010/07/solving-e-sub-process-usrbindpkg-returned-an-error-code1/](http://allforlinux.com/2010/07/solving-e-sub-process-usrbindpkg-returned-an-error-code1/)

I ran through the process described in that post for one of the three problem packages - samba. 

At the end of the process, I then ran 'apt-get install samba'.
I got:
"samba is already the newest version"

So, the process gets rid of the error messages from apt.

However, I actually want samba installed.

Thanks for the link, but the processed described there doesn't do what I want.

---

### Post by wildmanne39 on 2011-08-26
Hi, according to this
> "samba is already the newest version"

it is already installed.

---

