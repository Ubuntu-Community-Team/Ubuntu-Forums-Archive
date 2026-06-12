---
title: "DNS Problem?"
date: 2006-08-29
forum: Desktop Environments
---

### Post by khedron on 2006-08-29
My problem is that when I open Synaptic (or use apt-get) it can neither update package information nor download any packages. The error is as follows:

```

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

```

It seems strange, but I can make the problem disappear by visiting the sites contained in /etc/apt/sources.lst with Firefox. Once I do that, Synaptic (and apt-get) have no problem with accessing files from those sites.

From my point of view it looks like my system's DNS is not set up properly. What can I do to diagnose and fix this?

---

### Post by Atomic Dog on 2006-08-29
Do a search of the forum.  There's a few posts like this one: [http://www.ubuntuforums.org/showthread.php?t=206692](http://www.ubuntuforums.org/showthread.php?t=206692)

I ended up editing the resolv.conf and adding the actual nameserver address(es).

Later I started using wifi-radar which makes custon config much easier IMHO.

---

