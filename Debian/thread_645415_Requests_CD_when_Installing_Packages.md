---
title: "Requests CD when Installing Packages"
date: 2007-12-20
forum: Debian
---

### Post by VoodooSteve on 2007-12-20
Whenever I install a new package thru aptitude, it always asks for me to insert the Debian Install CD. Any way I can get rid of this minor annoyance?

---

### Post by Lord_Dicranius on 2007-12-20
In Synaptic, Settings > Repositories.  Then uncheck the boxes at the bottom of the window for Cdrom.

**EDIT*
ROFL Just saw what forum this was in...might not work for ya like that, I don't know.  I've never used Debian :-P

---

### Post by jingo811 on 2007-12-20
```
su -
nano /etc/apt/sources.list
```
Then uncomment your cdrom lines.
> # deb cdrom:[Debian GNU/Linux 4.0 r1 _Etch_ - Official i386 CD Binary-1 20070819-11:52]/ etch contrib $


Here's my list just adapt the (htttp://ftp.....) server list to servers in your own country for optimal download speeds.
#Country mirrors for General and Multimedia debs.
[http://www.debian.org/mirror/mirrors_full#SE](http://www.debian.org/mirror/mirrors_full#SE)
[http://www.debian-multimedia.org/debian-m.php](http://www.debian-multimedia.org/debian-m.php)

```

######
#
# Standard list for most Debian users in Sweden.
#
######

deb http://ftp.sunet.se/pub/Linux/distributions/debian/ etch main contrib non-free
deb-src http://ftp.sunet.se/pub/Linux/distributions/debian/ etch main contrib non-free

deb http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/ stable main
deb-src http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/ stable main

deb http://security.debian.org/ etch/updates main contrib non-free
deb-src http://security.debian.org/ etch/updates main contrib non-free




############################################################################################



#
# deb cdrom:[Debian GNU/Linux 4.0 r1 _Etch_ - Official i386 CD Binary-1 20070819-11:52]/ etch contrib $
#deb cdrom:[Debian GNU/Linux 4.0 r1 _Etch_ - Official i386 CD Binary-1 20070819-11:52]/ etch contrib m$

# Line commented out by installer because it failed to verify:
#deb http://security.debian.org/ etch/updates main contrib
# Line commented out by installer because it failed to verify:
#deb-src http://security.debian.org/ etch/updates main contrib
```

---

