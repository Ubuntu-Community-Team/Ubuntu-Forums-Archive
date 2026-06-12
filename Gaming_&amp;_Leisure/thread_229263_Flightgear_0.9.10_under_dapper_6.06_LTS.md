---
title: "Flightgear 0.9.10 under dapper 6.06 LTS"
date: 2006-08-04
forum: Gaming &amp; Leisure
---

### Post by qmx on 2006-08-04
I've sucessifully backported it to dapper (adding edgy source repos and building it)
does anyone have some interest in putting it to dapper-backports (the build went seamlessly)

Any comments?

PS: Atlas-0.3.0 rocks!

---

### Post by kaffelars on 2006-08-04
I'd really like to have it :)

---

### Post by hobieone on 2006-08-04
is this version in the repositories yet? i downloaded the .deb file from thier website but couldn't get ito install it kept saying i was missing a certian file  which i already have and it was the corect version and everything. i would like tthe new version:-P

---

### Post by qmx on 2006-08-04
> is this version in the repositories yet?
No, only in edgy eft repositories

The 0.9.10 series brought a lot of improvements! Please share the word with MOTU's to bring the backport to dapper

---

### Post by JaymZZZ on 2006-08-04
Exactly which repository do you have in your sources list? I tried a few different ones, but none worked.

---

### Post by qmx on 2006-08-08
edgy deb-src

then i've downloaded the sources and built it

---

### Post by bja78 on 2006-08-23
Hi,
I have the following problem. I would like to compile flightgear 0.9.10 on dapper. I added the line 
```

deb-src http://archive.ubuntu.com/ubuntu edgy universe main restricted

```
to my source.list. 

Now, when I execute
```

apt-get build-dep fgfs-atlas
...
E: Paket xlibmesa-gl-dev hat keinen Installationskandidaten
E: Konnte die Build-Depends-Abhängigkeit für fgfs-atlas nicht erfüllen: xlibmesa-gl-dev

```

Ok. I execute
```

apt-get build-dep xlibmesa-gl-dev
apt-get --build source xlibmesa-gl-dev

```

Now, I have new packages 
xorg_7.0.22ubuntu7_all.deb
xserver-xorg_7.0.22ubuntu7_all.deb
and others.

And now my question: Is that right, a new version of X?

Now, I have install only xlibmesa-gl-dev and flightgear, fgfs-atlas, fgfs-base, simgear0, simgear-dev. The problem is, that flightgear in fullscreen mode is very very slow.

Thank you for your efforts and sorry for my english.

Bye
BjA

---

### Post by mlind on 2006-08-23
> **bja78 said:**
> Hi,
I have the following problem. I would like to compile flightgear 0.9.10 on dapper. I added the line 
```

deb-src http://archive.ubuntu.com/ubuntu edgy universe main restricted

```
to my source.list. 

Now, when I execute
```

apt-get build-dep fgfs-atlas
...
E: Paket xlibmesa-gl-dev hat keinen Installationskandidaten
E: Konnte die Build-Depends-Abhängigkeit für fgfs-atlas nicht erfüllen: xlibmesa-gl-dev

```

Ok. I execute
```

apt-get build-dep xlibmesa-gl-dev
apt-get --build source xlibmesa-gl-dev

```

Now, I have new packages 
xorg_7.0.22ubuntu7_all.deb
xserver-xorg_7.0.22ubuntu7_all.deb
and others.

And now my question: Is that right, a new version of X?

Now, I have install only xlibmesa-gl-dev and flightgear, fgfs-atlas, fgfs-base, simgear0, simgear-dev. The problem is, that flightgear in fullscreen mode is very very slow.

Thank you for your efforts and sorry for my english.

Bye
BjA

xlibmesa-gl-dev is a transitional package from Debian sarge to etch. Dapper doesn't have it. It should be okay just to remove this package from **debian/control** *Build-Depends* and build the package. That's what I've been doing.

---

### Post by bja78 on 2006-08-24
Ok, now, the package xlibmesa-gl-dev isn't installed on my sytem. But, the problem is the same. Flightgear is very very slow with options 

--enable-fullscreen

Without this option, the game-speed is ok. Did you updated an other package, for example sdl, freeglut3 or so?

Thanks for your efforts,
bye
BjA

---

### Post by bja78 on 2006-08-25
Ok, I did founded a work around. I executed the following command

```

fgfs --enable-game-mode --geometry=1280x1024

```

Thanks at all.

Bye
BjA

---

### Post by jsandys on 2006-10-30
I would like Flightgear-0.9.10 and Atlas-0.3.0 for Dapper in the Backports.  I was able to get Atlas-0.3.0 running with FlightGear-0.9.9 on Dapper but now I keep getting update messages.  I guess I need to do the build-dep to fix it.
      [http://ubuntuforums.org/showthread.php?t=287562](http://ubuntuforums.org/showthread.php?t=287562)

Let us know when the backport is in the repository.

---

