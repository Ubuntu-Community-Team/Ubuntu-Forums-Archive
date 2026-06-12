---
title: "Gset-compiz &amp; AMD64"
date: 2006-07-07
forum: Desktop Environments
---

### Post by DaRkBLa on 2006-07-07
Hi all,
I am a new member of this forum and i'm exicted for this great DISTRO UBUNTU.
Before postin' i searched all the forum after the question i'm exposing to you.

I installed XGL & Compiz following step by step the great guide of the great pdc303 [http://ubuntuforums.org/showthread.php?t=133427](http://ubuntuforums.org/showthread.php?t=133427) and it goes successfully

I have problems to find gset-compiz e gcompizthemer for my distribution. 

I have updated the apt repositories with this 2 other :

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

but i am unable to find them.

Someone can say me if with amd64 distro i am able to install gset-compiz and gcompizthemer?

Thank you for support.

DaRkBLa

---

### Post by jvictor on 2006-07-07
I dint find it too. I moved to 32 bit bcoz some apps were missing .. it may take some time for the software world to catch up with the hardware worlds pace.

---

### Post by art on 2006-07-07
I have compiled gset-compiz some time ago on 64 bit, I don't have the .deb file now, but I attach the binary. Try placing it in /usr/bin/. 
```
tar zxf gset-compiz.tar.gz
sudo cp gset-compiz /usr/bin/
```

And run it from terminal as gset-compiz. It might work. As for the gcompizthemer, I don't think it is possible at this stage, maybe I am wrong.

---

### Post by th3t1nm4n on 2006-07-12
there's a .deb here: [http://ubuntu.compiz.net/pool/main/g/gset-compiz/](http://ubuntu.compiz.net/pool/main/g/gset-compiz/)

<--edit-->
I use these repositories for up to date AMD64 Compiz/XGL files: [http://ubuntu.moshen.de/dists/dapper/all/](http://ubuntu.moshen.de/dists/dapper/all/)

---

### Post by mattlach on 2006-08-12
> **th3t1nm4n said:**
> there's a .deb here: [http://ubuntu.compiz.net/pool/main/g/gset-compiz/](http://ubuntu.compiz.net/pool/main/g/gset-compiz/)

<--edit-->
I use these repositories for up to date AMD64 Compiz/XGL files: [http://ubuntu.moshen.de/dists/dapper/all/](http://ubuntu.moshen.de/dists/dapper/all/)


I wasn't able to use the .deb you located there.   It fails due to not finding the dependancy libpango-1.0.0  (I checked and I ahve the latest libpango in the repositry installed)

Has anyone actually succeeded getting XGL compiz nad up and running on an AMD64 lately?  is there an updated guide anywhere?  The only ones I can find explicitly for AMD 64 are in the old beta Dapper forums.

---

