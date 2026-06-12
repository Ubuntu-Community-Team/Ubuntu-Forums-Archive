---
title: "Trouble installing compiz"
date: 2006-08-12
forum: Desktop Environments
---

### Post by thebasard on 2006-08-12
I get the following error when trying to install compiz on Dapper.  Any help would be appreciated.

The following packages have unmet dependencies.
  compiz-quinn-aiglx: Depends: gset-compiz but it is not installable
E: Broken packages

I don't see gset-compiz available on any of the repos that I've tried including:
# Install compiz
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper aiglx
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main
deb [http://ubuntu.systemadministrator.org](http://ubuntu.systemadministrator.org) dapper eyecandy
deb-src [http://ubuntu.systemadministrator.org](http://ubuntu.systemadministrator.org) dapper eyecandy

---

### Post by Greycloak on 2006-08-12
I had the same problem last night.  Now I get this:

```
Package compiz-quinn-aiglx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package compiz-quinn-aiglx has no installation candidate

```

[edit]Nevermind...automatix changed my sources.list

---

### Post by phetre on 2006-08-13
Hi, Thebasard.  I had the same problem, and you can download a .deb file of gset-compiz from here:
[http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/](http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/)
If that doesn't work, I'm temporarily hosting a backup at [http://home.uchicago.edu/~pashultz/gset-compiz_0.3.4-3v1ubuntu3_i386.deb](http://home.uchicago.edu/~pashultz/gset-compiz_0.3.4-3v1ubuntu3_i386.deb)

Good luck,
Peter

---

