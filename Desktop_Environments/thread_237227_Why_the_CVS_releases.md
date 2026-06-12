---
title: "Why the CVS releases?"
date: 2006-08-15
forum: Desktop Environments
---

### Post by com4 on 2006-08-15
I've been using ubuntu for a few months now and I've noticed something "strange" with with many of the packages (considering ubuntu is debian based).

```
jason@vaio:~$ apt-cache show gaim
Package: gaim
...
Version: 1:1.5.0+1.5.1cvs20051015-1ubuntu10

jason@vaio:~$ apt-cache show xmms
Package: xmms
...
Version: 1.2.10+cvs20050809-4ubuntu5

```
and wxpython which has had quite a bit of debian related drama surrounding it, so I understand the old version...
```

Python 2.4.3 (#2, Apr 27 2006, 14:43:58)
[GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import wx
>>> wx.__version__
'2.6.1.2pre'

```

Why are CVS and alpha packages deemed "ok" to be put into the ubuntu repositories? I was always under the impression that these weren't ready for a production system.

---

### Post by 23meg on 2006-08-15
It just means that package was built from the CVS repo in the date that follows the "cvs" prefix. Not everything in CVS is necessarily unstable; there are stable and unstable branches (as well as others) in CVS repositories. Stable branches typically just get bug fixes.

Plus, just because Ubuntu is based on Debian doesn't mean it has to get (and gets) all its components from Debian. There are many packages in Ubuntu which are not in Debian, and some Debian components have different versions in Ubuntu, or exist in heavily modified form.

I'm not sure where you ran into "alpha" but it doesn't say anything about the stability of the software. It doesn't necessarily mean "very unstable", it just means the software is just in its very beginning phases of development. An alpha or beta build can be perfectly stable.

---

### Post by az on 2006-08-15
Look at the changelogs.  Sometimes, it just means one stable version with a few patches from CVS.  You get the best of both worlds that way.

Often, upstream will reccommend you do that anyway, depending on the time in the release cycle of the particular application.

---

### Post by 23meg on 2006-08-15
Also the latest version of the application may not have hit Sid yet and may only be available via CVS. In that case it may be more convenient to just build from CVS rather than bug the Debian maintainer about it.

---

### Post by com4 on 2006-08-15
i wasn't suggesting that ubuntu got it's packages from debian, rather that it's taking the philosophy that stable is the way to go. now you see why i found it wierd there was CVS packages in the repository. i was mistaken. thank you azz.

the wx package is what boggles me the most as i've ran into a few problems with it being old and a "pre" release.  it does look like, however, edgy will get a more up to date package that fixes a few, but not all of the problems that plague me, and other wx users. *shrug* whatever though

thank-you for your comments.

---

