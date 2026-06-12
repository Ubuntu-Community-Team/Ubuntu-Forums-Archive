---
title: "KDE crashes upon logging in"
date: 2009-03-14
forum: Desktop Environments
---

### Post by JockVSJock on 2009-03-14
Running the following: 
-Ubuntu 8.10 
-KDE 4 (which I've installed)
-Linux ladytron 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

When trying to start KDE from KDM, I the desktop gets drawn and here the login sound, however the screen turns to black.  Before this happened, I believe I tried to use high quality graphics which may have caused the issue.  Looking thru the logs, see the following from /var/log/kdm.log

```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux ladytron 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd)
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar 14 19:01:50 2009
(==) Using config file: "/etc/X11/xorg.conf"
kdmgreet(5627) KLocalePrivate::initEncoding: Cannot resolve system encoding, defaulting to ISO 8859-1.

```

Any ideas...?

thanks

---

