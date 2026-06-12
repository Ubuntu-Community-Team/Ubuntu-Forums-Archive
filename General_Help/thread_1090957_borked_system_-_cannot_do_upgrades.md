---
title: "borked system - cannot do upgrades"
date: 2009-03-08
forum: General Help
---

### Post by GOwin on 2009-03-08
I'm running 64-bit Intrepid. While experimenting with spatialite, I moved some libraries to /usr/lib. I then realized that the version I got didn't work with 64-bit so I proceeded to delete the libraries I just installed --- however, I probably deleted more than what I put in leading to my present problem.


While trying to do a safe-upgrade, I get the message below. Please note that the root of the error appears to be the line "/usr/lib/xulrunner-1.9.0.7/xulrunner-bin: error while loading shared libraries: libsqlite3.so.0: cannot open shared object file: No such file or directory"


```
 
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
The following partially installed packages will be configured:
  firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support 
  firefox-gnome-support xulrunner-1.9 xulrunner-1.9-gnome-support 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up xulrunner-1.9 (1.9.0.7+nobinonly-0ubuntu0.8.10.1) ...
/usr/lib/xulrunner-1.9.0.7/xulrunner-bin: error while loading shared libraries: libsqlite3.so.0: cannot open shared object file: No such file or directory
dpkg: error processing xulrunner-1.9 (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of firefox-3.0:
 firefox-3.0 depends on xulrunner-1.9 (>= 1.9.0.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing firefox-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-branding:
 firefox-3.0-branding depends on firefox-3.0 (= 3.0.7+nobinonly-0ubuntu0.8.10.1); however:
  Package firefox-3.0 is not configured yet.
dpkg: error processing firefox-3.0-branding (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.0; however:
  Package firefox-3.0 is not configured yet.
 firefox depends on firefox-3.0-branding; however:
  Package firefox-3.0-branding is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9-gnome-support:
 xulrunner-1.9-gnome-support depends on xulrunner-1.9 (= 1.9.0.7+nobinonly-0ubuntu0.8.10.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-gnome-support:
 firefox-3.0-gnome-support depends on firefox-3.0 (= 3.0.7+nobinonly-0ubuntu0.8.10.1); however:
  Package firefox-3.0 is not configured yet.
 firefox-3.0-gnome-support depends on xulrunner-1.9-gnome-support (>= 1.9~b4~); however:
  Package xulrunner-1.9-gnome-support is not configured yet.
dpkg: error processing firefox-3.0-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox-3.0-gnome-support; however:
  Package firefox-3.0-gnome-support is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xulrunner-1.9
 firefox-3.0
 firefox-3.0-branding
 firefox
 xulrunner-1.9-gnome-support
 firefox-3.0-gnome-support
 firefox-gnome-support
Setting up xulrunner-1.9 (1.9.0.7+nobinonly-0ubuntu0.8.10.1) ...
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...

```

Since I couldn't do sudo aptitude install libsqlite3-0, I decided to download the debian package for my system and installed it. Rebooted and everything is working alright again.

---

### Post by dcstar on 2009-03-08
> **GOwin said:**
> I'm running 64-bit Intrepid. While experimenting with spatialite, I moved some libraries to /usr/lib. I then realized that the version I got didn't work with 64-bit so I proceeded to delete the libraries I just installed --- however, I probably deleted more than what I put in leading to my present problem.


While trying to do a safe-upgrade, I get the message below. Please note that the root of the error appears to be the line "/usr/lib/xulrunner-1.9.0.7/xulrunner-bin: error while loading shared libraries: libsqlite3.so.0: cannot open shared object file: No such file or directory"
........


Then reinstall the libsqlite3 package (libsqlite3-0) - the message can't be much clearer when it says it is missing.

---

