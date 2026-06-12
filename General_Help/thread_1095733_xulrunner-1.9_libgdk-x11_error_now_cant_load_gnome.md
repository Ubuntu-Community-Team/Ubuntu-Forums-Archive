---
title: "xulrunner-1.9 libgdk-x11 error now cant load gnome desktop"
date: 2009-03-14
forum: General Help
---

### Post by munkiepus on 2009-03-14
Hi folks,

I was wondering if anyone could shed any light on this error, it's stopping me from loading the gnome desktop properly and these packages are now broken. I've searched all over the place and cant find anything.


I've tried removing the  xulrunner-1.9 package with purge and reinstalling and it didn't help.


 xulrunner-1.9
 yelp
 gnome-user-guide
 ubuntu-docs
 firefox-3.0
 firefox-3.0-branding
 firefox
 xulrunner-1.9-gnome-support
 firefox-3.0-gnome-support
 firefox-gnome-support
 ubufox
 ubuntu-desktop


/usr/lib/xulrunner-1.9.0.7/xulrunner-bin: error while loading shared libraries: /usr/lib/libgdk-x11-2.0.so.0: unexpected PLT reloc type 0x03
dpkg: error processing xulrunner-1.9



```
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up xulrunner-1.9 (1.9.0.7+nobinonly-0ubuntu0.8.10.1) ...
/usr/lib/xulrunner-1.9.0.7/xulrunner-bin: error while loading shared libraries: /usr/lib/libgdk-x11-2.0.so.0: unexpected PLT reloc type 0x03
dpkg: error processing xulrunner-1.9 (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of yelp:
 yelp depends on xulrunner-1.9 (>= 1.9~rc1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing yelp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-guide:
 gnome-user-guide depends on yelp; however:
  Package yelp is not configured yet.
dpkg: error processing gnome-user-guide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-docs:
 ubuntu-docs depends on gnome-user-guide; however:
  Package gnome-user-guide is not configured yet.
 ubuntu-docs depends on yelp; however:
  Package yelp is not configured yet.
dpkg: error processing ubuntu-docs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firNo apport report written because the error message indicates its a followup error from a previous failure.
                 No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                           No apport report written because MaxReports is reached already
                                          No apport report written because MaxReports is reached already
                                                                                                        No apport report written because MaxReports is reached already
                       No apport report written because MaxReports is reached already
                                                                                     No apport report written because MaxReports is reached already
    No apport report written because MaxReports is reached already
                                                                  No apport report written because MaxReports is reached already
                                                                                                                                No apport report written because MaxReports is reached already
                                               No apport report written because MaxReports is reached already
                                                                                                             efox-3.0:
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
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on firefox | abrowser | firefox-3.0 | firefox-2; however:
  Package firefox is not configured yet.
  Package abrowser is not installed.
  Package firefox-3.0 is not configured yet.
  Package firefox-2 is not installed.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on yelp; however:
  Package yelp is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xulrunner-1.9
 yelp
 gnome-user-guide
 ubuntu-docs
 firefox-3.0
 firefox-3.0-branding
 firefox
 xulrunner-1.9-gnome-support
 firefox-3.0-gnome-support
 firefox-gnome-support
 ubufox
 ubuntu-desktop

```


thanks

---

