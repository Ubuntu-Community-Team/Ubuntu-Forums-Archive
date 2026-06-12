---
title: "help with apt-get error"
date: 2006-07-07
forum: Desktop Environments
---

### Post by Thund3rstruck on 2006-07-07
I'm having all kinds of trouble with apt-get. My autoupdater keeps telling me that apt is broken. When I try to run apt-get install -f I get this output. 

Can anyone assist me on troubleshooting this?
TIA

Reading package lists...
Building dependency tree...
Correcting dependencies... Done
The following extra packages will be installed:
  amarok amarok-xine
Suggested packages:
  libvisual0.2-plugins konqueror www-browser python-qt3 libqt0-ruby1.8
Recommended packages:
  kdemultimedia-kio-plugins
The following NEW packages will be installed:
  amarok amarok-xine
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
7 not fully installed or removed.
Need to get 0B/13.3MB of archives.
After unpacking 26.5MB of additional disk space will be used.
(Reading database ... 136768 files and directories currently installed.)
Unpacking amarok-xine (from .../amarok-xine_2%3a1.4.1-0ubuntu1_i386.deb) ...
Unpacking amarok (from .../amarok_2%3a1.4.1-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/amarok-xine_2%3a1.4.1-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/share/services/amarok_xine-engine.desktop', which is also in package amarok-1.4.1
dpkg: error processing /var/cache/apt/archives/amarok_2%3a1.4.1-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde3/libamarok_void-engine_plugin.la', which is also in package amarok-1.4.1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/amarok-xine_2%3a1.4.1-0ubuntu1_i386.deb
 /var/cache/apt/archives/amarok_2%3a1.4.1-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Thund3rstruck on 2006-07-07
some how I always end up solving my own problem...

Turns out I had locally installed amarok 1.4.1 locally via package: amarok-1.4.1_i386.deb. 

The next day I decided to add amarok repository into apt/sources.list so that it would auto update. By doing that, amarok's repository must have installed additional conflicting packages because I started getting the error above today. 

I uninstalled amarok from the .deb package and ran sudo-apt install -f and repaired the dependency issue.

---

