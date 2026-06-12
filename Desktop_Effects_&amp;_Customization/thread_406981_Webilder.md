---
title: "Webilder"
date: 2007-04-11
forum: Desktop Effects &amp; Customization
---

### Post by theredcross on 2007-04-11
haven't seen anyone post any help threads on webilder so I'm probably doing something obviously wrong; but I followed the directions on the project website and I'm getting a weird hangup:
```
$ webilder_desktop
Traceback (most recent call last):
  File "/usr/bin/webilder_desktop", line 2, in ?
    from webilder.WebilderDesktop import main
  File "/usr/lib/python2.4/site-packages/webilder/WebilderDesktop.py", line 3, in ?
    import gtk, gtk.glade, gobject
ImportError: No module named glade

```

I'm running kubuntu edgy, the program starts but i can't interact with the icon and the command-line interface spits out that little ditty. suggestions?

---

### Post by Paul41 on 2007-04-12
I have no idea what webilder is so I don't know if this will help, but you can try to install glade to see if that makes any difference.

```
sudo aptitude install glade
```

---

### Post by theredcross on 2007-04-12
that helped, and a bunch of other files that I missed as dependencies. All of them are in the default repo's though, they should be tagged as dependencies in apt by default.

---

### Post by behanw on 2007-04-13
> **theredcross said:**
> that helped, and a bunch of other files that I missed as dependencies. All of them are in the default repo's though, they should be tagged as dependencies in apt by default.

Actually, all that you were missing was the "python-glade2" package.

It absolutely was a missing dependency in my package.  Sorry about that.

I've updated the webilder package to include this dependency on debian.websterwood.com.

Behan

---

### Post by theredcross on 2007-04-15
no problemo, easy fix. glad to hear it'll be updated!

---

### Post by emmerc on 2007-04-19
I hope soon might be an update for Ubuntu 7.04 I just upgrade to it and I lost webilder functionality.

---

### Post by dnns on 2007-04-23
The Feisty repositories on the Webilder website aren't functional yet, you could try the Debian sid or sarge depositories (or for that matter the edgy one as well). I remember them functioning in my Feisty beta. For now, I'm waiting for the official release.

---

### Post by dnns on 2007-04-23
Doublepost sorry

---

### Post by FLPCGuy on 2008-02-12
> **dnns said:**
> The Feisty repositories on the Webilder website aren't functional yet, you could try the Debian sid or sarge depositories (or for that matter the edgy one as well). I remember them functioning in my Feisty beta. For now, I'm waiting for the official release.

I'm running Edgy but webilder won't update from apt-get install because it requires Python 2.5 which I don't believe is in the Edgy repository.  I'm trying to keep my Edgy completely compatible with the repository.   Anyway, the older version of webilder I have installed still works but it has never updated (websterwood fails authentication).  My /etc/apt/sources.list includes:

deb [http://debian.websterwood.com/](http://debian.websterwood.com/) edgy main
deb-src [http://debian.websterwood.com/](http://debian.websterwood.com/) edgy main

---

