---
title: "Request: Azureus 2.3.0.6"
date: 2005-12-31
forum: Deferred/Invalid Requests
---

### Post by Rory on 2005-12-31
PLF Ubuntu says that Azureus is in Backports-Extras, but I'm not seeing it.
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

I've search the forum, so I apologize if this has already been explained elsewhere.

Is there a plan to add Azureus to backports?  If so, when?  If not, why?

If there is no plan, I'm guessing that the PLF page should be updated and maybe we can build a package and have it submitted to PLF?  

Rory

---

### Post by F for Fragging on 2005-12-31
I can remember that it was once part of backports, found it here: [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/universe/binary-i386/](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/universe/binary-i386/)

However, this is an old version of Azureus, and somehow I couldn't get Azureus to auto update when I installed it from the deb package, even as root.

Of course it isn't very difficult to install Azureus manually with the download from the Azureus website, but installing software through the repository is easier.

I would love to see the latest version been backported though. Even though I don't like Azureus (uTorrent rules on Windows), all the other Bittorrent clients on Linux suck hard, so Azureus is quite an essential backport for me.

---

### Post by jdong on 2005-12-31
I am not maintaining Extras anymore.... You can get Azureus packages from Debian Sid -- those debs will install safely on a Ubuntu system.

In addition, you can just extract Azureus directly to a directory on your system and run it from there. Bonus points for doing it in your home directory, since then the updater functions.


The reason Azureus hasn't entered official repositories is because our chosen Java implementation (GCC Java) currently does not support classpath stuff that Azureus needs. The in-development GCC 4.1 does, but since it's in beta stage it will not be adopted until after Dapper.

---

### Post by Rory on 2006-01-01
Thanks for that information. That's very helpful.  

Do you think there's a way to modify the Debian Sib Azureus package so it can be added to PLF, then?  

This would allow Ubuntu users to then grab it from an Ubuntu non-official repository which would make it more accessible.

Rory

---

