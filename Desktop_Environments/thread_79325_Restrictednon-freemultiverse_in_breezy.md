---
title: "Restricted/non-free/multiverse in breezy?"
date: 2005-10-20
forum: Desktop Environments
---

### Post by uberlinux on 2005-10-20
Anyone know where I can score a well equiped /etc/apt/sources.list?
Thanks,
Kodiak

---

### Post by aysiu on 2005-10-20
[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

---

### Post by uberlinux on 2005-10-20
[QUOTE=aysiu][http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)[/QUOTE]
Thank you!  That at least covers multiverse stuff.  Now if only I could find the reps for the non-free things like w32codecs and such.

---

### Post by aysiu on 2005-10-20
For those, I used the [Debian repositories](http://www1.apt-get.org/search.php). If you do add them, install the codecs, then take them off your sources.list immediately afterwards. Otherwise, you might have weird conflicts when updating your system.

---

### Post by uberlinux on 2005-10-20
[QUOTE=aysiu]For those, I used the [Debian repositories](http://www1.apt-get.org/search.php). If you do add them, install the codecs, then take them off your sources.list immediately afterwards. Otherwise, you might have weird conflicts when updating your system.[/QUOTE]
Is there still a Marilliat repository?

---

### Post by objorkum on 2005-10-20
w32codecs are no longer in any Ubuntu-repository.

The w32codecs-package MPlayer's essential codec pack, so if you just download it, and put the codecs in /usr/lib/win32, you have it (install totem-xine, to be able to use them)

Here it is:
[http://www2.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2](http://www2.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2)

---

### Post by ranf on 2005-10-20
[QUOTE=uberlinux]Is there still a Marilliat repository?[/QUOTE]
Yes there is. Just no `testing' in dists.

My (Hoary) sources list had this line:
```
ranf@schlepp:~ $ grep marillat /etc/apt/sources.list
#  deb ftp://ftp.nerim.net/debian-marillat/ testing main #mplayer
```

There are only these dists (pick one, I'm not sure which one fits best).
```
Index of ftp://ftp.nerim.net/debian-marillat/dists
Up to higher level directory
Directory: etch 		20.10.2005 	15:30:00
Directory: experimental 	20.10.2005 	15:30:00
Directory: sarge 		20.10.2005 	15:30:00
Directory: sid 			20.10.2005 	15:30:00
```

---

### Post by uberlinux on 2005-10-20
Any ideas what I should do with that other than going to it and individually grabbing .Debs?

---

