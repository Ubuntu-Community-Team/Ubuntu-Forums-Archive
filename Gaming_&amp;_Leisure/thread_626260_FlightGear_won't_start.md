---
title: "FlightGear won't start"
date: 2007-11-28
forum: Gaming &amp; Leisure
---

### Post by mmmpancakes on 2007-11-28
Hi all. I searched the forums for a discussion on this but can't find any. 

I'm running the latest version of Ubuntu and everything is up to date. 

I recently installed FlightGear using Add/Remove. The program appears in my menu bar, but when I click to start the program, nothing happens. No program, and no related apps running in my system monitor. 

Any thoughts on what this could be?

---

### Post by mmmpancakes on 2007-11-29
bump

---

### Post by Cannaregio on 2007-12-01
same problem here
here the results of locate flightgear

```
locate flightgear
/var/cache/apt/archives/flightgear_0.9.10-2ubuntu1_i386.deb
/var/lib/dpkg/info/flightgear.postinst
/var/lib/dpkg/info/flightgear.list
/var/lib/dpkg/info/flightgear.postrm
/var/lib/dpkg/info/flightgear.md5sums
/home/cron/.opera/images/www.flightgear.org.gif
/usr/share/app-install/desktop/flightgear.desktop
/usr/share/applications/flightgear.desktop
/usr/share/doc/flightgear
/usr/share/doc/flightgear/README.Debian
/usr/share/doc/flightgear/AUTHORS
/usr/share/doc/flightgear/README
/usr/share/doc/flightgear/FlightGear-FAQ.html
/usr/share/doc/flightgear/copyright
/usr/share/doc/flightgear/Thanks.gz
/usr/share/doc/flightgear/NEWS.gz
/usr/share/doc/flightgear/AptNavFAQ.FlightGear.html
/usr/share/doc/flightgear/Nasal.html
/usr/share/doc/flightgear/README.Cygwin
/usr/share/doc/flightgear/changelog.gz
/usr/share/doc/flightgear/README.IRIX
/usr/share/doc/flightgear/README.JSBSim
/usr/share/doc/flightgear/README.Joystick
/usr/share/doc/flightgear/README.MSVC
/usr/share/doc/flightgear/README.MacOS
/usr/share/doc/flightgear/README.SimGear
/usr/share/doc/flightgear/README.Unix
/usr/share/doc/flightgear/README.Win32-X
/usr/share/doc/flightgear/README.autoconf
/usr/share/doc/flightgear/README.electrical.gz
/usr/share/doc/flightgear/README.gui.gz
/usr/share/doc/flightgear/README.digitalfilters
/usr/share/doc/flightgear/README.properties.gz
/usr/share/doc/flightgear/README.extensions
/usr/share/doc/flightgear/README.fgjs
/usr/share/doc/flightgear/README.introduction
/usr/share/doc/flightgear/README.jsclient
/usr/share/doc/flightgear/README.logging
/usr/share/doc/flightgear/README.mingw
/usr/share/doc/flightgear/README.running.gz
/usr/share/doc/flightgear/README.plib
/usr/share/doc/flightgear/README.submodels.gz
/usr/share/doc/flightgear/README.protocol
/usr/share/doc/flightgear/README.uiuc.gz
/usr/share/doc/flightgear/README.sound
/usr/share/doc/flightgear/README.src
/usr/share/doc/flightgear/README.xmlhud.gz
/usr/share/doc/flightgear/README.tutorial
/usr/share/doc/flightgear/README.xmlpanel.gz
/usr/share/doc/flightgear/README.xmlsound.gz
/usr/share/doc/flightgear/README.xmlsyntax.gz
/usr/share/doc/flightgear/changelog.Debian.gz
/usr/share/doc/flightgear/README.TerraSync
/usr/share/doc/flightgear/README.commands.gz
/usr/share/doc/flightgear/README.IO.gz
/usr/share/doc/flightgear/README.Linux.gz
/usr/share/doc/flightgear/README.conditions.gz
/usr/share/doc/flightgear/README.multiplayer.gz
/usr/share/menu/flightgear

```


SOLVED:
Reinstalled through synaptic package manager
command to start is fgfs
and if you want a different aircraft then 
fgfs --aircraft=A-10
fgfs --aircraft=c310

etcetera, see /usr/share/games/FlightGear/Aircraft 
and install more from
[http://www.flightgear.org/Downloads/aircraft/]("http://www.flightgear.org/Downloads/aircraft/")

---

