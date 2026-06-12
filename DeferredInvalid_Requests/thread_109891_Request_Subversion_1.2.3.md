---
title: "Request: Subversion 1.2.3"
date: 2005-12-29
forum: Deferred/Invalid Requests
---

### Post by isoaglib on 2005-12-29
The current stable version of subversion is 1.2.3 while the newest available version for BREEZY is 1.2.0 .

A look at the CHANGES 
([http://svn.collab.net/repos/svn/trunk/CHANGES](http://svn.collab.net/repos/svn/trunk/CHANGES))
of subversion reveals, that there are important bugfixes and improvements since 1.2.0 .
Some examples that causes problems for my use case with server and client - and would urge me to make my own build:
* fixed: mod_dav_svn bug sets content-type incorrectly (r15046)
* fixed: mod_authz_svn being overly restrictive (r15463)
 * fixed: 'svn merge' memory leak (r15233)
* improvements to 'svnmerge' utility (r14008,-458,-587,-632, r15329,-340)


By the way:
The version 1.2.3 of subversion and the corresponding sister packages made it already to the dapper pre-release. Thus the version 1.2.3 should match to the overall ubuntu build process.

Thanks

---

### Post by abandoned_hussam on 2005-12-30
I've actually asked for this before. There are soem problems I've faced that are fixed in 1.2.3 so I would like this as well.

---

### Post by jdong on 2006-01-02
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=sourcenames&version=all&exact=1&keywords=subversion](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=sourcenames&version=all&exact=1&keywords=subversion)

Subversion exports several libraries -- not a backports candidate.

---

### Post by isoaglib on 2006-01-04
Hi,
on the one hand I can understand, that there are some other packages depending on subversion.

But on the other hand those deps are ways smaller than the deps of the firefox package that was rejected for backport.

Additionally:
Are those deps depending with the EXACT version number, or is it possible that some of them depend with >= relationship, so that a newer version wouldn't hurt?

Last note:
Since today the new 1.3 version is out, so that the latest Breezy revision is very outdated.

Happily I am used to compile things also from source. So I will help myself with compiling from vanilla sources or from the Dapper adopted source package (in case the 1.3 rev makes it there soon).

---

### Post by jdong on 2006-01-04
There are always minor API changes behind the scenes that dpkg won't detect but packages that use certain features of subversion would behave strangely...

---

