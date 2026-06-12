---
title: "Minimize issue after driver and Desktop Effects"
date: 2009-11-27
forum: Desktop Environments
---

### Post by KrGAce on 2009-11-27
Hello All,

Having the same issue again which eventually got fixed with Jaunty.  After I activate my driver for my ATI 3600HD card, and then enable desktop effects, everything works pretty well except when I minimize/maximize a window there is a 5 second delay.  Not a deal breaker, but after enough times it gets annoying.

In Jaunty, there became an xserver-backfill file that you could update and that took care of the issue.  In Karmic it tells me I have the latest file, but yet it still doesn't work right.

Anyone provide any help?  I have the card I stated, and am running the 64bit version of Karmic.

Much appreciated in advance,

AceMan

---

### Post by calanor on 2009-12-01
go to [https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)
fixed the issue for many of us

---

### Post by kouchris on 2010-01-28
> **KrGAce said:**
> Hello All,

Having the same issue again which eventually got fixed with Jaunty.  After I activate my driver for my ATI 3600HD card, and then enable desktop effects, everything works pretty well except when I minimize/maximize a window there is a 5 second delay.  Not a deal breaker, but after enough times it gets annoying.

In Jaunty, there became an xserver-backfill file that you could update and that took care of the issue.  In Karmic it tells me I have the latest file, but yet it still doesn't work right.

Anyone provide any help?  I have the card I stated, and am running the 64bit version of Karmic.

Much appreciated in advance,

AceMan

you should try these, it got mine fixed.

```
apt-get build-dep xorg-server
```

```
sudo apt-get install devscripts
```

```
sudo apt-get source xorg-server
```

```
cd xorg-server-*
```

```
wget http://launchpadlibrarian.net/32728179/xserver-xorg-backclear.patch
```

```
patch -p1 < xserver-xorg-backclear.patch
```

```
debuild
```

```
cd ..
```

```
sudo dpkg --install xserver-xorg-core*.deb
```

i hope this works for you as well
Cheers

P.S the debuild should take some time, dont worry about it.

---

### Post by kouchris on 2010-01-28
Let me know if it worked !!

---

