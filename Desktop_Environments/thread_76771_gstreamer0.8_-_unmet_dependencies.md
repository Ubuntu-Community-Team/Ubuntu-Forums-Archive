---
title: "gstreamer0.8 - unmet dependencies"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Redindian on 2005-10-15
I'm getting the following error during my upgradation.

E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
tazzh@taz:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gstreamer0.8-misc
The following NEW packages will be installed:
  gstreamer0.8-misc
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/1243kB of archives.
After unpacking 3457kB of additional disk space will be used.
Do you want to continue [Y/n]? Y

Preconfiguring packages ...
(Reading database ... 100736 files and directories currently installed.)
Unpacking gstreamer0.8-misc (from .../gstreamer0.8-misc_0.8.11-0ubuntu5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/gstreamer0.8-misc_0.8.11-0ubuntu5_i386.deb (--unpack):
 trying to overwrite `/usr/lib/gstreamer-0.8/libgstgoom.so', which is also in package gstreamer0.8-visuals
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gstreamer0.8-misc_0.8.11-0ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help?????
thanks.

---

### Post by dickmorrell on 2005-10-18
Me too....

Any joy ?

---

### Post by UzbrojonyBandyta on 2005-10-28
Me too, and this appeared when I used Automatix

---

### Post by el toro on 2005-10-28
I noticed it says that it conflicts with the package gstreamer-0.8-visuals.  This package is not in the breezy repos from what I can see--what do you have in your sources.list?  You might also want to try removing the aforementioned package and then trying to install gstreamer-misc again.

---

