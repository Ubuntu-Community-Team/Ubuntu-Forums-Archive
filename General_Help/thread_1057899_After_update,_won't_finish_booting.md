---
title: "After update, won't finish booting"
date: 2009-02-02
forum: General Help
---

### Post by bradhaack on 2009-02-02
ubuntu 8.10, dual boot.
After letting the update manager do it's thing, my system is broken.  There were some error messages from the update (which I didn't write down), it was still running but gnucash wouldn't start, so I restarted.  Now it never gets to the login screen, it gets to a screen with a rolling bowling ball (or maybe it's some kind of smiley face?) and hangs there.  How do I get this working again?

---

### Post by zvacet on 2009-02-02
Boot in recovery mode and type

```
dpkg --configure -a
```

or if that doesn't help 

```
apt-get -f install
```

---

### Post by bradhaack on 2009-02-02
Thanks, but that didn't work

dpkg --configure -a
gave me some msgs like:
nautilus-data not installed 
evolution not installed 
at-spi not configured 
errors encountered while processing:
evolution-exchange
at-spi
nautilus
evolution-plugins
python-pyatspi

with
apt-get -f install
it couldn't even run apt-get
GLIBCXX_3.4.9 not found

Based on another thread, I also tried aptitude, but same GLIB not found

---

### Post by zvacet on 2009-02-03
```
apt-get install nautilus-data evolution
```

and after that try 

```
dpkg --configure at-spi
```

---

### Post by bradhaack on 2009-02-03
That won't work because apt-get doesn't run.  
apt-get: /usr/local/lib/stdc++.so.6: version 'GLIBC++.3.4.9' not found (required by apt-get)

---

### Post by bradhaack on 2009-02-04
I have something similar to this:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/180160](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/180160)
So I did what they did only instead of 'adding' /usr/lib, I replaced /usr/local/lib with /usr/lib

Now I'm getting further, apt-get runs, but 'fails to fetch '... could not resolve us.archive.ubuntu.com.  Searching for that I find some people who had trouble with proxy server setup, but I'm not using a proxy server so I don't see how that can be it.  I can get to us.archive.ubuntu.com from firefox on a different computer, so it's not the network.

---

### Post by zvacet on 2009-02-04
Try with main server.

---

### Post by bradhaack on 2009-02-04
I don't know what the 'main server' is, or how to set it up.

But, I seem to be up and running again anyway,  I was doing the previous steps from recovery mode, I let it boot normally and can now login.

---

