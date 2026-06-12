---
title: "apt-get recommends after the fact"
date: 2009-03-24
forum: General Help
---

### Post by landtuna on 2009-03-24
After installing a package via apt-get, is it possible to install (or even just list) the packages that were in the recommends or suggests lists?  I don't see anything that does the trick in the apt-get, apt-cache, or dpkg manpages.

Thanks.

---

### Post by unutbu on 2009-03-24
If a package has recommendations, the should be listed in the output when you run
```

apt-cache show PACKAGE
```
For example,```

apt-cache show wesnoth
```
Outputs:
```

Recommends: wesnoth-ttb, wesnoth-httt, wesnoth-tsg
```
If you don't see any line that begins with "Recommends:", then 
that package doesn't have any recommendations.

---

### Post by drs305 on 2009-03-24
*Added: unutbu's post is the most convenient. Here are some other ways to view them:*

/var/lib/dpkg/status lists the packages and includes "recommends" if you want to take the time to look there.

[http://packages.ubuntu.com]("http://packages.ubuntu.com") also lists the dependencies and recommends.

If you highlight a package in synaptic and see the suggests, recommends and dependencies in the lower panel's Dependencies tab or by right clicking and selecting Properties.

You can also read the apt-cache man page.

---

