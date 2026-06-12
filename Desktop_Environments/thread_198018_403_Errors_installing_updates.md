---
title: "403 Errors installing updates"
date: 2006-06-16
forum: Desktop Environments
---

### Post by hawkbane on 2006-06-16
I am getting 403 errors when attempting to do automatic updates with a fresh install of Dapper.  I have not made any changes to my configuration, it is straight "out of the box". I get the error any time I try to access **us.archive.ubuntu.com** and **security.ubuntu.com**.  I am clueless as to what the resolution is to this.  Any ideas?

---

### Post by hawkbane on 2006-06-16
UPDATE:  I have tried changing my mirrors from the default to a local, but I still get the same errors.  This has to be some sort of configuration on my end, but I can't see it.  Like I said, other than the server changes I have made, this is a default install.  I am now trying to pull down updates from [http://ubuntu.mirrors.tds.net/ubuntu/](http://ubuntu.mirrors.tds.net/ubuntu/) .  I also tried the University of Minnesota as well, with the same effect.

---

### Post by Ramses de Norre on 2006-06-16
What errors do you get? Could you post the error messages?

---

### Post by hawkbane on 2006-06-16
The error messages I get from Synaptic Package Manager is:

[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper/main/binary-powerpc/Packages.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper/main/binary-powerpc/Packages.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper/restricted/binary-powerpc/Packages.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper/restricted/binary-powerpc/Packages.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper/universe/binary-powerpc/Packages.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper/universe/binary-powerpc/Packages.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper/multiverse/binary-powerpc/Packages.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper/multiverse/binary-powerpc/Packages.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper/main/source/Sources.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper/main/source/Sources.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper/restricted/source/Sources.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper/restricted/source/Sources.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper/universe/source/Sources.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper/universe/source/Sources.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper/multiverse/source/Sources.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper/multiverse/source/Sources.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-updates/main/binary-powerpc/Packages.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-updates/main/binary-powerpc/Packages.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-updates/restricted/binary-powerpc/Packages.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-updates/restricted/binary-powerpc/Packages.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-updates/universe/binary-powerpc/Packages.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-updates/universe/binary-powerpc/Packages.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-updates/multiverse/binary-powerpc/Packages.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-updates/multiverse/binary-powerpc/Packages.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-updates/main/source/Sources.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-updates/universe/source/Sources.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-updates/universe/source/Sources.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-backports/main/binary-powerpc/Packages.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-backports/main/binary-powerpc/Packages.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-backports/restricted/binary-powerpc/Packages.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-backports/restricted/binary-powerpc/Packages.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-backports/universe/binary-powerpc/Packages.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-backports/universe/binary-powerpc/Packages.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-backports/multiverse/binary-powerpc/Packages.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-backports/multiverse/binary-powerpc/Packages.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-backports/main/source/Sources.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-backports/main/source/Sources.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-backports/universe/source/Sources.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-backports/universe/source/Sources.gz:) 403 Forbidden
[http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:](http://ubuntu.mirrors.tds.net/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:) 403 Forbidden

I reallize that this is on a PPC and this is not the normal PPC forum thread, but from my research I have found that the problem is not exclusive to this brand of the build.  The consensus of others that I have found is that it just started working.  I am on my fourth install of this, and it hasn't worked yet.  Thanx for any insights you can give me.

---

### Post by clparker on 2006-06-21
Anybody ever figure this out?

---

