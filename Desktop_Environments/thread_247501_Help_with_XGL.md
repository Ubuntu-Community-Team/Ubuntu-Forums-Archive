---
title: "Help with XGL"
date: 2006-08-30
forum: Desktop Environments
---

### Post by andyrobo60 on 2006-08-30
When I run compiz all the menu bars on GNOME dissapear I get the message.

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No manageable screens found on display :0.0 

after searching around I found this post [http://www.ubuntuforums.org/showthread.php?t=131267&page=63](http://www.ubuntuforums.org/showthread.php?t=131267&page=63)

following one of the posts i tryed to reinstall all the compiz packages using
sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome --reinstall

however it gives back 

Reading package lists... Done
Building dependency tree... Done
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies.
  cgwd: Depends: compiz-plugins (>= 0.2) but it is not going to be installedor
                 compiz-vanilla but it is not going to be installed
  compiz: Depends: compiz-core but it is not going to be installed
          Depends: compiz-plugins (>= 0.7) but it is not going to be installed
  compiz-gnome: Depends: compiz-core (= 0.0.13.41-0ubuntu1) but it is not going to be installed
  libgl1-mesa: Conflicts: libgl1-mesa-dri (< 6.5.0) but 6.4.1-0ubuntu8 is to be installed
  libgl1-mesa-dri: Depends: libgl1-mesa (= 6.4.1-0ubuntu8) but 6.5.1+cvs20060824 is to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).

as it says I tryed running apt-get -f install but that returns 

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies...Done
The following extra packages will be installed:
  compiz-core compiz-plugins
The following NEW packages will be installed
  compiz-core compiz-plugins
0 upgraded, 2 newly installed, 0 to remove and 19 not upgraded.
1 not fully installed or removed.
Need to get 0B/627kB of archives.
After unpacking 2936kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  compiz-core compiz-plugins
Install these packages without verification [y/N]? y
(Reading database ... 88998 files and directories currently installed.)
Unpacking compiz-core (from .../compiz-core_0.0.13.41-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-core_0.0.13.41-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/compiz.real', which is also in package compiz
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking compiz-plugins (from .../compiz-plugins_0.7-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-plugins_0.7-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libresize.so', which is also in package compiz
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-core_0.0.13.41-0ubuntu1_i386.deb
 /var/cache/apt/archives/compiz-plugins_0.7-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

If anyone can help with this problem it would be VERY much appreciated.

---

